Solutions to SQL Queries (Countries)

Table aliasing is not used in these example solutions, but it is perfectly acceptable if students chose to implement this practice.

​1. What query would you run to get all the countries with Surface Area below 501 and Population greater than 100,000? Include the country name, surface area, and population in your results.


SELECT countries.name, countries.surface_area, countries.population
FROM countries
WHERE countries.surface_area < 501 AND countries.population > 100000;

![Screenshot 2023-08-05 at 6 34 52 PM](https://github.com/hdtran103/D.E-SQL-Queries/assets/127581702/f55a0157-34de-4adf-a0d5-27ed0ec09be8)


2. What query would you run to get countries with only Constitutional Monarchy with a capital greater than 200 and a life expectancy greater than 75 years?  Include the country name, form of government, and capital in your results.


SELECT countries.name, countries.government_form, countries.capital
FROM countries
WHERE countries.government_form = 'Constitutional Monarchy'
	AND countries.life_expectancy > 75
	AND countries.capital > 200;

![Screenshot 2023-08-03 at 5 33 20 PM](https://github.com/hdtran103/D.E-SQL-Queries/assets/127581702/5ce7aa74-9062-418e-81f6-6f5b9f4c6c23)

3. What query would you run to summarize the number of countries in each region? The query should display the name of the region and the number of countries. Also, the query should arrange the result by the number of countries in descending order. ​​
SELECT countries.region, COUNT(countries.id) AS num_countries   
FROM countries
GROUP BY countries.region
ORDER BY num_countries DESC;

![Screenshot 2023-08-05 at 6 13 40 PM](https://github.com/hdtran103/D.E-SQL-Queries/assets/127581702/4c25d557-79cd-4219-b8ed-f3ce67599f8d)

4. What query would you run to get all the countries that speak Slovene? Your query should return the name of the country, language and language percentage. Your query should arrange the result by language percentage in descending order. 
SELECT countries.name, languages.language, languages.percentage
FROM countries
JOIN languages ON countries.id = languages.country_id
WHERE languages.language = 'Slovene'
ORDER BY languages.percentage DESC;

![Screenshot 2023-08-05 at 6 18 05 PM](https://github.com/hdtran103/D.E-SQL-Queries/assets/127581702/5f9f24b4-635d-4e9b-87e6-e6e64e1b9f71)

5. What query would you run to display the total number of cities for each country? Your query should return the name of the country and the total number of cities. Your query should arrange the result by the number of cities in descending order. 
SELECT countries.name, COUNT(cities.id) as num_cities
FROM countries
JOIN cities ON countries.id = cities.country_id
GROUP BY countries.id
ORDER BY num_cities DESC;

![Screenshot 2023-08-05 at 6 22 23 PM](https://github.com/hdtran103/D.E-SQL-Queries/assets/127581702/d85a6059-3fc4-4feb-bd56-68db4c3d465c)

6. What query would you run to get all the cities in Mexico with a population of greater than 500,000? Your query should arrange the result by population in descending order. 
SELECT cities.name, cities.population
FROM countries
JOIN cities ON countries.id = cities.country_id
WHERE countries.name = 'Mexico' AND cities.population > 500000
ORDER BY cities.population DESC;

![Screenshot 2023-08-05 at 6 25 15 PM](https://github.com/hdtran103/D.E-SQL-Queries/assets/127581702/f4b26bb8-2a1f-4c66-9c3c-ac3fa4429c4d)

7. What query would you run to get all languages in each country with a percentage greater than 89%? Include the country name, language, and percentage.  Your query should arrange the result by percentage in descending order.
SELECT countries.name, languages.language, languages.percentage
FROM countries
JOIN languages ON countries.id = languages.country_id
WHERE languages.percentage > 89
ORDER BY languages.percentage DESC;

![Screenshot 2023-08-05 at 6 26 57 PM](https://github.com/hdtran103/D.E-SQL-Queries/assets/127581702/9ff53eeb-4c16-4f1b-a5cb-adc114e52da7)

8. What query would you run to get all the cities of Argentina inside the Buenos Aires district and have the population greater than 500, 000? The query should return the Country Name, City Name, District and Population. 

SELECT countries.name, cities.name, cities.district, cities.population
FROM countries
JOIN cities ON countries.id = cities.country_id
WHERE countries.name = 'Argentina'
	AND cities.district = 'Buenos Aires'
	AND cities.population > 500000;

![Screenshot 2023-08-05 at 6 28 21 PM](https://github.com/hdtran103/D.E-SQL-Queries/assets/127581702/2e710217-6629-4d70-91d0-954336659b55)
