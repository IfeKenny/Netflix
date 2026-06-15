# Netflix
create database netflix_titles;
use netflix_titles;
select * from netflix_titles;
-- replacing the empty strings with none for director

SELECT director, COALESCE(NULLIF(director, ''), 'none') AS director_filled FROM netflix_titles;
select * from netflix_titles
-- set safe updates

SET SQL_SAFE_UPDATES=0;
UPDATE netflix_titles
SET director = COALESCE(NULLIF(director, ''), 'none');
select * from netflix_titles

--  replacing the empty strings with none for cast
SELECT cast, COALESCE(NULLIF(cast, ''), 'none') AS cast_filled FROM netflix_titles;

-- updating the table
UPDATE netflix_titles
SET cast = COALESCE(NULLIF(cast, ''), 'none');
select * from netflix_titles

--  replacing the empty strings with none for country
SELECT country, COALESCE(NULLIF(country, ''), 'none') AS country_filled FROM netflix_titles;

-- updating the table
UPDATE netflix_titles
SET country = COALESCE(NULLIF(country, ''), 'none');
select * from netflix_titles;
describe netflix_titles;

-- 1. Movies vs TV Shows distribution
select type, count(*) as total from netflix_titles group by type;

-- 2.Content added by year
SELECT YEAR(date_added) AS year_added, COUNT(*) AS total_titles FROM netflix_titles WHERE date_added IS NOT NULL
GROUP BY YEAR(date_added)
ORDER BY year_added;

-- 3.. Most common ratings
select rating, count(*) as ratings_common from netflix_titles group by rating order by ratings_common DESC;

-- 4. Most common genres/categories
select listed_in, count(*) as listed_common from netflix_titles group by listed_in order by listed_common DESC;

<img width="760" height="393" alt="Netflix" src="https://github.com/user-attachments/assets/b9ed45fe-5f29-4295-902a-f46aff187f26" />
