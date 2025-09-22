# A5: Self-paced reading task

<aside>

For this assignment, you will:

1. Replicate experimental materials
2. Set up the experiment
3. Publish the experiment and collect sample data

We use the “number agreement attraction effect” as a test case to work on these tasks. 

The experiment you will build should look like this (although not exactly the same): [https://farm.pcibex.net/p/EhLeMH/](https://farm.pcibex.net/p/EhLeMH/)

</aside>

---

# Relevant materials

For this assignment, you should download two files: 1) `Parker_An-2018-material.pdf`; 2) `demo-attraction-template.zip`

<aside>
<img src="https://www.notion.so/icons/attachment_gray.svg" alt="https://www.notion.so/icons/attachment_gray.svg" width="40px" />

[Parker_An-2018-material.pdf](A5%20Self-paced%20reading%20task%20a5_files/Parker_An-2018-material.pdf)

[demo-attraction-template.zip](A5%20Self-paced%20reading%20task%20a5_files/demo-attraction-template.zip)

</aside>

# Design

In class, we discussed what it means to create materials using a **fully crossed 2x2 design**.

In the garden-path effect experiment we saw in class had a design varied by Verb Type (intransitive-only vs. (in)transitive-flexible) and Ambiguity (ambiguous vs. unambiguous).

We can have the same design in the number agreement attraction effect, as well. Below has a **fully crossed 2x2 design varied by Attractor/Distractor noun (singular vs. plural) & Grammaticality (grammatical vs. ungrammatical)**. Note that the subject remains as a singular noun for all conditions. So the grammaticality of the sentence depends on whether ‘was’ or ‘were’ is used as the main verb.

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

Recall that in the **standard number agreement attraction effect**, around the “**critical region**” (’was’/’were’), reading times (RTs) pattern as: 
(shorter RTs) a ~ b < c < d (longer RTs).

# Experimental material

We will replicate the attraction effect, reported in Experiment 1 in [Parker & An’s (2018) study](https://doi.org/10.3389/fpsyg.2018.01566). You will see 48 items * 8 conditions in Experiment 1. 

**For this assignment, we will use the first 24 items (items 1-24) and only conditions e-h.**

<aside>
<img src="https://www.notion.so/icons/flag-swallowtail_gray.svg" alt="https://www.notion.so/icons/flag-swallowtail_gray.svg" width="40px" />

**YOUR TASK**

Copy and paste the relevant items to a dataframe or a .csv file. However you do this, the data frame should have 

1. **three columns: item_no, condition, and sentence.** 
2. **24 (items) * 4 (conditions) + 1 (column header) rows.**

The first few rows would look something like this:

![image.png](A5%20Self-paced%20reading%20task%20a5_files/image.png)

- Click the toggle button for a Hint
    
    There are different ways of doing this. I prefer copy pasting the material into a spreadsheet first for a quick glimpse into the number of words and structure of the sentence.
    
    - One way to do this is to drag and copy all the items in Experiment 1 (including conditions a-d) and paste them into an Excel spread sheet. It will look like below.
        
        ![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%201.png)
        
    
    - Select all (command + A in Mac) > click Data > click Text to columns. Then you will see something like below. Choose ‘Delimited’ > click ‘Next’.
        
        ![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%202.png)
        
    
    - Click ‘Space’. Then you’ll see all the words split into different columns based on space. Then click Next (and Next, again, on the next page as well.)
        
        ![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%203.png)
        
    
    - You should see something like below. Then save into ‘your_file.csv’
        
        ![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%204.png)
        
    
    - Now that you have your file saved, you can continue to use Excel or use Python to name the columns and join the words into a sentence.
        - Excel
            
            In V1 cell, type in the following. Then use the fill handle to click and drag, or double click it to fill the rest of the cells. 
            
            ```r
            =TEXTJOIN(" ", TRUE, C1:U1)
            ```
            
            Once you’re done filling in the cells using the function, make sure to copy again and click “Paste Values” to only keep the generated text.
            
            ![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%205.png)
            
        - Python
            
            ```python
            import pandas as pd
            
            # Read in your csv file; header=None because there isn't a column name yet.
            df = pd.read_csv("your_file.csv", header=None)
            
            # Rename the first two columns
            df = df.rename(columns={0: 'item_no', 1: 'condition'})
            
            # Join all remaining columns (from column 2 onward) as a sentence
            # df.iloc specifies the row and column
            # df.iloc[:, ] means all rows; 
            # df.iloc[:, 2:] means all rows, starting from the 2nd column (3rd, actually, since Python index starts from 0)
            # .astype(str) means that we will convert the type the values of the cells into a string type
            # .apply is applying a function that follows after
            # axis=1 means to apply the function in row direction
            df['sentence'] = df.iloc[:, 2:].astype(str).apply(lambda x: ' '.join(x.dropna()), axis=1)
            
            # Keep columns (dropping the columns with just words)
            df = df[['item_no', 'condition', 'sentence']]
            
            # See first few rows of the dataframe
            print(df.head())
            ```
            
</aside>

# Setting up the experiment

## Create a new project

1. Create an empty project on PCIbex.
2. Unzip the downloaded .zip file. You will find four folders: chunk_includes, css_includes, data_includes, and js_includes. 

You will move some of the files in these folder to **Folders and Files** in your new PCIbex project page.

- [ ]  Upload **all the html files** under /chunk_includes to **Resources**.
- [ ]  Upload `main.js` under /data_includes to **Scripts**.
- [ ]  Upload `global_z.css` under /css_includes to **Aesthetics**.

![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%206.png)

<aside>
<img src="https://www.notion.so/icons/flag-swallowtail_gray.svg" alt="https://www.notion.so/icons/flag-swallowtail_gray.svg" width="40px" />

**YOUR TASK**

1. Edit `Participant_info.html` so that it asks 1) participant’s age, and 2) participant’s first language.
2. Edit `main.js` so that after the experiment, the participant can see a message that says, 
    
    <aside>
    
    “This is the end of the experiment. Please proceed to the next page to submit your responses to the server. Do NOT close the browser until you see a message that says, “The results were successfully sent to the server.”
    
    </aside>
    
    (Once the participant sees this message, they should be able to move onto the next page by clicking a button.
    
3. Edit `main.js` so that it includes a self paced reading task experiment with 24 critical experimental items and 24 filler items. Filler items are already given. You should create new lines for the critical experimental items.
</aside>

## DashedSentence

For Task 3, you will use a controller called `DashedSentence`. See [here](https://github.com/addrummond/ibex/blob/master/docs/manual.md#dashedsentence) for guidelines.

You will create experimental items following the given syntax (see right).

- [ ]  Use a code that marks which ones are the experimental target items (e.g., ”e_”) and which ones are the filler items (”filler”). This should be compatible with the code you’re using in `var shuffleSequence` .
- [ ]  Make sure you have four conditions (e, f, g, h) for each target item.
- [ ]  For the target items, the Question should ask if the participant has seen the distractor noun. Make sure you change the question based on the distractor number (e.g., the girl / the girls).

```html
[["e_e", 1], "DashedSentence", {s: "The waitress who sat near the girls unsurprisingly was unhappy about all the noise."}, "Question", {q: "Did you see the word 'the girls'?", as: [["f","yes"], ["j","no"]]}],

[["e_f", 1], "DashedSentence", {s: "The waitress who sat near the girl unsurprisingly was unhappy about all the noise."}, "Question", {q: "Did you see the word 'the girl'?", as: [["f","yes"], ["j","no"]]}],

[["filler", 101], "DashedSentence", {s: ["It", "seemed", "incredible", "to", "the", "spectators", "that", "the", "game", "was", "still", "going", "on", "after", "5", "hours."]}, "Question", {q: "Was it a quick game?", as: [["f","yes"], ["j","no"]]}],
```

- Hint: Click the Toggle button to automize the process of converting csv data into PCIbex template
    
    ```python
    import pandas as pd
    import string
    
    # Load the CSV file (assuming it's comma-separated)
    df = pd.read_csv("parker_an_2018_or_your_file_name.csv")
    print(df.head(4))
    
    # Define the Ibex item template
    template_str = string.Template(
        '[["e_${condition}", ${item_no}], "DashedSentence", {s: "${sentence}"}, '
        '"Question", {q: "${question}", as: [["f","yes"], ["j","no"]]}],'
    )
    
    # Iterate through rows and generate formatted output
    for _, row in df.iterrows():
    # for idx, row in df.iterrows():
        output = template_str.substitute(
            condition=row["condition"],
            item_no=row["item_no"],
            sentence=row["sentence"],
            question=row["question"]
        )
        print(output)
    ```
    
    In the code above, it’s assumed that you already have a column named ‘question’ in the csv file you’re reading (see below). 
    
    TIP: If you used Excel in copy pasting the materials from Parker & An (2018), you can use the TEXTJOIN function again to automatically create the question based on the distractor words. 
    
    ![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%207.png)
    

# Publish experiment and collect sample data

1. Once you have checked everything works fine, publish the experiment! You can do this by clicking on the button under Actions. The button should turn into blue when the experiment is Published.
    
    ![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%208.png)
    
    ![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%209.png)
    

1. Then, click on Share to get the link to the experiment. Copy the **Data-collection link** (NOT the Demonstration-link).

![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%2010.png)

1. Share the copied link with **two people.** These will be your participants.
    
    <aside>
    <img src="https://www.notion.so/icons/exclamation-mark_gray.svg" alt="https://www.notion.so/icons/exclamation-mark_gray.svg" width="40px" />
    
    Your participant will be prompted to enter a participation code in the beginning of the experiment. Their code should be YourLastName_Number. For example, my last name is Kim, so my participant 1 should enter “KIM_1”; my participant 2 should enter “KIM_2”.
    
    </aside>
    

1. Once you are done collecting the data, Unpublish the experiment (see Step 1 above).
2. Then download your data from Results on the right panel.
    
    ![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%2011.png)
    
    Click on the three dots right Results. Then, you will see a message like below. Click on the **‘Data-Collection’ tab. Click Download.**
    
    ![image.png](A5%20Self-paced%20reading%20task%20a5_files/image%2012.png)
    

# Submission

<aside>

On Canvas, you should submit

1. **URL: Your Demonstration-link** (NOTE: This is NOT the Data-collecton link you used for collecting data.)
2. **.csv file:** The downloaded results file
</aside>