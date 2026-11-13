# Python Weather Dashboard -- Teil 1

Ein kleines Python-Konsolenprojekt, das für einen frei eingegebenen Ort
aktuelle Wetterdaten abruft und übersichtlich ausgibt.

Die Anleitung orientiert sich thematisch an **„Build a Python Weather
Dashboard, Step by Step --- Part 1"** von Nishitha Kalathil. Sie ist
eine eigenständige, deutschsprachige Umsetzung mit neu strukturiertem
Beispielcode.

**Originalartikel:**\
https://medium.com/@nishithakalathil/build-a-python-weather-dashboard-step-by-step-part-1-c3fbfb6d766c

## Lernziele

Nach diesem Projekt kannst du:

-   eine HTTP-API mit Python aufrufen,
-   JSON-Daten auswerten,
-   Ortsnamen in geografische Koordinaten umwandeln,
-   Funktionen und Rückgabewerte verwenden,
-   Benutzereingaben verarbeiten,
-   einfache Fehlerbehandlung implementieren.

## Verwendete Technologien

-   Python 3.10 oder neuer
-   [Open-Meteo Geocoding
    API](https://open-meteo.com/en/docs/geocoding-api)
-   [Open-Meteo Forecast API](https://open-meteo.com/en/docs)
-   Python-Paket `requests`

Open-Meteo kann für diesen Einstieg ohne API-Key verwendet werden. Bitte
beachte die Nutzungsbedingungen und die jeweils geltenden Limits des
Dienstes.

## 1. Projekt einrichten

Erstelle ein Projektverzeichnis:

``` bash
mkdir python-weather-dashboard
cd python-weather-dashboard
```

Erzeuge und aktiviere eine virtuelle Umgebung.

### Linux / macOS

``` bash
python3 -m venv .venv
source .venv/bin/activate
```

### Windows (PowerShell)

``` powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```

Installiere die benötigte Bibliothek:

``` bash
python -m pip install requests
```

Lege die Abhängigkeiten fest:

``` bash
python -m pip freeze > requirements.txt
```

## 2. Projektstruktur

Am Ende dieses ersten Teils besteht das Projekt aus:

``` text
python-weather-dashboard/
├── .venv/
├── weather.py
├── requirements.txt
└── README.md
```

## 3. Wetterdaten für einen festen Ort abrufen

Die Forecast API benötigt geografische Koordinaten. Als erster Test
können Koordinaten fest im Programm hinterlegt werden.

Erstelle `weather.py`:

``` python
import requests

API_URL = "https://api.open-meteo.com/v1/forecast"

latitude = 48.2082
longitude = 16.3738

params = {
    "latitude": latitude,
    "longitude": longitude,
    "current": "temperature_2m"
}

response = requests.get(API_URL, params=params, timeout=10)
response.raise_for_status()

weather_data = response.json()
temperature = weather_data["current"]["temperature_2m"]

print(f"Aktuelle Temperatur: {temperature} °C")
```

Starte das Programm:

``` bash
python weather.py
```

Die Ausgabe enthält die aktuelle Temperatur für die angegebenen
Koordinaten. Der konkrete Wert hängt vom Zeitpunkt des Abrufs ab.

### Was passiert hier?

1.  `requests.get()` sendet eine HTTP-Anfrage.
2.  Die API liefert eine JSON-Antwort.
3.  `response.json()` wandelt die Antwort in Python-Datenstrukturen um.
4.  Über `weather_data["current"]` werden die aktuellen Messwerte
    gelesen.
5.  `raise_for_status()` meldet HTTP-Fehler, statt eine Fehlerantwort
    unbemerkt weiterzuverarbeiten.

## 4. Mehr Wetterwerte abrufen

Die API kann mehrere aktuelle Werte in einer Anfrage liefern. Ergänze
die Parameter um Luftfeuchtigkeit, Windgeschwindigkeit und Wettercode:

``` python
params = {
    "latitude": latitude,
    "longitude": longitude,
    "current": (
        "temperature_2m,"
        "relative_humidity_2m,"
        "wind_speed_10m,"
        "weather_code"
    )
}
```

Die Werte stehen anschließend im Objekt `weather_data["current"]` zur
Verfügung.

## 5. Ortsnamen in Koordinaten umwandeln

Damit Benutzer nicht selbst Breitengrad und Längengrad suchen müssen,
verwenden wir die Geocoding API.

``` python
import requests

GEOCODING_URL = "https://geocoding-api.open-meteo.com/v1/search"


def find_location(city: str):
    """Sucht einen Ort und liefert Name, Breiten- und Längengrad."""
    params = {
        "name": city,
        "count": 1,
        "language": "de",
        "format": "json"
    }

    response = requests.get(
        GEOCODING_URL,
        params=params,
        timeout=10
    )
    response.raise_for_status()

    results = response.json().get("results", [])

    if not results:
        return None

    place = results[0]

    return {
        "name": place["name"],
        "country": place.get("country", ""),
        "latitude": place["latitude"],
        "longitude": place["longitude"]
    }
```

Die Funktion liefert entweder ein Dictionary mit Ortsdaten oder `None`,
wenn kein passender Ort gefunden wurde.

## 6. Wetterdaten über eine Funktion abrufen

``` python
FORECAST_URL = "https://api.open-meteo.com/v1/forecast"


def get_current_weather(latitude: float, longitude: float):
    """Ruft aktuelle Wetterwerte für Koordinaten ab."""
    params = {
        "latitude": latitude,
        "longitude": longitude,
        "current": (
            "temperature_2m,"
            "relative_humidity_2m,"
            "wind_speed_10m,"
            "weather_code"
        )
    }

    response = requests.get(
        FORECAST_URL,
        params=params,
        timeout=10
    )
    response.raise_for_status()

    return response.json()["current"]
```

## 7. Wettercodes lesbar darstellen

Die API liefert für den Zustand des Wetters einen numerischen
WMO-Wettercode. Eine kleine Hilfsfunktion übersetzt ausgewählte Codes in
verständliche Beschreibungen.

``` python
def describe_weather(code: int) -> str:
    """Übersetzt wichtige WMO-Wettercodes in deutsche Texte."""
    descriptions = {
        0: "Klarer Himmel",
        1: "Überwiegend klar",
        2: "Teilweise bewölkt",
        3: "Bedeckt",
        45: "Nebel",
        48: "Nebel mit Reifbildung",
        51: "Leichter Nieselregen",
        53: "Mäßiger Nieselregen",
        55: "Starker Nieselregen",
        61: "Leichter Regen",
        63: "Mäßiger Regen",
        65: "Starker Regen",
        71: "Leichter Schneefall",
        73: "Mäßiger Schneefall",
        75: "Starker Schneefall",
        95: "Gewitter"
    }

    return descriptions.get(code, "Unbekannte Wetterlage")
```

Die Liste ist bewusst kompakt. Für eine vollständige Abdeckung sollten
alle Codes der
[Open-Meteo-Dokumentation](https://open-meteo.com/en/docs)
berücksichtigt werden.

## 8. Vollständiges Programm

Ersetze den Inhalt von `weather.py` durch die folgende zusammengeführte
Version:

``` python
import requests

GEOCODING_URL = "https://geocoding-api.open-meteo.com/v1/search"
FORECAST_URL = "https://api.open-meteo.com/v1/forecast"


def find_location(city: str):
    """Ermittelt die Koordinaten eines Ortsnamens."""
    params = {
        "name": city,
        "count": 1,
        "language": "de",
        "format": "json"
    }

    response = requests.get(
        GEOCODING_URL,
        params=params,
        timeout=10
    )
    response.raise_for_status()

    results = response.json().get("results", [])
    if not results:
        return None

    place = results[0]

    return {
        "name": place["name"],
        "country": place.get("country", ""),
        "latitude": place["latitude"],
        "longitude": place["longitude"]
    }


def get_current_weather(latitude: float, longitude: float):
    """Lädt aktuelle Wetterdaten für einen Standort."""
    params = {
        "latitude": latitude,
        "longitude": longitude,
        "current": (
            "temperature_2m,"
            "relative_humidity_2m,"
            "wind_speed_10m,"
            "weather_code"
        )
    }

    response = requests.get(
        FORECAST_URL,
        params=params,
        timeout=10
    )
    response.raise_for_status()

    return response.json()["current"]


def describe_weather(code: int) -> str:
    """Liefert eine kurze Beschreibung zum Wettercode."""
    descriptions = {
        0: "Klarer Himmel",
        1: "Überwiegend klar",
        2: "Teilweise bewölkt",
        3: "Bedeckt",
        45: "Nebel",
        48: "Nebel mit Reifbildung",
        51: "Leichter Nieselregen",
        53: "Mäßiger Nieselregen",
        55: "Starker Nieselregen",
        61: "Leichter Regen",
        63: "Mäßiger Regen",
        65: "Starker Regen",
        71: "Leichter Schneefall",
        73: "Mäßiger Schneefall",
        75: "Starker Schneefall",
        95: "Gewitter"
    }

    return descriptions.get(code, "Unbekannte Wetterlage")


def main():
    city = input("Bitte Stadt eingeben: ").strip()

    if not city:
        print("Es wurde kein Ort eingegeben.")
        return

    try:
        location = find_location(city)

        if location is None:
            print(f"Der Ort '{city}' wurde nicht gefunden.")
            return

        weather = get_current_weather(
            location["latitude"],
            location["longitude"]
        )

        print("\n" + "=" * 38)
        print("             WETTER DASHBOARD")
        print("=" * 38)
        print(f"Ort           : {location['name']}")
        print(f"Land          : {location['country']}")
        print(f"Temperatur    : {weather['temperature_2m']} °C")
        print(f"Luftfeuchte   : {weather['relative_humidity_2m']} %")
        print(f"Windgeschw.   : {weather['wind_speed_10m']} km/h")
        print(
            "Wetter        : "
            f"{describe_weather(weather['weather_code'])}"
        )
        print("=" * 38)

    except requests.exceptions.Timeout:
        print("Zeitüberschreitung: Der Wetterdienst antwortet nicht rechtzeitig.")
    except requests.exceptions.RequestException as error:
        print(f"Fehler bei der HTTP-Anfrage: {error}")
    except (KeyError, ValueError) as error:
        print(f"Unerwartete Antwort des Wetterdienstes: {error}")


if __name__ == "__main__":
    main()
```

Starte das Programm:

``` bash
python weather.py
```

Beispiel für die Ausgabe (Wetterwerte sind beispielhaft):

``` text
Bitte Stadt eingeben: Wien

======================================
             WETTER DASHBOARD
======================================
Ort           : Wien
Land          : Österreich
Temperatur    : 18.4 °C
Luftfeuchte   : 62 %
Windgeschw.   : 11.2 km/h
Wetter        : Teilweise bewölkt
======================================
```

## 9. Lern- und Übungsaufgaben

1.  Ändere das Programm so, dass statt Wien ein beliebiger Ort abgefragt
    wird.
2.  Ergänze die Anzeige um die Windrichtung.
3.  Was passiert, wenn ein nicht existierender Ort eingegeben wird?
4.  Warum verwenden wir für `requests.get()` den Parameter `timeout=10`?
5.  Erkläre den Unterschied zwischen einer Funktion, die `None`
    zurückgibt, und einer Funktion, die ein Dictionary zurückgibt.
6.  Ergänze weitere WMO-Wettercodes.
7.  Ändere die Ausgabe so, dass die Messwerte mit zwei Nachkommastellen
    angezeigt werden.

## 10. Mögliche Erweiterungen in den nächsten Projektteilen

-   Celsius/Fahrenheit auswählen
-   wiederholte Ortssuchen in einer Schleife
-   Fehlerbehandlung weiter ausbauen
-   Quellcode in mehrere Python-Module aufteilen
-   eine 7-Tage-Vorhersage anzeigen
-   Temperaturverlauf mit Matplotlib visualisieren
-   grafische Benutzeroberfläche mit Tkinter erstellen

## Quellen und weiterführende Dokumentation

-   Originalartikel: [Build a Python Weather Dashboard, Step by Step ---
    Part
    1](https://medium.com/@nishithakalathil/build-a-python-weather-dashboard-step-by-step-part-1-c3fbfb6d766c)
-   Open-Meteo: [Forecast API](https://open-meteo.com/en/docs)
-   Open-Meteo: [Geocoding
    API](https://open-meteo.com/en/docs/geocoding-api)
-   Python Requests:
    [Quickstart](https://requests.readthedocs.io/en/latest/user/quickstart/)

------------------------------------------------------------------------

**Lizenzhinweis:** Dies ist eine eigenständige Lernunterlage, die sich
thematisch am oben verlinkten Artikel orientiert. Für den
Originalartikel gelten die Rechte der Autorin. Open-Meteo und die
verwendeten Python-Bibliotheken unterliegen ihren jeweiligen
Nutzungsbedingungen und Lizenzen.
