# Jenkins Pipiline Case Study
Zdeněk Brabec  
brabezd1@fel.cvut.cz  
A4M33SEP Softwarové inženýrství pro praxi

## Úvod
Cílem této case study je prozkoumat funkce Jenkins Pipeline. Pro
demonstrování byla vytvořena jednoducha nodejs aplikace. Jenkins
bude muset stáhnut zdrojové soubory, nainstalovat závislosti, 
spustit testy a pak aplikaci nasadit na Heroku.

## Jenkins
Jenkins je open source nástroj pro tzv. _Continous delivery_. Dokáže zautomatizovat
vývojový proces při tvorbě software. Je primárně zaměřený na Javu, ale
lze pomocí pluginů jednoduše ohnout a použít pro téměř všechny vývojové
prostředí (jak je ukázano v tomto projektu). Jenkins běží jako standalone
server, takže všechny úkony provadí ve svém diskovém prostoru - podle
toho, kde jej nasadíte.
