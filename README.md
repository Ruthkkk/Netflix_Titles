# Netflix_Titles
Code written by Ruth Igbinigie
Netlix is one of the most popular media and video streaming platforms. They have over 8000 movies or tv shows available on their platform
The dataset was gotten from Kaggle https://www.kaggle.com/datasets/shivamb/netflix-shows?resource=download

# Tool used:
# Excel and Sql was used on this project
# Excel:
The data was very messy so I used excel to to do some data cleaning such as removing unwanted columns and blank spaces. I also did quote a lot of find and replace to corect some spellings such as:
√© replaced with é,
√º- replaced with u,
√° replaced with a,
ƒ± replaced with i,
ƒü replaced with a,
√≠ replaced with I,
√≥ replaced with ó,
ƒ± replaced with I,
√∂ replaced with o,
√ñ replaced with o,
√ß replaced with c,
√± Replaced with n,
ƒÖ replaced with a,
≈Ç replaced with eL,
ƒ∞ replaced with I,
√® replaced with è,
√¥ replaced with ô,
√´ replaced ë,
√∫ replaced with u,
√• replaced with å,
√Å replaced with å,
√∏ replaced with ø,
Æ replaced with ô,
≈º replaced with ż,
√¶ replaced with ae,
√Ø replaced with i,
√ò replaced with ø,
√£ replaced with ã,
√° replaced with a,
√â replaced with e

# SQL
I used SQL to analyze Netflix Movie & Tv shows up to mid 2021
This dataset consists of listings of all the movies and tv shows available on Netflix, along with details such as - cast, directors, ratings, release year, duration, etc. Below are some of my analysis:

# Selecting all from the Netflix
SELECT *
FROM [Netflix ] 

# TV SHOWS In Netflix
SELECT *
FROM [Netflix ] 
WHERE [type] = 'TV Show';

# Movies on Netflix
SELECT *
FROM [Netflix ] 
WHERE [type] = 'Movie';

# How many shows and movies are available on Netflix?
SELECT type, COUNT(type) AS CountOfContent
FROM [Netflix ]
GROUP BY [type];


# What are the top 10 countries with the most content available on Netflix?
SELECT TOP 10 country 
FROM [Netflix ]; 


# How many TV shows and movies are available in each content rating category (e.g., TV-MA, TV-PG, PG-13)?
SELECT rating, type, COUNT([type]) as CountOfContent 
FROM [Netflix ]
WHERE rating IN ('TV-MA', 'TV-PG', 'PG-13')
GROUP BY type, rating
ORDER BY CountOfContent DESC;


# What are the top 10 genres or categories of content available on Netflix?
SELECT TOP 10 listed_in
FROM [Netflix ]


# How many shows and movies were released in each year? Are there any trends over the years?
SELECT type, release_year, COUNT([type]) as CountOfContent
FROM [Netflix ]
GROUP BY type,release_year
ORDER BY CountOfContent DESC, release_year DESC;


# Which directors have produced the most content on Netflix?
SELECT director, COUNT(show_id) as CountOfContent
FROM [Netflix ]
GROUP BY director
ORDER BY CountOfContent DESC;

# What is the average duration of TV shows and movies on Netflix?
-- Calculate average duration of TV shows and movies on Netflix
SELECT 
    AVG(
        CASE
        WHEN duration LIKE '% min' THEN CAST(SUBSTRING(duration, 1, CHARINDEX(' min', duration) - 1) AS INT)
        WHEN duration LIKE '% Season%' THEN 0  -- Assuming each season has no duration, you can adjust this if needed
        END
    ) AS average_duration_minutes
FROM [Netflix ];

# Which countries has the most TV shows and movies available?
SELECT country, type, COUNT(*) AS CountOfContent
FROM [Netflix ]
GROUP BY country, [type]
ORDER BY CountOfContent DESC;


# Which TV shows or movies were the director is Marcus Raboy
SELECT type, title 
FROM [Netflix ]
WHERE director LIKE '%Marcus Raboy%';
