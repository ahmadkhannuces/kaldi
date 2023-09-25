# Kaldi Speech Recognition Setup

## Installation and Project Setup

1. **WSL and Repository Cloning**:
   - First of all using WSL, I get into the OS, created a directory, and cloned the repo into my Ubuntu-22.04.

2. **Dependency Check and Compilation**:
   - Then I followed bash+makefile (Option 1) and run these commands one by one:
     ```bash
     extras/check_dependencies.sh
     CXX=g++-4.8 extras/check_dependencies.sh
     make
     make CXX=g++-4.8
     ```
   - I was having multiple CPUs in PC, so I also did `make -j 4`.

3. **Configuration**:
   - Then, I followed a series of these commands:
     ```bash
     ./configure --shared
     make depend -j 8
     make -j 8
     ```
   - Now in the attached screenshot, we can see Kaldi get properly set up on our system.

## Data Preparation

4. **Directory Structure**:
   - Next step is to make proper directories and start setting up/placing our testing and training data.
   - I went into the `/egs` directory and created a folder `/digits` over there.
   - Next up, I created a new folder inside `/egs/digits`, which is `/digits_audio`. Now my working directory is looking like this `/egs/digits/digit_audio`. This is the place where I'm going to put my audio sample data.

5. **Testing and Training Data**:
   - Then I created two new directories: `/egs/digits/digit_audio/test` and `/egs/digits/digit_audio/train`.
   - I split the testing and training data into these folders.

6. **Data Duplication**:
   - I created a folder `/data` in the `/digits` folder and also `/test` and `/train` folders inside them, just for having another copy and representing another thing.
   - Then I created another folder `/local` inside `/data` and a file `corpus.txt` inside it, and I added all the transcriptions in it.

7. **Dictionary Setup**:
   - Next, I created another folder `/dict` under `/local` and created `lexicon.txt` file inside it, which has every word from my dictionary with its 'phone transcriptions'.
   - Next, from `kaldi/egs/wsj/s5`, I copied two folders `-utils` and `-steps` with their entire content and added them in my `kaldi/egs/digits` directory.
