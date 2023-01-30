# Konceptuální návrh databáze
- Proces navrhování databáze => definuje strukturu dat a vzahy mezi nimi
- cílem je vytvořit logický model databáze
	- říká jak budou data uložena
	- říká jak budou data propojena
- umožňuje pochopit a popsat požadavky na databázi => vznikne struktura, pro efektivní ukládání a používání dat

## Základní prvky koncepttuálního návrhu
- **Entitní typ**
	- specifikuje jaké typy objektů budou v databázi uchovány
	- např. třída žák, učitel, ředitel...
- **Atributy**
	- charakterizují jednotlivé entitní typy
	- např. žád - jméno, příjmení, datum narození...
- **Vztahy (relace)**
	- způsob propojení mezi entitami
	- 1:1, 1:M, M:M
	- např. třída má více žáků => vztah mezi třídou a studenty

## Pojmy
- **Primární klíč** - PK (časo nazvané ...ID) 
	- unikátní hodnota, která jednoznačně identifikuje záznam (řádek) v tabulce 
	- nesmí být null
- **Cizí klíč** - FK
	- primární klíč z jiné tabulky => realizuje vazbu
- **Silná entita**
	- lze popsat jen za pomoci jejích atributů
	- může existovat i bez vazby na slabou entitu
- **Slabá entita**
	- povinná účast ve vazbě se silnou entitou
	- Může povinná vazba vést na slabou entitu????????
	- Klíč nelze vytvořit bez atributů jiné entity (cizích klíčů)
- Kardenalita
	- vyjadřuje kolik entit daného typu se na relaci podílí/může podílet
	- npř. učitel vyučuje více studentů (1:N)
- Parcialita
	- vyjadřuje povinnou účast v relaci
	- 0 - nemandatorní relace (nemusí být)
	- 1 - mandatorní realce (musí být)
	- npř. učiel NEMUSÍ vyučovat žádné studenty, ale student MUSÍ být vyučován studentem

## Relace závislostí mezi entitami
- **Agregace**
	- část může existovat bez celku
	- celek není unikátní pro všechy části
	- npř. manželství (člověk jich může během života vystřídat několik)
	![[Pasted image 20230128102314.png]]
- **Kompozice**
	- část nemůže existovat bez celku => jen mezi slabou a silnou entitou
	- npř. náku a položka v seznamu (smaže se nákup => smažou se jeho položky)
	![[Pasted image 20230128102345.png]]
- **Vazba 1:1**
	- v relalaci odpovídá jeden záznam první tabulky maximálně jednomu záznamu druhé tabulce (a naopak)
	- npř. stát a jeho hl. město
	![[Pasted image 20230128102354.png]]
- **Vazba 1:N**
	- na jeden záznam první tabulky se může vázat více záznamů druhé tabulky
	- k vazbě je použit cizí klíč
	- npř. třída a student
	![[Pasted image 20230128102516.png]]
- **Vazba M:N**
	- nelze realizovat přímo => vytvořit asociativní tabulku
	- npř. knihy a autoři (kniha může mít více autorů)
	![[Pasted image 20230128102654.png]]

