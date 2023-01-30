# Jazyk SQL
= structured query language
- dotazovací jazyk (připodobněný angličtině)
- práce s daty v relačních databázích (tabulky)
- nástup jazyka SEQUEL
- Různé dialekty (MySQL, MsSQL, SQL Server...)
- udržuje a definuje standady ISO a ANSI 
	- syntaxe, datové typy a funkce jazyka
	- implementace RDBMS (Relational Database Management System) - systém pro řízení databáze
- **DML** 
	- Data modeling language
	- Jazyk pro manipulování s daty
	- SELECT, INSERT, UPDATE, DELETE
- **DDL**
	- Data definition language
	- Definice struktury DB
	- CREATE, ALTER, DROP
- **DCL**
	- Data control language
	- řízení přístupu k datům
	- GRANT, REVOKE, ROLLBACK, START TRANSACTION, COMMIT
- **TCL**
	- transaction control language
	- pro řízení transakcí
	- COMMIT, ROLLBACK, SAVEPOINT

## SQL příkazy a jejich funkčnost
- **INSERT**
	- přidá položku do databáze
	- npř. INSERT INTO Zamestnanci (id, jmeno, prijmeni) VALUES (55, 'Jan', 'Novak')
- **UPDATE**
	- slouží k modifikaci již existujících záznamů v tabulce
	- npř. UPDATE table_name SET column1 = value1, column2 = value2... WHERE condition
- **DELETE**
	- vymaže záznamy z tabulky
	- npř. DELETE FROM table_name WHERE condition
- **CREATE**
	- vytvoří novou tabulku v databázi
	- CREATE TABLE People (PersonID, LastName varchar(255), FirstName varchar (255)...);
- **ALTER** 
	- přidání/odstranění/úprava sloupců v již existující tabulce
	- npř. ALTER TABLE Customers ADD Email varchar(255);
	- npř. ALTER TABLE Customers DROP COLUMN Email;
- **DROP** a **TRUNCATE**
	- odstraní definici tabulky a všechny jejích data, indexy, triggery, omezení a specifikace
	- po odstranění jsou všechny tabulkové informace navždy ztraceny
	- npř. DROP TABLE table_name => vymaže tabulku i obsah
	- npř. TRUNCATE TABLE table_name => vymaže obsah tabulky
- **GRANT**
	- poskytne oprávnění k tabulkám (SELECT, INSERT, UPDATE, DELETE)
	- npř. GRANT privilege_name ON object_name TO {user_name | PUBLIC | role_name} \[WITH GRANT OPTION]
- **REVOKE**
	- odebere práva
	- npř. REVOKE privilege_name ON object_name FROM {user_name | PUBLIC | role_name}

## Transakce
= sekvence jednoho, či více SQL dotazů, které jsou vykonány najednou
- **BEGIN TRANSACTION**
	- započne novou transakci
- **COMMIT**
	- uloží změny vytvořené během transakce
- ROLLBACK
	- zahodí všechny změny vytvořené během transakce => tabulka se vrátí do stavu před jejím započetím
	- Realizováno pomocí opačných dotazů, které si databáze při spuštění transakce vytvoří 
		- efektivita => nepočítá se s navrácením původního stavu (ve většině případů proběhnou transakce úspěšně)
		- pokud nastane chyba => zavolají se všechny zpětné dotazy => navrácení původního stavu