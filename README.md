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
vývojový proces při tvorbě software. Nabízí primárně řešení pro nejpoužívanější
jazyky, ale lze pomocí pluginů jednoduše ohnout a použít pro téměř všechny vývojové
prostředí (jak je ukázano v tomto projektu). Jenkins běží jako standalone
server, takže všechny úkony provadí ve svém diskovém prostoru - podle
toho, kde jej nasadíte. Typické úkony pro _Continous delivery_ jsou build, 
spuštění testů a nasazení. 

Jenkins nabízí grafické rozhraní běžící v prohlížeči, případně _Command line tool_ 
(CLI). Můžete v něm spravovat všehny své projekty.

V tomto projektu bylo využito grafické rozhraní Blue Ocean.

## Pipiline

Pipeline je způsob, jak zadat posloupnost vykonávaných akcí. Definuje se pomocí 
`Jenkinsfile`. To je konfigurační soubor napsaný v Gradle formátu. 

```gradle
node { // <1>
    stage('Build') { // <2>
        /* .. snip .. */
    }
    stage('Test') {
        /* .. snip .. */
    }
    stage('Deploy') {
        /* .. snip .. */
    }
}
```

Tohle je úkázkový příklad takové pipeline. Pomocí `node` alokujete workspace. Jedná
se tedy o omezení scope pro definované proměnné. Následují tři `stage`, tedy
jednotlivé po sobě jdoucí kroky v pipeline. Jenkins nabízí širokou škálu příkazů
(nazývané steps), které lze nalézt v [dokumentaci](https://jenkins.io/doc/pipeline/steps/).

![alt text](img/pipeline_history.png "Pipeline historie")
Základní pohled na pipeline nabízí přehled historie buildů.

Konfigurační soubor lze uchovávat přímo v repozitáři a Jenkins na něj odkázat, nebo
jej vepsat přímo v grafickém rozhraní v nastavení pipeline. 

![alt text](img/settings_general.png "Nastavení pipeline")

V nastavení pipeline jdou dále specifikovat tzv. _Build Triggers_, tedy události, kdy se
má pipeline spouštět. Lze nastavit, že se pipeline bude provádět s nějakou periodicitou,
nebo například Github webhook (Jenkins pozná, že do určité větve v repozitáři byl 
pushnut nový commit).

![alt text](img/settings_triggers.png "Pipeline triggers")