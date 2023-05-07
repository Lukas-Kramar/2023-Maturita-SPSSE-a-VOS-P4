----

- většinově se GPU používají pro zpracování grafiky (filmy, hry, renderování, 3D modeling)
	- práce s vektory / maticemi
- GPU lze využít i k jiným náročným výpočtům
	- vědecké účely (simulace vývoje bílkovin, výpočty pro chování tělěs ve vesmíru)
	- prolamování hesel
	- těžení crypta
	- machine learning

### Proč jsou GPU lepší než CPU

- mají mnohem větší výpočetní výkon
	- **stovky až tisíce jader** (rozsháhlé možnosti pro paralelizaci) = **pipelining**
	- výrazný posun až 2007 s příchodem jader CUDA a Stream od ATI
- teoreticky je každé jádro schopno provést 32bit operaci v jednom cyklu 
- mnohem rychleji řeší složité matematické problémy
	- vychází z jejich speciální navržení pro práci s maticemi + jiné matematické operace => CPU jsou navrženy pro různorodé úkoly 
- **GPU mají širší paměťové pásmo** => mnohem rychleji přesouvají data mezi pamětí a procesorem 
- lepší poměr **výkon / watt** (GPU jsou sice mnohem žravější ale potom mají i lepší efektivitu provozu)

####  **CUDA jádra**

- Compute Unified Device Architecture
- only C, C++ jazyky
- nadesignovány přímo pro **paralelní úlohy** ("stejné instrukce, ale jiná data")
- spoléhá na "bloky vláken"
- *podporuje různé jazyky API => Fortran, OpenCL, C, nebo DirectX Compute*

#### **OpenCL jádra**

- open source standart pro paralelizování úloh (GPU)
- jsou multiplatformí (Win, Linux, Mac OS) => crossplatform
	- CUDA jsou jen Nvidia devices only
- versatilnější oproti CUDA (neřeší na které hadrdwaru běží)
- podporuje C, C++ a další jazyky
- mnohem "jemnějšíš" ohledně pralelizace => pracuje přímo s jádry / vlákny
- o něco pomalejší než CUDA (daň za to že nejsou přímo specializované pro daný hardware)
- lepší debugging  - tools(CUDA se musí spoléhat na third-party software a enviroment)
- aplikace v OpenCL mohou běžet jak na CPU, tak i GPU

![[Pasted image 20230322122741.png]]
![[Pasted image 20230322122753.png]]

![[Pasted image 20230322123557.png]]

![[Pasted image 20230322123620.png]]

### Distribuované výpočty

- většinou pro vědecké účely
- stačí PC, GPU a internet
- lze se dobrovolně přihlásit => výpočetní výkon PC je zařazen do celkového poolu projektu => výpočetní práce je rozdělena na několik zařízení (WU - work units)
	- úkoly se rozdělují podle potřeby a podle náročnosti
- **Folding@Home**
	- první projekt pro distribuované výpočty 
	- spuštěn 2006 - Stanfordská univerzita  ve spolupráci s ATI
		- běhěm devíti dní => 31 tera FLOPS výkonu (450 grafik Radeon X1900)
	- výzkum v oblastní bílkovin, léku na Alzheimerou a Parkinsonovu chorobu + některé formy rakoviny

### Machine learning

- analitika obrovského množství dat
	- analytické modely
	- extrémně náročné na výkon => GPU jsou zde mnohem vhodnější než CPU
- alogoritmy pro "umělou inteligenci"
	- obrovské množštví dat a parameterů (GPT 4.0 až 3 trilions of parameters)
	- training and sample data


### Prolamování hesel (generování hashů)

- při vykradení databáze získáme přihlašovací údaje ve formátu hashů
- GPU začne generovat textové řetězce, které s použitím hashovacího algoritmu (SHA-256, nebo Scrypt) převede do hashe => porovná ho s hashy v databázi => pokud se shodují = heslo bylo prolomeno

![[Pasted image 20230322123743.png]]

- hádání hesel (brute-force) => EDPR = Elcomsoft Distributed Password Recovery  

### Blockchain a crypto mining

- blockchainy používají speciální algoritmy (ether měl proměnlivý => grafiky, BTC má jeden a ten samej => ASIC minery)
	- matematické algoritmy pro validaci nových bloků
	- vytvoří se hash => minery se ho snaží uhádnout => generují svoje "tipy" = potřeba velké výpočetní síli