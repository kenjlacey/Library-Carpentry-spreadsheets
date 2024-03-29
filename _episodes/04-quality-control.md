---
title: Basic quality assurance and control, and data manipulation in spreadsheets
teaching: 20
exercises: 10
questions:
  - "How can you keep data clean and sane?"
objectives:
  - "Apply quality assurance techniques to limit incorrect data entry."
  - "Apply quality control techniques to identify errors in spreadsheets."
keypoints:
  - "Use data validation tools to minimise the possibility of input errors."
  - "Use sorting and conditional formatting to identify possibly errors."

authors:
  - Jez Cope
  - Christie Bahlai
  - Aleksandra Pawlik
contributors:
  - Jennifer Bryan
  - Alexander Duryee
  - Jeffrey Hollister
  - Daisie Huang
  - Owen Jones
  - Ben Marwick
  - Ethan White
---


When you have a well-structured data table, you can use several simple
techniques within your spreadsheet to ensure the data you enter is
free of errors. These approaches include techniques that are
implemented **prior to entering data** (**quality assurance**) and
techniques that are used **after entering data to check for errors**
(**quality control**).

# Quality Assurance

Quality assurance stops bad data from ever being entered by checking to see if
values are valid during data entry. For example, if research is being conducted
at sites A, B, and C, then the value V (which is right next to B on the
keyboard) should never be entered. Likewise if one of the kinds of data being
collected is a count, only integers greater than or equal to zero should be
allowed.

To control the kind of data entered into a a spreadsheet we use Data Validation
(Excel) or Validity (LibreOffice Calc), to set the values that can be entered
in each data column.

1. Select the cells or column you want to validate

2. On the `Data` tab select `Data Validation`

   ![Image of Data Validation button on Data tab](../fig/data_validation.png)

3. In the `Allow` box select the kind of data that should be in the
   column. Options include whole numbers, decimals, lists of items, dates, and
   other values.

   ![Image of Data Validation window](../fig/04-Data_Validation.png)

4. After selecting an item enter any additional details. For example if you've
   chosen a list of values then enter a comma-delimited list of allowable
   values in the `Source` box.

We can't have half a person attending a workshop, so let's try this
out by setting the `num_registered` column in our spreadsheet to only
allow whole numbers between 1 and 100.

1. Select the `num_registered` column
2. On the `Data` tab select `Data Validation`
3. In the `Allow` box select `Whole number`
4. Set the minimum and maximum values to 1 and 50.

![Image of Data Validation window for validating plot values](../fig/04-Data_Validation_Whole_number.png)

Now let's try entering a new value in the num_registered column that isn't a valid
class size. The spreadsheet stops us from entering the wrong value and asks us if we
would like to try again.

![Image of error when trying to enter invalid data](../fig/04-Data_Validation_restrictions_apply.png)

You can also customize the resulting message to be more informative by entering
your own message in the `Input Message` tab

![Image of Input Message tab](../fig/04-Data_Validation_Valid_class_size.png)

and allow invalid data to just result in a warning by modifying the `Style`
option on the `Error Alert` tab.

![Image of Error Alert tab](../fig/04-Data_Validation_Error_Tab.png)

Quality assurance can make data entry easier as well as more robust. For
example, if you use a list of options to restrict data entry, the spreadsheet
will provide you with a drop-downlist of the available items. So, instead of
trying to remember the initials of all your trainers, you can just select the
right option from the list.

![Image of drop-down menu](../fig/04-Data_Validation_List.png)

# Quality Control

> ## Tip!
>
> Before doing any quality control operations, save your original file with the formulas and a name indicating it is the original data. Create a **separate file** with appropriate naming and versioning, and ensure your data is stored as **values** and not as **formulas**.  Because formulas refer to other cells, and you may be moving cells around, you may compromise the integrity of your data if you do not take this step!
{: .callout}

**readMe (README) files:** As you start manipulating your data files, create a readMe document / text file to keep track of your files and document your manipulations so that they may be easily understood and replicated, either by your future self or by an independent researcher. Your readMe file should document all of the files in your data set (including documentation), describe their content and format, and lay out the organizing principles of folders and subfolders. For each of the separate files listed, it is a good idea to document the manipulations or analyses that were carried out on those data.

<!-- [Example: converting all data to values: use soybean aphid suction trap dataset for this section] -->

## Sorting

**Bad values often sort to bottom or top of the column**. For example, if your data should be numeric, then alphabetical and null data will group at the ends of the sorted data. Sort your data by each field, one at a time. Scan through each column, but pay the most attention to the top and the bottom of a column.
If your dataset is well-structured and does not contain formulas, sorting should never affect the integrity of your dataset.

> ## Exercise
>
> Let's try this with the *Date* tab in our messy spreadsheet. Go to that tab. Select
> **Data** then select **Sort**
>
> Sort by `date` in the order *Smallest to Largest*
>
> ![Figure of Sorting menu](../fig/sorting.png)
>
> - When you do this sort, do you notice anything strange?
>
> - Try sorting by other columns. Anything strange there?
{: .challenge}


## Conditional formatting ##

Use with caution! But a great way to flag inconsistent values when entering data.

Conditional formatting basically can do something like color code your values by some
criteria or lowest to highest. This makes it easy to scan your data for outliers.

> ## Exercise:
>
> Let's try this again with weight. Go to **Format** then **Conditional Formatting**.
>
> We'll do the *2-Color Scale* with Lowest to Highest for the orange colors. Then we'll
> apply that to the `len_hours` column again. Now we can scan through and different colors will
> stand out. Again, do we notice any strange values?
>
> It is nice to do be able to do these scans in spreadsheets, but we also can do these
> checks in a programming language like Python or R, or in OpenRefine or SQL.
{: .challenge}
