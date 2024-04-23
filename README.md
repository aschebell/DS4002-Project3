# DS4002-Project3 

## Contents of Repository
This repository contains the code and documentation for investigating whether it is possible to predict the primary types of different Pokemon based on the hex color codes found in their graphic images. This repository contains a README file, LICENSE file, SCRIPTS folder, DATA folder, and OUTPUT folder. 

## Section 1: Software and Platform Section
- Software Used: RStudio (R)
- Packages Used: tidyverse, randomForest
- Platform used: Mac

## Section 2: Map of Documentation 

- Outline or tree of hierarchy of folders and subfolders and list the files stored in each folder
```mermaid
graph TD;
    README.md;
    LICENSE.md;
    SCRIPTS-->randomForest_building.rmd;
    DATA-->pokemon.csv-->colorDataPokemon.csv-->trainingset.csv-->testingset.csv-->testingset2.csv;
    OUTPUT-->confusion_matrix1.png-->confusion_matrix2.png-->error_rate.png
```

## Section 3: Instructions for Reproducing Results

GET THE DATA:
1. AVERYYYYYY 

CLEAN THE DATA:
1. AVERYYYYYY

CREATE EXPLORATORY PLOTS FOR EDA:
1. Use ggplot to create different bar plots that will help to visualize our data, where the Pokemon type is on the x-axis and the frequency of respective Pokemon types are on  the y-axis for each graph
2. Create sample color palettes and plots for specific Pokemon to see what the hex codes represent (and to display the different hues of color)
3. Save these plots into the OUTPUT folder

DATA PREP FOR BASIC CLASSIFICATION TREE MODEL BUILDING:
1. Read in the previously cleaned data as a csv file in R
2. Convert the "sex", "name", and "region" variables into factor variable types
3. Remove unnecessary columns from our current data frame -- this should include the "decades" column (which we won't need for analysis), the first column, and the "stat_abb" column
4. Use the uncount() function in R where the "weights" argument is set equal to the "count" column to expand our data based on the count column
   - After this step each row should represent one single baby in our data set
5. Set the seed using set.seed(4002) --> you can use a random number but make sure to stay consistent throughout the project
6. Split our data set now into a training and a test data set with a 70/30 split

BASIC CLASSIFICATION TREE -- RECURSIVE BINARY SPLITTING:

1. Use the tree::tree(...,data=...) function from the tree library in R to create the first basic classification tree model
2. Apply summary() to the classification tree created above
   - This will give you the significant variables used, the number of terminal nodes, the residual mean deviance, and also the misclassification error rate of the model (test error rate!)
3. Apply plot() and text() to the classification tree created in (1) to view the graphical output
4. Optional: Use the y response of our data set, the y response of our test data set, the tree we created in (1), the predict() function, and the table() function in R to create a confusion matrix

CLASSIFICATION TREE USING RPART PACKAGE IN R:
1. Use the rpart() and rpart.plot() functions from the rpart and rpart.plot packages in R to create classification trees that are more informative and visually appealing than the basic models we created above
   - The rpart() method can be used on our data set to actually create the classification tree, while the rpart.plot() method is used to output the classification tree graphically

PRUNE THE CLASSIFICATION TREE:
1. You may need to use the tree::cv.tree() and tree::prune.misclass() functions on our initial basic classification tree model to remove some of the branches, reduce its complexity, or improve its general performance-- pruning a classification tree generally prevents overfitting of the data in the model
   - Note that in our project, when we pruned the classification tree using our data set and then reapplied the plot() function on our tree to observe its graphical output, our tree looked exactly the same as before pruning-- in this specific case it appears that pruning the classification tree will not lead to significant improvements

ANSWER THE RESEARCH QUESTION AND DETERMINE FUTURE PROJECT IMPROVEMENT:
1. Since our original research question asked whether we could create a model to successfully determine the sex of unisex-named babies (under the hypothesis that we would have more female than male babies), the last step of this investigation would be to look at the test error rate of our model to determine its success, and also the ending branches of the model to determine whether our hypothesis is supported by the model we created
2. Ask: are there any underlying trends in the classification model we created that we did not anticipate, but can help to lead us into further investigation?
3. With time allowing, after pruning our classification tree we would want to use explore methods that could potentially create more accurate models, such as bagging, random forests, and boosting

