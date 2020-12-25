# 1980’den itibaren herhangi bir spor grubunda üst üste 3 veya daha fazla madalya almış atletleri bulalım.
```SQL
SELECT * FROM (
    SELECT Sport, Athlete, COUNT(1) as Medals, ROW_NUMBER() OVER(PARTITION BY SPORT ORDER BY COUNT(1) desc) AS Row
    FROM `dsmbootcamp.sample.summer_medals`
    WHERE Medal is not null and year >= 1980
    GROUP BY Sport, Athlete
    ORDER BY Sport, COUNT(1) desc
) WHERE Medals >= 3
```
