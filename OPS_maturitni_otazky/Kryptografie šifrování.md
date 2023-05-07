- dnes se moderně používají eliptické křivky => počítané hardwarově a nejsou prolomitelné ani s využitím kvantových počítačů
## Symetrická
- 
## Asymetrická
- používá se k autentizaci a přenosu klíčů
- veřejný a soukromý klíč
	- veřejným "zamikáme" a soukromým "odemykáme"
- Přenos důvěry
- Problémy certifikátů
	- nedůvěryhodnost a chyba ze strany člověka
	- podvržení certifikátů => stejně jako DNS cache poisoning => podvržení adres 
## Hashe
- vychází z principu kontrolního součtu
- nejznámějším je CRC32 (32bitů)
- SHA (secure hash algorithm)
	- později se za název přidávaly čísla (vyšší počet bitů =>  bezpečnost)
- neprozrazuje velikost zahashovaného souboru
- při změně jediného bitu vzniká úplně jiný hash 
- neměly by existovat žádné dva soubory se stejným hashem (nesmí nastat kolize)
- hackování funguje následovně
	- ukradnu databázy zahashovaných hesel
	- vezmu databázy hesel (ve stringu) => vezmu HashCat => svou databázy hesel začnu hashovat a výsledky porovnávám se zaheshovanou databází => najdu shodu = na 90% jsem prolomil heslo
	- jednou prolomené heslo není nikdy bezpečné (hacker ho bude mít ve své databázy string hesel)

