--Displaying Covid deaths for Countries
 SELECT * FROM covid_deaths
WHERE continent IS NOT NULL
ORDER BY date, population; 


--Total Cases Vs Total Deaths and Deaths Persentage per Total Cases in Egypt
 SELECT location, date, total_cases, total_deaths,
(total_deaths / total_cases)*100 AS DeathsPersentage
FROM covid_deaths
WHERE continent IS NOT NULL AND location LIKE '%Egypt%'
ORDER BY location, date; 


--The Persentage of Population infected with covid
 SELECT location, date, total_cases, population,
(total_cases / population)*100 AS InfectionPersentage
FROM covid_deaths
WHERE continent IS NOT NULL AND location LIKE '%Egypt%'
ORDER BY location, date; 


--continent whith higest infection rates compared to population
 SELECT date, location, Max(total_cases) AS HighestInfectionCount, MAX((total_cases/population)) * 100 AS PersentPopulationInfected
FROM covid_deaths
WHERE continent IS NULL 
GROUP BY population, location, date; 


--countries with highest deaths per population
 SELECT location, MAX(cast(total_deaths AS int)) AS TotalDeathsCount
FROM covid_deaths
WHERE continent IS NOT NULL 
GROUP BY continent, location
ORDER BY TotalDeathsCount DESC; 


--Exploring vaccinations table
 SELECT * FROM covid_vaccinations; 

--Population Vs Vaccinations 
SELECT dea.date, dea.location, dea.population, vac.total_vaccinations 
FROM covid_deaths dea
JOIN covid_vaccinations vac 
ON dea.date = vac.date AND dea.location = vac.location
WHERE dea.continent IS NOT NULL; 


--creating a cte 
 WITH popvsvac (date, country, population, total_vaccinations) AS 
(SELECT dea.date, dea.location, dea.population, vac.total_vaccinations 
FROM covid_deaths dea
JOIN covid_vaccinations vac 
ON dea.date = vac.date AND dea.location = vac.location
WHERE dea.continent IS NOT NULL)

SELECT *, (total_vaccinations / population) * 100 AS vaccinations_per_population
FROM popvsvac;









