

Závěrečná studijní práce
dokumentace
Mayan EDMS




Obor: 

Třída:
Školní rok:
Poděkování
Chtěl bych poděkovat všem učitelům, kteří mi pomáhali při vývoji projektu, zvláště pak panu učiteli Ing. Petru Grussmanovi za trpělivost a konzultaci ohledně použitých technologií.
Prohlašuji, že jsem závěrečnou práci vypracoval samostatně a uvedl veškeré použité 
informační zdroje.
Souhlasím, aby tato studijní práce byla použita k výukovým účelům na Střední průmyslové 
a umělecké škole v Opavě, Praskova 399/8.
V Opavě 	31. 12. 2017
podpis autora práce
ANOTACE
Cílem projektu byla digitalizace papírových dokumentů a propojení a zprovoznění Mayan EDMS s Autoscannerem. Dále bylo cílem vytvoření API aplikace pro propojení Mayan EDMS s Autoscannerem.
Klíčová slova: webová aplikace, API, dokumenty, Autoscanner








OBSAH
Úvod	5
1	Teoretická a metodická východiska	6
		6
2	Využité technologie	7
		7
		7
		7
		7
3	Způsoby řešení a použité postupy	8
		8
		8
		10   
4		12
Závěr	13
Seznam použitýCH INFORMAČNÍCH ZDROJů	14
Seznam příloh	15
Úvod
Ve firmách kolují různé druhy dokumentů, faktur a jiných papírů. Tyto papíry zaberou spoustu místa a zabere hodně času najít požadovaný dokument uprostřed složky. Tenhle problém jsem využil při výběru mého projektu.
	Mým prvním cílem byla instalace DMS systému. Pan Ing. Petr Grussman mi poradil s výběrem Mayan EDMS. Pro instalaci Mayanu EDMS se doporučuje užití Docker Image. Po instalaci jsem přistoupil k řešení API clientu, který má po naskenování dokumentu automaticky daný dokument poslat na server.
První část mé dokumentace se zaměřuje na principy, technologie a postupy, které jsem využil během řešení svého projektu. Zmiňuji se kromě jiného o možnostech digitálního zpracování dokumentu a systémech pro správu dokumentů. V druhé části své práce se snažím přiblížit strukturu aplikace. Dále podrobněji popisuji fungovaní API. 
Teoretická a metodická východiska
Digitalizace dokumentů je jedním z trendů, související s proměnou klasických knihoven (s klasickými dokumenty) v knihovny hybridní a elektronické (s dokumenty v elektronické podobě). V dnešní době vzniká obrovské množství dokumentů již pouze v elektronické podobě. Knihovny a další organizace se však musí vypořádat s převodem tradičních dokumentů do elektronické podoby - proces digitalizace. 
S tématem digitalizace souvisí:

automatické rozpoznávání typu dokumentu,
CR/OMR rozpoznávání obsahu dokumentů a formulářů, 
automatické získávání indexů, klíčových informací o dokumentu,
integrace s informačními systémy a export vytěžených dat do databází,
uchovávání různých verzí dokumentů a sledování jejich historie,
atd. 
Systémy pro správu dokumentů
Systém pro správu dokumentů (Document management system (DMS) nebo Electronic Document management (EDM)), je určený ke správě elektronických dokumentů a zdigitalizovaných papírových dokumentů.


Využité technologie
Python	
Python je vysokoúrovňový skriptovací programovací jazyk. Nabízí dynamickou kontrolu datových typů a podporuje různá programovací paradigmata, včetně objektově orientovaného, imperativního, procedurálního nebo funkcionálního. Python je vyvíjen jako open source projekt, který zdarma nabízí instalační balíky pro většinu běžných platforem (Unix, MS Windows, macOS).
Mayan EDMS
Mayan EDMS je Open source systém správy elektronických dokumentů, který je naprogramován v jazyce Python pomocí webové aplikací Django a je vydán pod licencí Apache 2.0. Poskytuje úložiště pro elektronické dokumenty.
Pycharm
PyCharm je integrované vývojové prostředí (IDE) používané v programování, specificky pro jazyk Python. Vývoj probíhá pod českou společností JetBrains. Poskytuje analýzu kódu, graficky debugger, integrovanou testovací jednotku a podporuje vývoj webových aplikací pomocí Django.
Docker
Docker je open source projekt, jehož cílem je poskytnout jednotné rozhraní pro izolaci aplikací do kontejnerů v prostředí Linuxu i Windows („odlehčená virtualizace“).
Způsoby řešení a použité postupy
Použití Mayan EDMS
Nejjednodušší způsob, jak používat Mayan EDMS, je pomocí oficiálního image Docker. Pro instalaci Dockeru stačí stáhnout instalační program s příponou .exe. 			 	  Pro mé účely mi Mayan EDMS zpřístupnil na adrese http://www.sspu-opava.cz:82/ pan Grussman.
	
Seznámení se s Mayan EDMS
Pro nahrání nového dokumentu stačí kliknout na „new document“.

Po kliknutí proběhne přesměrování na novou stránku, kde vybereme, o jaký typ dokumentu se jedná. Typy dokumentu můžeme přidávat a spravovat. 



Jakmile si vybereme typ dokumentu, Mayan EDMS nás přesměruje na stránku metadat, které jsou k příslušnému dokumentu připojeny.

Pak už jen stačí vybrat dokument, který chceme nahrát.
API
API (zkratka pro Application Programming Interface) označuje v informatice rozhraní pro programování aplikací. API určuje, jakým způsobem jsou funkce knihovny volány ze zdrojového kódu programu. Při použití v kontextu vývoje webu je API typicky definováno HTTP a požaduje zprávy spolu s definicí struktury odpovědí obvykle v XML nebo JSON formátu. REST má samozřejmě svá specifika a standardy, které je ale vhodné dodržovat. Leonard Richardson je rozdělil do 4 úrovní. 









Nultá úroveň
Jedná se o samotný přenos dat. 
První úroveň - zdroje (Resources)
Místo toho, aby se všechny požadavky posílaly na jeden centrální bod, použije se jich více. Každý zdroj má pak právě jeden koncový bod, kde ho lze dosáhnout. Např. GET /pisen- vrátí seznam písní, GET /pisen/zanry vrátí žánr k dané písničky apod.
Druhá úroveň - HTTP Verbs
V protokolu HTTP je asi nejznámější metoda GET. Byla by ale chyba omezovat se při návrhu API jen na ni. Protokol HTTP jich totiž nabízí mnohem více. Jsou to: PUT, PATCH, DELETE, OPTIONS a další. Akci, kterou chceme provést, vyjádříme právě pomocí HTTP Verbs.
Významy jednotlivých HTTP Verbs jsou následující:
GET - získání dat
POST - vytvoření
PUT - úpravy 
DELETE - smazání
Třetí úroveň – Hypermedia Controls
Poslední třetí úroveň je známá pod akronymem HATEOAS (Hypertext as the Engine of Application State). Známe pouze základní koncový bod, který vrací spolu s daty také odkazy na další zdroje, ty zase na další a tak dále. Každý zdroj tak klientovi dává možnosti, jakou akci může provést nebo co dál udělat. 






Výsledky řešení, výstupy, uživatelský manuál






Závěr
Cílem tohoto projektu bylo vytvoření funkční API aplikace, která propojí Mayan EDMS a Autoscanner. Určené cíle, jako vytvoření  API aplikace a instalace Mayan EDMS, byly splněny. 
Do budoucna by bylo možné vytvořit univerzální API, kde se akorát zadá cílová adresa a API client se o nahrání obrázku postará. Tuto API aplikaci jsem vytvořil pro osobní účely. 




Seznam použitýCH INFORMAČNÍCH ZDROJů
[1]		Docker [online]. 2017 [cit. 2017-12-28]. 
		<https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/#install-docker-ce>
[2]		Mayan EDMS [online].2017 [cit. 2017-12-28].
		<http://docs.mayan-edms.com/en/latest/>
		<https://hub.docker.com/r/mayanedms/mayanedms/>
[3]		API [online].2017 [cit. 2017-12-28] .
		<https://pypi.python.org/pypi/mayan-api_client>	
		<https://www.w3schools.com/tags/ref_httpmethods.asp>
[4]		Python [online].2017 [cit. 2017-12-28]
		<https://docs.python.org/3/>
		<http://diveintopython3.py.cz/native-datatypes.html>
		<http://programujte.com/clanek/2005082802-python-8-lekce/>
		<http://programujte.com/forum/vlakno/8040-vice-rozmerne-pole-seznam-v-pythonu/>
[5]		WTForms[online].2017 [cit. 2017-12-28]
		<https://wtforms.readthedocs.io/en/latest/>
