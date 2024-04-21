# Project4-Perfume
technologies used: machine learning model, python, pandas, hvplot,pandas, sqlite3, ast,  SQLite, SQL, Scikit-learn, sklearn.cluster, KMeans, sklearn.decomposition, PCA, StandardScaler, Tableau, Canva  

# **Introduction Summary**

In our perfume project, we've been experimenting with machine models to understand scent categories and personalize recommendations. We're prioritizing exploration over accuracy, aiming to uncover new scent combinations and trends. Join us as we venture into the unpredictable world of fragrance, pushing the boundaries of what's possible with machine learning. Together, let's discover the unexpected and redefine how we approach perfume.

We invite you to take a look at our [Canva Presentation](https://www.canva.com/design/DAGB-Xct9so/zUYbIlq8RsFhcxc-5W-1cA/view?utm_content=DAGB-Xct9so&utm_campaign=designshare&utm_medium=link&utm_source=editor)

# **Problem Worth Solving**

The problems we are trying to solve are two-fold.

- The first problem is can we create an unsupervised clustering machine model that performs with accuracy?

- The other problem is can we recommend a perfume for you and/or can we predict if you like a perfume brand based on your inputs (using a chatbot)? 

# **Methodology**

**For more details and documentation on our process, please visit the [Projects Tab](https://github.com/users/ThatCoryGirl/projects/3) associated with this project**

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

    - Tried [Parsehub](https://www.parsehub.com/) app
    
    - Implemented `request` `html.parser` `beautifulsoup` `scrapy.spider` `selenium` `splinter`

- Webscraping was already done on this github: [Perfume_Designer_App](https://github.com/sir-omoreno/perfume_designer_app)

  - Scraping was done from 2021.

  - Due to web scraping limitations that they had, there were a total of 517 perfumes in the dataset

*Database*

- SQLite was utilized for dataset storage and created using Jupyter Notebook

  - An uncleaned CSV and JSON file can be uploaded from the Resources folder of the dataset

*Data Cleaning*

- Column Removal

    - Unnecessary columns were removed including: **image**, **for_gender**, **description**, **gender_vote**, **price value**, **top notes**, **middle notes**, **base notes**
 
    - We felt that useing the **main_accord** column would be better for our model because **top notes**, **middle notes**, and **base notes** had more values represented
 
- Preprocessing

    - Perfumes that had a rating below 3.59 and had < or = to 100 votes were removed from the dataset for enhanced accuracy

    - **main accords** was divided for each perfume and a column was created for the **scent_strength**

    - The perfume entries were duplicated based on the number of scents in each one
 
    - Data with **NaN** values were removed
 
    - Ended up with 2655 entries
 
    - Merged **name** and **company** columns into one as to lessen the amount of string columns

# **Analysis**

*Part I*

Unsupervised Cluster Model

We determined that the best value for `k` is 4 based on this elbow curve

![originalelbowcurve](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/5cb6bafd-957b-4627-bc15-d0d095e28c64)

The **random_state** = 42 because 42 is the answer to the meaning of life, the universe, and everything

![Screenshot 2024-04-20 184616](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/94450b83-5eb6-4cbe-bbd0-fefdd01f2178)

We fit the K-Means model using scaled data

Here we have the original scatter plot with predicted clusters:

![originalscatterplot](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/c5c681ae-7b94-4feb-9933-9fb2c9a932c9)

For the PCA model the **n_components** were set to 3. After fitting and tranforming the explained variance rations were:

Explained Variance Ratios:

PCA1: 0.4162

PCA2: 0.3299

PCA3: 0.2539

Total Explained Variance: 1.0000

The best value for `k` when using the PCA data is also 4.

![pcaelbowcurve](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/c195ed6a-6077-428a-a1e5-2e844885a36f)

Here is the PCA scatter plot with predicted clusters:

![pcascatterplot](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/8f81a669-1125-4ba3-ba68-265dfd78138b)

*Part II*

Decision Tree ChatBot

We were unsuccessful at completing a decision tree chatbot with our dataset. We had too many strings and our dataset became too convoluted as we used `OneHot Encoder` and `LabelCoder`. Most machine models use integers and many use very clear `X` and `y` variables. We recleaned our dataframe such that the scents were each divided into their own columns with 0's and 1's to indicate if a perfume had that scent in it or not. This in turn created a chaotic mess of machine models (62) each with a different accuracy percentage ranging from 52% to 100%.

![dftransformation](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/2871a4cc-a60e-43d4-9a8b-d87b4ad8ebc3)

*Part III*

To further analyze our data we were able to create a [Tableau](https://public.tableau.com/app/profile/katie.starnes/viz/PerfumeWIP/PerfumeDashboard?publish=yes) dashboard. Here's a preview but please feel free to follow the link to the actual dash.

Interactive Visualization to break down the Top 100 perfumes from our dataset

![Perfume Dashboard](https://github.com/ThatCoryGirl/Project4-Perfume/assets/146380542/0bbbab85-faed-4350-aa54-18d8524026af)

This dash shows the most popular scents and the branded perfumes that include them. You can choose which perfume you want in the middle of the dashboard and it will break down all of the details about that specific perfume in each visualization. It will show you the **rating**, **vote counts**, **gender**, and **fragrances** associated with each perfume.


# **Recommendations & Conclusions**

We recommend that a lot more time be dedicated to dataset scraping and machine model research. Our dataset did not have enough numerical/integer values. We cleaned the data in a way that it did not cater to one of our machine models. It would have been a good idea to explore scents based on gender selection but this was already done in the github cited above. Having a dataset with a column that identified two variables would be best either yes/no or 1/0. We could have focused more on reviews. And dates could have been useful for our data as we didn't have any.

However our unsupervised clustering model worked pretty well with the data. It was surprising how much the data changed with the PCA transformation. We were experimenting with the idea of 5 clusters instead of 4 but the accuracy messed up with 5 so we stuck with 4.

# **Citations**

Students: 

[Cory Chapman](https://www.linkedin.com/in/thatcorygirl/)

[Amanda Hinkle](https://www.linkedin.com/in/amanda-hinkle-9105941b6/)

[Katie Starnes](https://www.linkedin.com/in/katie-starnes-7aa037204/)

Instructor:

[Othmane Benyoucef](https://www.linkedin.com/in/othmanebenyoucef/)

Suggestions for datacleaning [.melt()](https://www.geeksforgeeks.org/python-pandas-melt/) and .apply() from Stephen Greenberg and Jesus Parra

Used `import ast` for dataframe transformation from [docs.python.org](https://docs.python.org/3/library/ast.html)
