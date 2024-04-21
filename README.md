# Project4-Perfume
machine learning model, python, SQLite, SQL

# **Introduction Summary**

In our perfume project, we've developed two machine models: one for categorizing scents and another for recommending perfumes based on user preferences. Accuracy is our top priority. With these models, we aim to make navigating the world of fragrances easier and more enjoyable for everyone.

Let's explore scent popularity and combinations together. Maybe we can find the perfect perfume just for you! Join us on this olfactory journey of discovery and delight.

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
