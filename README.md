## Exploring The Sonic Archive
### Digital Tools for Richard Freedman's course at Heidelberg University, Fall 2026

This repository contains Jupyter Notebooks and related data for Richard Freedman's sessions during the course. They are designed for the CRIM Project JupyterHub, but most will also run in a local Python environment or in Google Colab.

The notebooks build on one another, from the basics of Python and data tables, through the analysis of encoded texts and scores, to experiments with Large Language Models:

1. **Python and Pandas Basics**: the building blocks: notebooks, Python, and data tables
2. **MEI, music21, and CRIM Intervals**: encoded *music*: notes, intervals, patterns, and corpora
3. **LLM Analysis**: what Large Language Models can (and cannot) tell us about music

**How to use these notebooks:** open them in JupyterHub and run the cells in order, top to bottom. Within each folder, work through the notebooks in alphabetical order (A, B, ...). In the Beatles folder this matters: notebooks B and C each save a file that the later notebooks load.

## Notebooks

### 01 Python and Pandas Basics

*The big idea: a notebook is a place to think with code. Python holds and transforms information; Pandas organizes it into tables we can question.*

**[A_Python_Basics.ipynb](01_Python%20Pandas%20Basics%20/A_Python_Basics.ipynb)**: How Jupyter notebooks work, and the core Python every later notebook relies on, taught with music-themed examples. Students learn to tell Markdown cells from code cells, and to recognize the basic kinds of data (text, numbers, True/False) and how to convert between them. They also meet the two containers used everywhere in data work: **lists** (ordered collections) and **dictionaries** (look-ups from keys to values).
- Running cells, importing libraries, printing results
- Data types, string methods, and type conversion
- Lists and dictionaries

**[B_Pandas_Basics_Beatles.ipynb](01_Python%20Pandas%20Basics%20/B_Pandas_Basics_Beatles.ipynb)**: An introduction to the **DataFrame**, the table at the heart of data analysis in Python.  Here we use the Beatles dataset, `Beatles_Belgrade_Complete.csv`, to show how to load a CSV file into a DataFrame, inspect its rows and columns, select and reshape data, sort and count values, and combine two tables into one. A closing section shows why Pandas' built-in methods are usually better than writing loops.

**[C_Pandas_Basics_CRIM.ipynb](01_Python%20Pandas%20Basics%20/C_Pandas_Basics_CRIM.ipynb)**: Here we work with the CRIM project dataset to show how to work with complex JSON and flatten it into a DataFrame. Students learn to read JSON, normalize nested structures, and combine multiple files into one table. They also learn how to save their work as a CSV or Pickle file for later use.
- Loading CSV and JSON files into DataFrames
- Inspecting, selecting, and reshaping data
- Sorting, counting, and combining tables



### 03 MEI, music21, and CRIM Intervals: Encoded Music

*The big idea: once music is encoded, a computer can find notes, intervals, and recurring patterns, in one piece or across a whole corpus.*

**[Music21_Basics.ipynb](04%20MEI%20M21%20CRIM%20Intervals/Music21_Basics.ipynb)**: An introduction to [music21](https://web.mit.edu/music21/), the core library for computational musicology, using encoded scores (MEI and Humdrum) such as Chopin's Prelude Op. 28, No. 1 and a canzonet by Thomas Morley. Students learn how a score is represented in code: parts, measures, and notes, where each note is an object with pitch, octave, duration, and position. They also learn the difference between notes and rests, and between melodic intervals (within a voice) and harmonic intervals (between voices).
- Loading scores and reading their metadata
- Parts, measures, notes, rests, and durations
- Melodic and harmonic intervals

**[CRIM_Intervals_Duos.ipynb](04%20MEI%20M21%20CRIM%20Intervals/CRIM_Intervals_Duos.ipynb)**: [CRIM Intervals](https://github.com/HCDigitalScholarship/intervals) builds on music21 and returns its results as Pandas DataFrames, bringing the tools of the earlier notebooks to bear on music. Working with two-voice pieces by Bach, Bartók, and Morley, students chart the notes and intervals of a single piece, find recurring melodic and contrapuntal patterns (**n-grams**) and cadences, and then scale up to a **corpus**. They compare pieces side by side and build a network linking pieces that share melodic patterns.
- Notes, intervals, and n-grams as DataFrames
- Bar charts, radar plots, and heatmaps of musical features
- From one piece to a corpus
- Networks of pieces linked by shared patterns

### 04 LLM Analysis: Large Language Models and Music

*The big idea: LLMs are fluent, but are they accurate? When musical facts matter, we can let the model call real analysis tools, and test its answers against a known answer key.*

**[A_LLM_LangChain_Intro.ipynb](05_LLM_Analysis/A_LLM_LangChain_Intro.ipynb)**: The very basics of working with an LLM from Python, using [LangChain](https://www.langchain.com/). Students set up an API key safely, choose a model, send a first prompt, and see how a **system prompt** changes the model's behavior, and how firmly it holds.
- API keys and model selection
- Prompts and system prompts
- A reusable function for asking questions

**[Music_Analysis_LLM.ipynb](05_LLM_Analysis/Music_Analysis_LLM.ipynb)**: A controlled experiment in using LLMs for music analysis, with nine MEI scores by Bach, Bartók, and Morley. The same question is asked two ways: once with the LLM **reading a text summary** of the music, and once with the LLM **calling music21 tools** that open the scores and compute the answer. Both are compared with a correct answer computed directly in music21. The tasks range from easy to hard: metadata, note counts, pitch histograms, intervals, key, lyrics, and ranking pieces by difficulty. Students draw their own conclusions about where LLMs help, and where they guess.
- Tool-calling ("agentic") LLMs with LangChain and LangGraph
- Designing a fair comparison: same question, one variable changed
- Checking AI answers against verifiable computation
