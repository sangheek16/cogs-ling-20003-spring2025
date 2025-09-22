# A6: Reading time and surprisal

---

**UPDATE (May 15): In the preprocessed you’ll use, the words are presented in word-by-word (without any phrases). So the words should look like “The” / “waitress” / … (NOT “The waitress”). This should be reflected on your line graph (x-axis tick labels) as well as identifying the critical region. The critical region will be word number 9; spillover regions being regions 10 and 11.**

# Overview

We discussed that a standard number agreement attraction effect is identified by two reading time (RT) pattern: 

1. Longer RTs with ungrammatical conditions than grammatical conditions: **c & d > a & b**
2. Within the ungrammatical condition (’were’), longer RTs with a singular distractor noun (’girl’) than a plural distractor (’girls’): **d > c**

<aside>

1. Plural - Grammatical
The waitress who sat near the girls unsurprisingly was unhappy about all the noise.
2. Singular - Grammatical
The waitress who sat near the girl unsurprisingly was unhappy about all the noise.
3. Plural - Ungrammatical
The waitress who sat near the girls unsurprisingly were unhappy about all the noise.
4. Singular - Ungrammatical
The waitress who sat near the girl unsurprisingly were unhappy about all the noise.
</aside>

In this assignment, **you will examine whether the two key patterns appear in (1) the human data we collected in class, and (2) the surprisal values using a GPT-2 model.**

<aside>

### Tasks

1. **Plot line graphs** of the **mean reading times** (with **standard error bars**) using the **human reading time data collected in class**.
    
    → Use the file: `combined_results_preprocessed.csv`.
    
2. **Calculate surprisal values using GPT-2** for the **critical region** (*"was"/"were"*) in your stimuli.
    
    → You may use either `Parker_An-2018-material-exp1-PP.csv` or your dataset you used for A5.
    
3. **Plot a bar graph** of the **mean surprisal values** (with **standard error bars**) across the **four conditions**, based on the surprisal values calculated in Task 2.
4. **Write a brief summary and key takeaways**, comparing the human reading time data and the GPT-2 surprisal results.

- **Tasks 1, 3, and 4** should be completed in **R Markdown**; **Task 2** should be done in **Python**.
- Your **final submission should be a compiled PDF using the R Markdown file**, including the outputs for Tasks 1, 3, and 4.
**You do NOT need to submit your Python code.**
</aside>

# Human reading time data

## Data

Below is the combined data that were collected by your classmates. I’ve preprocessed the data. Time and IP information of the participants are anonymized. 

[combined_results_preprocessed.csv](A6%20Reading%20time%20and%20surprisal%20a6_files/combined_results_preprocessed.csv)

Check out the columns by `colnames(df)`. 

- The **Subj** column was created based on participants’ Time and IP information. So instead of using those two fields to identify subjects, you can simply use the **Subj** column.
- The three types of subject information you collected have been renamed as **verification_code**, **Age**, and **first_language**. These column names might differ from what you used in your original experiment, so make sure to refer to the correct names.

## Task

Everything below case be executed based on the functions we practiced in class! Feel free to recycle the code in `linegraph.Rmd` .

[linegraph](A6%20Reading%20time%20and%20surprisal%20a6_files/linegraph.rmd)

1. **Print the number of subjects** in the dataset.
2. **Compute and report the age statistics**:
    - Minimum, maximum, and mean age of the subjects.
3. **Print the number of critical trials** each subject completed.
4. **Print the names of the four experimental conditions** used in the critical trials.
5. **Plot the mean reading times across word regions**, following these guidelines:
    - Use **line type and color** (and optionally, points) to differentiate the four conditions.
        
        (Note: The 2×2 design means two pairs of conditions should be visually grouped.)
        
    - **Do not use facet grids**.
    - Label the x-axis with **example word regions** (e.g., *The waitress / who / sat / … / the noise*). Limit to **11 regions**, as we did in class.
    - Clearly **label the x-axis, y-axis, and provide a title** for the graph.
    - Mark on the plot **word regions 7 (critical), 8 (spillover1), and 9 (spillover2)** as relevant to the number agreement attraction effect.
        
        (Note: In class, we only analyzed regions 7 and 8; here, include region 9 as well.)
        
6. **Interpret the results** based on the mean reading times.
    
    (Tip: To help interpretation, you may also include a second plot **without error bars**, since large standard errors can obscure the pattern in the data.)
    

# Surprisal

## Data

The data for this task come from Parker & An’s (2018) Experiment 1, specifically conditions (e)-(h). You download the materials below:

[Parker_An-2018-material-exp1-PP.csv](A6%20Reading%20time%20and%20surprisal%20a6_files/Parker_An-2018-material-exp1-PP.csv)

## Task

1. **Calculate surprisal values** for the **target word** (e.g., *was/were*) given the **preceding context** (e.g., *the waitress who sat near the girl(s)*) for all 24 items * 4 conditions. Use the provided code in Google Colab. 
    
    (*If you’re reading this instruction before the first class of Week 7: We will go over the code below in class, so don’t worry even if you don’t understand anything.)*
    
    [Google Colab](https://colab.research.google.com/drive/1u-AHUUWfCIX4WyB6t23NY_SlRPFnhpjt?usp=sharing)
    
2. **Plot a box plot** showing the **mean surprisal** values (with **error bars**) across the **four conditions** at the critical region (”was/were”).
    - This task is similar to the plotting assignment we completed for the Federmeier & Kutas (1999) replication study. Feel free to recycle the R Markdown file we used in class for plotting a bar graph, or the code you used for Assignment 4. Y can **choose any aesthetics** that best communicate the pattern in your data.
        
        [bargraph-simplified](A6%20Reading%20time%20and%20surprisal%20a6_files/bargraph-simplified.rmd)
        
3. Interpret the results. Do you see the expected number agreement attraction effect as you saw in the human reading time results?

# Synthesis

Given the findings in the **human reading time data** and the **GPT-2 surprisal values**, write a brief synthesis addressing the following:

1. **Do both sources (human data and GPT-2 surprisal) show the two key patterns of number agreement attraction?**
    - **Pattern 1**: Longer RTs/surprisal values in ungrammatical conditions than grammatical ones (*c & d > a & b*).
    - **Pattern 2**: Within ungrammatical conditions, longer RTs/surprisal when the distractor is singular (*d > c*).
2. **To what extent does GPT-2 replicate the human sensitivity to number agreement violations?**
    - If it differs, where does it diverge most clearly?
3. **What might explain any mismatches between human reading behavior and GPT-2’s surprisal estimates?**
    - When interpreting your results, consider the nature of surprisal as a probabilistic metric and the limitations of GPT-2’s linguistic capabilities. You may refer to Arehalli & Linzen (2020) (assigned reading) to support your analysis. Your synthesis should be 1-2 short paragraphs and reflect your interpretation and evidence from both human and language model output.

# Submission

- **Write your report using an R Markdown file**. The report should include the following:
    - **Plots**: All required plots (line graph(s), and a bar graph) should be included.
    - **Synthesis**: A brief written synthesis comparing the human reading time data and GPT-2 surprisal results.
- **Compile your R Markdown file into a PDF**. This will be your final submission document.