# Project4-Perfume
machine learning model, python, SQLite, SQL

# **Introduction Summary**

In our perfume project, we've been experimenting with machine models to understand scent categories and personalize recommendations. We're prioritizing exploration over accuracy, aiming to uncover new scent combinations and trends. Join us as we venture into the unpredictable world of fragrance, pushing the boundaries of what's possible with machine learning. Together, let's discover the unexpected and redefine how we approach perfume.

# **Methodology**

*Dataset*

- Dataset pulled from [Fragrantica.com](https://www.fragrantica.com/)

    - The datasets included:

      - Perfume name and company
     
      - A perfume image
     
      - main_accords
     
      - Top Notes, Middle Notes, and Base Notes
     
      - There was a perfume user rating up to 5
     
      - Sillage and Longevity
     
      - Price Point/Value
     
      - Gender

*Webscraping*

- Webscraping at Fragrantica could have taken up the entire timeframe for this project due to inconsistencies of website/forum

    - Tried Parsehub app
    
    - Implemented request/html.parser, beautifulsoup, scrapy.spider, selenium, splinter

- Webscraping was already done on this github: [Perfume_Designer_App](https://github.com/sir-omoreno/perfume_designer_app)

  - Scraping was done from 2021.

  - Due to web scraping limitations that they had, there were a total of 517 perfumes in the dataset

*Database*

- SQLite was utilized for dataset storage and created using Jupyter Notebook

  - An uncleaned CSV and JSON file can be uploaded from the Resources folder of the dataset

*Data Cleaning*

- Column Removal

    - Unnecessary columns were removed including: image for_gender description gender_vote price value top notes middle notes base notes
 
    - We felt that useing the main_accord column would be better for our model because top notes middle notes and base notes had more values represented
 
- Preprocessing

    - Perfumes that had a rating below 3.59 and had < or = to 100 votes were removed from the dataset for enhanced accuracy

    - main accords was divided for each perfume and a column was created for the scent_strength

    - The perfume entries were duplicated based on the number of scents in each one
 
    - Data with NaN values were removed
 
    - Ended up with 2655 entries
 
    - Merged name and company columns into one as to lessen the amount of string columns

# **Analysis**

*Part I*

Unsupervised Cluster Model

We determined that the best value for k is 4 based on this elbow curve

![originalelbowcurve](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/5cb6bafd-957b-4627-bc15-d0d095e28c64)

The random_state = 42 because 42 is the answer to the meaning of life, the universe, and everything

![Screenshot 2024-04-20 184616](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/94450b83-5eb6-4cbe-bbd0-fefdd01f2178)

We fit the K-Means model using scaled data

Here we have the original scatter plot with predicted clusters:

![originalscatterplot](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/c5c681ae-7b94-4feb-9933-9fb2c9a932c9)

For the PCA model the n_components were set to 3. After fitting and tranforming the explained variance rations were:

Explained Variance Ratios:

PCA1: 0.4162

PCA2: 0.3299

PCA3: 0.2539

Total Explained Variance: 1.0000

The best value for k when using the PCA data is also 4.

![pcaelbowcurve](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/c195ed6a-6077-428a-a1e5-2e844885a36f)

Here is the PCA scatter plot with predicted clusters:

![pcascatterplot](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/8f81a669-1125-4ba3-ba68-265dfd78138b)

*Part II*

We were unsuccessful at completing a decision tree chatbot with our dataset. We had too many strings and our dataset became too convoluted as we used OneHot Encoder and LabelCoder. Most machine models use integers and many use very clear X and y variables. We recleaned our dataframe such that the scents were each divided into their own columns with 0's and 1's to indicate if a perfume had that scent in it or not. This in turn created a chaotic mess of machine models (62) each with a different accuracy percentage ranging from 52% to 100%.

![dftransformation](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/2871a4cc-a60e-43d4-9a8b-d87b4ad8ebc3)


# **Recommendations**

# **Conclusion**

# **Citations**

Students: 

[Cory Chapman](https://www.linkedin.com/in/thatcorygirl/)

[Amanda Hinkle](https://www.linkedin.com/in/amanda-hinkle-9105941b6/)

[Katie Starnes](https://www.linkedin.com/in/katie-starnes-7aa037204/)

Instructor:

[Othmane Benyoucef](https://www.linkedin.com/in/othmanebenyoucef/)

Suggestions for datacleaning [.melt()](https://www.geeksforgeeks.org/python-pandas-melt/) and .apply() from Stephen Greenberg and Jesus Parra

Used import ast for dataframe transformation from [docs.python.org](https://docs.python.org/3/library/ast.html)
