USE world;

Q1. Count how many cities are there in each country
SELECT c.Name AS Country,
       COUNT(ci.ID) AS Total_Cities
FROM country c
JOIN city ci
ON c.Code = ci.CountryCode
GROUP BY c.Name;

Q2. Display all continents having more than 30 countries
SELECT Continent,
       COUNT(*) AS Total_Countries
FROM country
GROUP BY Continent
HAVING COUNT(*) > 30;

Q3.List regions whose total population exceeds 200 million
SELECT Region,
       SUM(Population) AS Total_Population
FROM country
GROUP BY Region
HAVING SUM(Population) > 200000000;

Q4.Find the top 5 continents by average GNP per country
SELECT Continent,
       AVG(GNP) AS Avg_GNP
FROM country
GROUP BY Continent
ORDER BY Avg_GNP DESC
LIMIT 5;
Q5. Find the total number of official languages spoken in each continent
SELECT c.Continent,
       COUNT(cl.Language) AS Official_Languages
FROM country c
JOIN countrylanguage cl
ON c.Code = cl.CountryCode
WHERE cl.IsOfficial = 'T'
GROUP BY c.Continent;

Q6. Find the maximum and minimum GNP for each continent
 SELECT Continent,
       MAX(GNP) AS Max_GNP,
       MIN(GNP) AS Min_GNP
FROM country
GROUP BY Continent;

Q7. Find the country with the highest average city population
SELECT c.Name AS Country,
       AVG(ci.Population) AS Avg_City_Population
FROM country c
JOIN city ci
ON c.Code = ci.CountryCode
GROUP BY c.Name
ORDER BY Avg_City_Population DESC
LIMIT 1;

Q8.List continents where the average city population is greater than 200,000
SELECT c.Continent,
       AVG(ci.Population) AS Avg_City_Population
FROM country c
JOIN city ci
ON c.Code = ci.CountryCode
GROUP BY c.Continent
HAVING AVG(ci.Population) > 200000;

Q9. Find the total population and average life expectancy for each continent, ordered by average life expectancy (DESC)
SELECT Continent,
       SUM(Population) AS Total_Population,
       AVG(LifeExpectancy) AS Avg_Life_Expectancy
FROM country
GROUP BY Continent
ORDER BY Avg_Life_Expectancy DESC;

Q10.Top 3 continents with highest average life expectancy (total population > 200 million)
SELECT Continent,
       AVG(LifeExpectancy) AS Avg_Life_Expectancy,
       SUM(Population) AS Total_Population
FROM country
GROUP BY Continent
HAVING SUM(Population) > 200000000
ORDER BY Avg_Life_Expectancy DESC
LIMIT 3;

 
