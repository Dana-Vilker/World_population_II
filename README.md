# World_population_II
World Population Project from Codecademy

--How many entries in the countries table are from Africa?

SELECT COUNT(*)
FROM countries
WHERE continent = 'Africa';

--What was the total population of the continent of Oceania in 2005?

SELECT SUM(population)
FROM population_years
JOIN countries
  ON population_years.country_id = countries.id
WHERE continent = 'Oceania' AND year = 2005;

-- What was the average population of countries in South America in 2003?

SELECT AVG(population)
FROM population_years
JOIN countries
  ON population_years.country_id = countries.id
WHERE continent = 'South America' AND year = 2005;

--What country had the smallest population in 2007?

SELECT population_years.population,
		countries.name
FROM population_years
JOIN countries
	ON population_years.country_id = countries.id
WHERE population_years.year = 2007
	and population_years.population is not NULL
ORDER by 1 ASC
limit 1;

--What is the average population of Poland during the time period covered by this dataset?

SELECT AVG(population_years.population)
FROM population_years
JOIN countries
  ON population_years.country_id = countries.id
WHERE countries.name = 'Poland';

--How many countries have the word "The" in their name?

SELECT COUNT(*)
FROM countries
WHERE name LIKE '%The%';

--What was the total population of each continent in 2010?

SELECT SUM(population_years.population), countries.continent
FROM population_years
JOIN countries
  ON population_years.country_id = countries.id
GROUP BY countries.continent;
