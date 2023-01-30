## DML 
= data manipulation language
- příkazy mění obsah (nikoliv strukturu) tabulky
- CRUD operace
- SELECT, INSERT, UDPATE, MERGE, DELETE, EXPLAIN
- **SELECT**
	- slouží pro získání/vypsání dat z tabulky
	- npř. SELECT soupce AS columns FROM tabulka (AS = nové pojmenování sloupce)
	- npř. SELECT jmeno, prijmeni FROM lide
	- npř. SELECT \* FROM tabulka (všechny sloupce)
- **WHERE (restrikce)**  
	- podmínka/filtrace pro jednotlivé dotazy
	- npř. SELECT jmeno FROM lide WHERE jméno = "Michal" 
-  **LIKE (restrikce)**
	- vyhledá podle zadaného výrazu
	- % představuje žádný, jeden, nebo více znaků
	- _ představuje 1 znak
	- npř. SELECT jmeno FROM lide WHERE jmeno LIKE "J%" 
- **Logické operátory**
	- =, >, <, >=
- **AND** a **OR**
	- pro spojování podmínek WHERE a LIKE
- **ORDER BY**
	- řazení dat
	- ASC => vzestupně (defaultní)
	- DESC => sestupně
	- npř. SELECT jmeno FROM lide WHERE *podminka* ORDER BY jmeno DESC
- **DISTINCT**
	- sloučí stejné řádky 
	- npř. SELECT DISTINC jmeno FROM lidé ![[Pasted image 20230128195856.png]]
- **Omezení počtu řádků - TOP, OFFSET, FETCH NEXT x ROWS ONLY**
	- npř. SELECT TOP(5) FROM lide ORDER BY prijmeni
	- npř. SELECT * FROM lide ORDER BY prijmeni OFFSET 10 ROWS
		- získej řádky od 10 dál
	- npř. SELECT * FROM lide ORDER BY prijmeni OFFSET 10 ROWS FETCH NEXT 5 ROWS ONLY (od 10. řádku jich získej 5)

## Spojování tabulek
- kartézký součin tabulek (všechny řádky tab1 se zkombinují se všemi sloupci tab2)
	- npř. SELECT * FROM tab1, tab2
	- nemá moc smysl používat
	- také funguje příkaz **CROSS JOIN**
![[Pasted image 20230128201304.png]]
- **JOIN**
	- npř. SELECT tab1.sl1, tab2.sl1 FROM tab1 JOIN tab2 ON tab1. klíč = tab2.klíč ...
- **INNER JOIN**
	- prunik => data s odpovídajícími klíči na obou stranách
	- npř. SELECT Pozice, Jmeno FROM Poz INNER JOIN Lide ON Poz.ClID = Lide.CiID
- **FULL OUTER JOIN**
	- sjednocení => každou položku z kterékoliv strany, jež chybí odpovídajcíí položky zahrne do výsledku
	- spojovaná pole bez protějškou jsou doplněna hodnotou null
	- npř. SELECT Pozice, Jmeno FROM Poz OUTER JOIN Lide ON Poz.ClID = Lide.CiID
- **LEFT / RIGHT OUTER JOIN**
	- zahrne veškeré položky z LEVÉ / PRAVÉ tabulky (název za FROM) a spojí je s odpovídajícími položkami z druhé tabulky
	- spojovaná pole bez protějškou jsou doplněna hodnotou null
	- SELECT Pozice, Jmeno FROM Poz LEFT / RIGHT JOIN Lide ON Poz.ClID = Lide.CiID

## AGREGACE
- získávání souhrných výsledků dat podle určitých kritérií
- "vezmi výsledky SELECTu a dej je dohromady podle těchto sloupečků a pak získej následující informace"
- **GROUP BY**
	- nemá smysl používat bez agregačních funkcí v seznamu sloupců
	- Na vypočítávané sloupce nelze použít WHERE
- COUNT(sloupec)
	- počet neprázdných řádků v daném sloupci 
	- lze použít *
	- npř. SELECT Jméno, COUNT(Jméno) FROM Lidé GROUP BY Jméno
- SUM(sloupec)
	- součet všech hodnot ve sloupci
- AVG(sloupec)
	- průměr hodnot ve sloupci
- MAX(sloupec)
	- největší hodnota ve sloupci
- MIN(sloupec)
	- nejmenší hodnota ve sloupci
- **HAVING**
	- restrikce na sloupce s agregovanou hodnotou
- SELECT Jméno, COUNT(Jméno) AS Počet FROM Lidé GROUP BY Jméno HAVING Počet > 
## SELECT
- **Pořadí klíčových slov**
	1. SELECT
	2. FROM
	3. WHERE
	4. GROUP BY
	5. HAVING
	6. ORDER BY
	7. OFFSET
- Pořadí zpracování
	1. Sestaví se všechny řádky a všechny sloupce na všech tabulkách (kartézský součin)
	2. Omezí se sloupce
	3. Omezí se řádky WHERE
	4. Provede se GROUP BY
	5. Vypočítají se agregované sloupce
	6. Omezí se přes HAVING
	7. Řádky se seřadí pomocí ORDER BY
## DDL
= data definition language
- příkazy mění strukturu tabulky
- CREATE, ALTER, DROP 