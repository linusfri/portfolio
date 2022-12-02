---
Title: Load
Template: analysis_single
---
Inledning
=======================

Denna rapport har som syfte att göra en analys av en rad hemsidor. Målet med analysen är att ta reda på hur laddningstider och prestanda på olika webbsidor skiljer sig samt vad som ger upphov till dessa skillnader.

<br>
Urval
-----------------------

Jag valde hemsidorna i kursmoment ett eftersom jag ansåg att alla hade tillräckligt intressant innehåll vilket kunde analyseras på olika sätt och med olika syften.
Alla sidor är så kallade "porfoliosidor" som skiljer sig relativt mycket från varandra stilmässigt. Jag tog inspiration från
<a href="https://collegeinfogeek.com/personal-website-examples/">denna</a> sida.

<br>
Metod
-----------------------

För att mäta hemsidornas hastighet så använde jag mig av Firefox inbyggda utvecklingsverktyg. För att mäta prestandan ur ett användarperspektiv använde jag mig att Google Pagespeed Insights eftersom denna tjänst tar hänsyn till andra aspekter än bara ren hastighet. Den mäter också användarvänligheten på sidan vilket inte är möjligt på samma sätt i Firefox utvecklingsverktyg.

<br>
Resultat
-----------------------
<h3>
    <a class="analysis-title" href="https://docs.google.com/spreadsheets/d/1OxC9N3JenmgdU_8AxLAL6DihzUGQkvHoWW7cvIISGi8/edit#gid=1276179215">
    Länk till analys
    </a>
</h3>
###Bilder
Tryck på bilderna för att förstora
<br><br>
<section class="images">
    <div>
        <h4>Grant Baldwin</h4>
        <img class="analysis-img" src="%assets_url%/img/grant_baldwin.png" alt="">
    </div>
    <div>
        <h4>Roxane gay</h4>
        <img class="analysis-img" src="%assets_url%/img/roxane_gay.png" alt="">
    </div>
    <div>
        <h4>Andrew Huang</h4>
        <img class="analysis-img" src="%assets_url%/img/andrew_huang.png" alt="">
    </div>
</section>
<article class="article-wide">
    <div class="non-resp-iframe-container">
        <iframe
            id="analysis-iframe"
            src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQo4RWvRQW6cGfHFhMGj9PxneBSJwkcWrBzaNXLTSPTa9G3LxD4jCqy6amw1NWLAgv0uyE9XJ1dmlIQ/pubhtml?widget=true&amp;headers=false"
            width="1000px"
            height="500px"
            class="non-resp-iframe"
        >
        </iframe>
    </div>
   
</article>
<article id="grant" class="analysis-article">
    <h3>Grant Baldwin</h3>
    <h4>Förbättringspotential</h4>
    <p>
       Grants webbsida presterar näst sämst i testet sett till prestanda och resursförbrukning.
       Enligt Google Pagespeed Insights finns en tidsbesparing > 5 sekunder att hämta hem bara
       genom att minska storleken på bilder och servera dessa i ett modernare format. Ytterligare
       en sekund skulle kunna sparas in om CSS och JS laddades förskjutet (deferred). Den största
       potentialen finns i hero-bilden högst upp på sidan. Den är över 600KB stor och tar cirka 1.2 sekunder att ladda in.
       Genom att optimera denna skulle hemsidan få ett högre betyg utan större ansträngning från hemsideskaparens. 
    </p>
</article>


<article id="roxane" class="analysis-article">
    <h3>Roxane Gay</h3>
    <h4>Förbättringspotential</h4>
    <p>
        Roxanes hemsida presterar bäst i testet och får höga betyg i Google Pagespeed Insights.
        Webbsidan serverar bilder i WebP-format och på index-sidan laddas ingen bild som är större än 200KB.
        Med detta sagt så finns det fortfarande potential till förbättring, speciellt sett till inladdning av CSS och JS.
        Genom att ta bort CSS-filer som inte används kan sidan laddningstid förbättras med en sekund, och genom att skjuta upp
        inladdning av JS samt CSS kan den minskas med ytterligare en sekund.
    </p>
</article>

<article id="huang" class="analysis-article">
    <h3>Andrew Huang</h3>
    <br>
    <h4>Förbättringspotential</h4>
    <p>
        Andrew Huangs förstasida får ett jämförelsevis (och objektivt) katastrofalt resultat när den analyseras i Google Pagespeed Insights.
        Sidans "Time to interactive" hamnar på 37 sekunder med en "Total blocking time" på 6 sekunder. Överraskande nog är det inte sidans bilder
        som ger mest avtryck i resultatet och den största boven är oanvänd JS. Över 12 sekunder hade kunnat sparas om oanvänd JS togs bort från sidan,
        något som Huang troligtvis borde överväga. Genom att optimera bilder och skjuta upp inladdning av CSS hade ytterligare tid sparats in, men
        i jämförelse med den oanvända JS-koden är denna insignifikant.
    </p>
</article>

Analys
-----------------------
Sammanfattningsvis presterar samtliga sidor bra rent subjektivt, med få indikationer som pekar på att vinster finns att hämta.
När man ser till mätvärdena målas en annan bild upp. Här ser man tydligt att Roxane Gays sida slår de andra med god marginal,
främst på grund av en minimalistisk designval där jämförelsevis få och väloptimerade resurser laddas in.
<br><br>
Grant Baldwin kammar
hem andraplatsen med en hemsida som subjektivt fungerar bra. Grants sida har dock stora vinster att hämta hem genom att optimera
bilder samt minska antalet inladdade CSS- och JS-filer.
<br><br>
Andrew Huangs sida hamnar långt efter de andra i mätresultaten. Överraskande nog är det inte ooptimerade bilder eller oanvänd CSS som är
orsaken bakom detta, utan här ser vi i stället javascript. Över tolv sekunder hade kunnat sparas om oanvänd JS hade tagits bort men sidan
presterar trots detta bra ur ett användarperspektiv.
<br><br>
###Avslutningsvis

Personligen anser jag att en absolut laddningstid om två sekunder är min gräns för en användbar sida. Roxane Gays sida klarar av att leverera detta
enligt Google Pagespeed Insights och klarar därför mitt gränsvärde.

Övrigt
------
Författare: Linus Fri


<script defer>
    const images = document.getElementsByClassName("analysis-img")
    const iframe = document.getElementById("analysis-iframe")
    for (const image of images) {
        image.addEventListener("click", () => {
            if (image.classList.contains("enlarged")) {
                image.classList.remove("enlarged")
                iframe.classList.remove("hide")
            } else {
                image.classList.add("enlarged")
                iframe.classList.add("hide")
            }
        })
    }
</script>