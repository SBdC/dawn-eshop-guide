# dawn-eshop-guide

## 👫 Aufgabe 1

### Ansatz
- **Neue Section entwickelt:**  
  Es wurde eine eigene Theme-Section (`gender-filter.liquid`) erstellt, die Nutzer:innen eine Auswahl ermöglicht, mit welchem Geschlecht sie sich identifizieren („man“, „woman“, "any").
- **Lokale Speicherung & JavaScript:**  
  Die Auswahl wird im lokalen Browser-Speicher (localStorage) gesichert. Mit JavaScript wird je nach Auswahl das jeweils passende Produktbild auf den Produktkarten angezeigt.
- **Datenlogik für Bilder:**  
  Im Produktkarten-Template (`card-product`) erhalten Produktbilder automatisch ein `data-gender`-Attribut basierend auf dem Bild-ALT-Text (z.B. enthält “woman” → `data-gender="woman"`).
- **Integration in Kollektionsseiten:**  
  Die Section kann leicht der Collection-Seitenschablone hinzugefügt werden

### Vorteile
- Verbessertes Einkaufserlebnis - Nutzer:innen können gezielt Produkte/Outfits entsprechend ihrer Gender-Präferenz auswählen und sehen direkt für sie relevante Produktbilder.
- Funktioniert mit beliebigen Produktbildern; Zuweisung erfolgt automatisch über ALT-Texte.
- Kein externer Service nötig, die gesamte Logik läuft clientseitig (JavaScript, localStorage); keine Abhängigkeit von externen Lösungen oder Apps.
- Einfache Integration, der Filter kann an beliebiger Stelle (z.B. auf Collection-Seiten) eingebunden werden.

### To Do / Verbesserungen

- Um Konflikte mit dem Image-Hover zu vermeiden, wurde der Standard-Hover-Effekt entfernt. Optional könnte eine Lösung erarbeitet werden, die sowohl die Hover- als auch die Gender-Logik kombiniert. 
- Filterstatus mit der URL synchronisieren, um Filteransichten teilen oder verlinken zu können.
- Responsives Design: Style und Layout des Gender-Filters weiter an das Responsive Design und das Store-Designsystem anpassen.
- Weitere Accessibility-Optimierungen (z.B. ARIA-Labels, bessere Tastatur-Bedienbarkeit) und Tests für alle Browser.


## 🏂👕 Aufgabe 2

### Ansatz
- **Erstellung einer JSON-Seitenvorlage** (`page.styling.json`), die zwei benutzerdefinierte Theme-Abschnitte kombiniert:
    - **Hero/Intro:**  
      Benutzerdefinierter Abschnitt (`styling-hero.liquid`), der den Outfit-Titel, Untertitel und ein Hero-Bild anzeigt.
    - **Featured Products:**  
      Benutzerdefinierter Abschnitt (`outfit-set.liquid`), der eine Produktliste (das Outfit/Set) mithilfe eines Metafields (`custom.outfit_products`) rendert.
        - Die Produkte werden seitenweise über dieses Metafeld zugewiesen.
        - „Alle zum Warenkorb hinzufügen“ verwendet die `/cart/add.js` API von Shopify, um alle Artikel in einem Rutsch in den Warenkorb zu legen.

### Vorteile
- Es können beliebig viele Styling-/Outfit-Seiten erstellt werden, jeweils mit eigenen Produkten, Titeln und Styling-Tipps.
- Die Produktzuweisung erfolgt komplett datenbasiert über Metafelder – kein Liquid-Code muss angepasst werden.
- Design und Layout werden über Theme-Abschnitte und Einstellungen gesteuert.
- Alle ausgewählten Produkte werden per AJAX mit nur einem Klick in den Warenkorb gelegt.
- Optionale Abwahl (Checkboxen) sowie Mengen- und Varianten-Auswahl für mehr Flexibilität.
- Produktinformationen (Bestand, Preis, Bild, Varianten) sind immer aktuell, da sie live anhand der Metafeld-Referenz geladen werden.
- Es werden ausschließlich von Shopify unterstützte Schnittstellen verwendet (offizielle AJAX Cart-API), keine Drittanbieter-Abhängigkeiten.

### To Do / Verbesserungen
- Anpassung des Designs an das Store-Designsystem.
- Verbesserung der responsiven Darstellung.
- Verbesserung der Zustandsanzeige/Feedback für den „In den Warenkorb“-Button.
- Erweiterung der Metafelder für z.B. Video, zusätzliche Styling-Hinweise, Designer-Zitate oder Cross-Sells.
- Bugfix: Die Warenkorb-Icon/Anzahl aktualisiert sich nicht sofort nach dem Hinzufügen von Produkten.