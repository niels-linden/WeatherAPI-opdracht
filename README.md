# WeatherApp

## Methodes die gebruikt worden

- HTML/CSS/JS
- API
- JSON
- Template literals
- Functions
- Fetch
- Async functions

### Stap 1. (Layout en Styling)

- Style je pagina ongeveer zoals op afbeelding 1.
- Gebruik vaste waardes voor nu. (We gaan later een API gebruiken om het huidige weer op te halen.)
- Icons kun je vinden in de map /icons (Voor de windrichting gebruik ik https://icon-sets.iconify.design/wi/wind-direction/)
- Link je Javascript

### Stap 2. (API_KEY)

- Maak een account op https://openweathermap.org/api
- Ga naar je account en maak een API key aan
- Open http://api.openweathermap.org/data/2.5/weather?lat=51.583830&lon=4.767410&units=metric&lang=nl&appid={API_KEY} (Verander {API_KEY} naar je eigen API Key die je net hebt aangemaakt.) Krijg je een JSON response met coord, weather, main, wind, clouds en sys? Dan is het gelukt!
- Sla je API_KEY op in een variable

### Stap 3. (Latitude en Longitude van je locatie ophalen)

- We willen nu de Latitude en Longitude van je huidige locatie opvragen.
- https://www.w3schools.com/js/js_api_geolocation.asp
- Maak een functie getLocation (Ga voor een voorbeeld naar de link hierboven)
- Maak ook een functie setPosition, console.log de latitude en longitude

### Stap 4. (Fetching API)

- We gaan nu de API aanroepen met onze latitude en longitude
- https://javascript.info/fetch
- Maak een async functie getWeather met de parameters latitude en longitude, zorg dat je een variable hebt met de URL van de API.
- Verander de URL zodat je eigen latitude en longitude waardes doorgegeven worden. (Tip: Gebruik template literals)
- fetch de API door de URL door te geven in de functie fetch, sla het resultaat op in een variable response (Ga voor een voorbeeld naar de link hierboven)
- Zet de data om naar JSON
- Console.log de data om te checken of je de juiste data hebt teruggekregen
- Zorg er ook voor dat je de functie getWeather aanroept in setPosition (In deze functie heb je toegang tot de latitude en longitude)

### Stap 5. (Data object maken)

- Maak een leeg object weather aan (Hier gaan we onze data in opslaan)
- In de functie getWeather kunnen we nu de data aan het object aan toevoegen, om de temperatuur in het weather object te krijgen doen we bijvoorbeeld: `weather.temperature = Math.floor(json.main.temp);`
- voeg de volgende eigenschappen toe aan het object

  - omschrijving
  - icon
  - stad
  - land
  - zonsopgang (tijd wordt weergegeven als UNIX Timestamp)
  - zonsondergang (tijd wordt weergegeven als UNIX Timestamp)
  - windkracht (Windkracht is in m/sec, we gebruiken de windschaal van Beaufort voor de app, zie: https://cdn.weerplaza.nl/weerinhetnieuws/articles/article_2733_b78407e4-4c9_image_large.png)
  - windrichting (Windrichting is in graden, zie tabel: https://www.researchgate.net/profile/Marcelo-Biudes/publication/315176876/figure/tbl1/AS:667625818447873@1536185807259/Wind-directions-symbology-and-direction-in-degrees.png)

### Stap 6. (Data in HTML tonen)

- Maak een functie displayWeather
- Haal alle elementen die je wilt invullen op
- De weer icons hebben al de goede naam (bijvoorbeeld 02d.png)
- Het goede windrichting icoontje kunnen we tonen door bijvoorbeeld `data-icon="wi:wind-direction-${variable_windrichting}` te doen
