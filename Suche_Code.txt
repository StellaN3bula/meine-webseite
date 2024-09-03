<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <link href="https://fonts.googleapis.com/css2?family=Butterfly+Kids&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&display=swap" rel="stylesheet">

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">

    <title>Suchergebnisse</title>
</head>

<style>
    *{
    /* Hintergrund */
    --weißBlau: #F4F7FF;
        --mittelhellBlau:#a5e0fcc0;

    /*navbar*/
    --schwarz:#000000;

    /* Akzentfarben */
    --grauBlau:#C2D4FF;

    --limeGruen: #32CD32;


    /* Buttons /Links */
    --seeBlau:#7CA4FF;
    --blau:#5D8EFE;

    /* schrift */
    --weiß:#FFFFFF;


    /* Rahmenfarbe / Highlight */
    --highlightBlau: #00b7ff;



    /* font-family: "Butterfly Kids", cursive; */
    font-family: 'Orbitron', sans-serif ; 

}

body{
    background-color: var(--mittelhellBlau);
}
    h1 {
        font-family: "Butterfly Kids", cursive;
        color: var(--highlightBlau);
    }


</style>
<body>
    <h1>Suchergebnisse anzeigen: </h1>
    <h3>Ihr Suchbegriff befindet sich auf der Seite: </h3>

    <ul id="results"></ul>



    <script>
        const seiten = [
            {title: "index", URL: "index.html", keywords: ["über mich", "übungen", "Dokumentation", "Doku"]},
            {title: "lebenslauf", URL: "lebenslauf.html", keywords: ["Kontakt", "E-Mail", "Email", "Fähigkeiten", "Erfahrungen", "Ausbildung", "Zertifikate", 
                            "Sprachkenntnisse", "Software", "Programmiersprachen", "EDV"]},
            {title: "übungen", URL: "Einfache_To_Do_Liste.html"},
            {title: "Dokumentationen", URL: "Doku.html"}
        ];
    
        // Holt den Query-Parameter aus der URL
        const params = new URLSearchParams(window.location.search);
        const query = params.get('query') ? params.get('query').toLowerCase() : '';
    

    
        // Filtert die Seiten
        const results = seiten.filter(seite => 
            seite.title.toLowerCase().includes(query) || 
            (seite.keywords && seite.keywords.some(keyword => keyword.toLowerCase().includes(query)))
        );
    

        // Holt das Ergebnis-Element
        const resultsContainer = document.getElementById('results');
        resultsContainer.innerHTML = ''; // Leert das Ergebnis-Element, falls bereits was drinnen steht
    
        // Ergebnisse anzeigen
        if (results.length > 0) {
            results.forEach(ergebnis => {
                const li = document.createElement('li');
                const link = document.createElement('a');
                link.href = ergebnis.URL;
                link.textContent = ergebnis.title; 
                li.appendChild(link);
                resultsContainer.appendChild(li);
            });
        } else {
            resultsContainer.textContent = 'Keine Ergebnisse gefunden.';
        }
    </script>
    
    
</body>
</html>
