# A4: Word prediction

---

<aside>

**UPDATE [April 18]: You will need to obtain the standard probabilities only as your final output**. **If you encounter a word that does not exist in the vocabulary in the model, then assign a 0.**

</aside>

# Task

There are three main tasks for this assignment.

<aside>
<img src="https://www.notion.so/icons/flag-swallowtail_gray.svg" alt="https://www.notion.so/icons/flag-swallowtail_gray.svg" width="40px" />

1. Calculate the probability of the target word given context, using the FK1999 dataset and using the assigned language model (**bert-base-uncased**). For this task, you may either recycle the code we used in class or come up with your own code using HuggingFace.
2. Plot bar plots that demonstrate mean probabilities (with standard errors) based on the model outputs you obtained in Task 1. For this task, you must use the functions and commands used in the R Markdown file that was used for the class exercise.
3. Synthesize the model results with the reported findings in FK1999. What can be said about word prediction? More specifically, what can be said about the cognitive mechanisms that underlie lexical access in the human mind? What do the results tell us about the similarities or differences between humans and machines?
</aside>

# Materials

You will have one main dataset and two helper code to complete this assignment.

- `fk1999-stimuli.csv` : This csv file contains experimental materials used in Federmeier & Kutas (1999) Experiment 1. (Or check out Canvas if the file doesn’t open.)
    
    [fk1999-stimuli.csv](A4%20Word%20prediction%20a4_files/fk1999-stimuli.csv)
    
- `word-surprisal.ipynb` : This contains the code getting word (log)probabilities of the target word given prior context. It uses the minicons library for getting access to the model and calculating probabilities a little easier. Feel free to recycle this code.
    
    [Google Colab](https://colab.research.google.com/drive/12GeCjeVrdPUUPpQBZXwGqdkF1h14QxHE?usp=sharing)
    
    - Alternatively, you’re welcome to directly use the pipeline offered in huggingface instead of using the minicons library. See: [https://huggingface.co/google-bert/bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased)
- `bargraph-simplified.Rmd` : This R Markdown file contains basic functions useful for summarizing observed data and drawing bar plots (and histograms). It uses the `results-demo-LexicalDecisionTask.csv` dataset (a mock experimental result dataset from the lexical decision task we set up in Assignment 2) for analysis. Use the functions used in this file for your assignment.
    
    [bargraph-simplified.Rmd](A4%20Word%20prediction%20a4_files/bargraph-simplified.rmd)
    

# Guideline and Submissions

There are two files you should submit.

- **[1] Google Colab URL**
    
    <aside>
    
    This code should:
    
    - [ ]  Read a dataset.
    - [ ]  Calculate the probabilities of the target word given prior context for all items.
    - [ ]  Save the dataframe with the calculated measures.
    </aside>
    
    - The code should read in the `fk1999-stimuli.csv` (which looks like below):
        
        ![image.png](A4%20Word%20prediction%20a4_files/image.png)
        
    - Then calculate the **probability** measure of seeing the target words given prior context. Feel free to reuse the code we used in class for this.
        1. Check if the target word exists in the vocabulary. If it doesn't, **assign the probability as 0 -- no conversion from log prob to prob required**.
        2. If the word exists, **get its log probability and convert it to a standard probability score**. 
        - Tip: Instead of using the given dataframe, it might be easier if you convert it into a long form that looks like below. If you want to convert the shape of the data structure, check out the **melt** function in **pandas** library ([https://pandas.pydata.org/docs/reference/api/pandas.melt.html](https://pandas.pydata.org/docs/reference/api/pandas.melt.html)).
        
        ![image.png](A4%20Word%20prediction%20a4_files/image%201.png)
        
    
    - There are three conditions for each item: expected, within_category, and between_category. Prior context is under the prefix ****column. So make sure that **for each item, you should obtain three values in total (= 3 target words * probability).**
    - Finally, the code should **save the new dataframe into a .csv file.**
    - The code should be **self contained** completing the tasks and should run from beginning to end **without any errors**.
    
- **[2] PDF File compiled by using R Markdown**
    - The **output** and **functions** and **your synthesis** should all be printed out in your compiled PDF file! (If you use the regular ```{r}``` chunk without any options, everything will show up by default.)
    - Feel free to recycle the R Markdown (.Rmd) we used in class.
    
    <aside>
    
    The R Markdown should contain functions and outputs that …
    
    - [ ]  Read the dataframe that contains the probability measure produced after Step 1.
    - [ ]  Use ***distinct*** and ***nrow*** to check if you have 3 unique values for each item. (”unique” doesn’t mean the values should have different values.)
    - [ ]  Use ***mutate*** and ***case_when*** to create a new column that distinguishes whether the condition is expected or unexpected. So the ‘unexpected_between’ and ‘unexpected_within’ conditions should be assigned the same value in this new column.
    - [ ]  Use ***filter*** (and other relevant functions) to examine the number of items that contain target words whose probability is 0.
    - [ ]  Use ***summarise,*** ***group_by, select*** and ***ggplot*** to plot **two separate bar graphs**. (These function don’t have to be used in the same chunk, but as long as they are used at a certain point in your script, that’s fine.)
        
        All bar graphs should commonly have an X-axis label, Y-axis label, a title, no legend, a choice of your color scheme, and a choice of your theme. 
        
        See [https://r-graph-gallery.com](https://r-graph-gallery.com/) for so many different example plots!
        See [https://ggplot2.tidyverse.org/reference/ggtheme.html](https://ggplot2.tidyverse.org/reference/ggtheme.html) for other themes.
        
        Each bar graph should show the mean (with error bars showing the standard errors of mean, with 95% Confidence Interval) as the y-value, and the x-axis should show different conditions.
        
        - Bar graph 1: x-axis based on **three conditions** (expected, unexpected_between, unexpected_within); y-axis based on mean **probabilities**.
        - Bar graph 2: x-axis based on **two conditions** (expected, unexpected); y-axis based on mean **probabilities**.
        
        **Make sure you have the correct x-axis and y-axis labels and the right titles for all four plots!**
        
    - [ ]  Synthesizes the model results. Compare the findings in Federmeier and Kutas (1999). What can be said about word prediction? More specifically, what can be said about the cognitive mechanisms that underlie lexical access in the human mind? What do the results tell us about the similarities or differences between humans and machines?
    </aside>