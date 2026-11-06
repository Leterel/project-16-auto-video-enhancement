# Projekt 16: Auto Video Enhancement

> **Status: Konzeptphase.** Dieses Repository dokumentiert eine geplante Plattform für Erwachsenen-Videos mit automatisierter, möglichst schonender Video- und Audiooptimierung. Es gibt noch keine implementierte Pipeline, Webplattform oder öffentliche Version.

## Idee

Nutzer laden rechtmäßig bereitgestellte Videos hoch. Nach einer technischen Analyse erzeugt die Plattform automatisch eine optimierte Wiedergabeversion. Die **optimierte Version ist die Standardansicht**; das **Original bleibt optional abrufbar**, sofern die Veröffentlichung und Speicherung rechtlich zulässig sind.

Das Ziel ist eine konsistent gute Wiedergabe ohne manuelle Nachbearbeitung durch die Uploader. Technische Korrekturen sollen nach Bedarf erfolgen und das Ausgangsmaterial nicht unnötig verändern.

## Geplante Funktionen

| Funktion | Geplantes Verhalten |
| --- | --- |
| **Auto Analyze** | Auflösung, Bildrate, Codec, Bitrate, Audiopegel und technische Auffälligkeiten prüfen |
| **Auto Compress** | Sinnvolle, qualitätsschonende Videokomprimierung |
| **Auto Normalize** | Audio-Lautheit vereinheitlichen und Übersteuerung vermeiden |
| **Auto Stabilize** | Verwacklungen nur bei erkanntem Bedarf reduzieren |
| **Auto Denoise** | Störendes Bildrauschen bei Bedarf verringern |
| **Auto Enhance** | Helligkeit, Kontrast und Farbdarstellung vorsichtig korrigieren |
| **Auto Transcode** | Geeignete Video- und Audioformate sowie mehrere Streaming-Qualitätsstufen erzeugen |
| **Quality Check** | Resultate auf Abspielfehler, Artefakte und Qualitätsverluste kontrollieren |
| **Original / Optimiert** | Optimierte Wiedergabe standardmäßig, Original als optionale Alternative |

**Nicht Teil des Konzepts:** KI-Upscaling auf künstliche 2K/4K/8K/16K-Auflösungen, erfundene Details und künstliche 30/60/120-FPS-Interpolation. Die Plattform soll echte Qualität erhalten oder verbessern, nicht eine höhere Aufnahmequalität vortäuschen.

## Geplanter Ablauf

1. **Upload und Zulässigkeitsprüfung:** Vor Verarbeitung und Veröffentlichung müssen Berechtigung, Einwilligung, Volljährigkeit der dargestellten Personen und Plattformregeln geprüft werden.
2. **Technische Analyse:** Quelldatei untersuchen und notwendige Verarbeitungsschritte bestimmen.
3. **Bedingte Optimierung:** Nur geeignete Filter anwenden. Bei bereits gutem Ausgangsmaterial unnötige Änderungen vermeiden.
4. **Transcoding:** Für Streaming geeignete Versionen und Qualitätsstufen erstellen.
5. **Qualitätskontrolle:** Technische Fehler und erkennbare Verschlechterungen prüfen; bei Bedarf auf eine weniger stark bearbeitete Version zurückgreifen.
6. **Bereitstellung:** Optimierte Fassung als Standard abspielen, Original nur bei entsprechender Berechtigung optional anbieten.

## Vorläufiger Technologieansatz

Die konkrete Architektur ist **noch nicht entschieden**.

- **FFmpeg / FFprobe:** Analyse, Audioverarbeitung, Filter und Encoding
- **Python:** Mögliche Orchestrierung einer asynchronen Verarbeitungspipeline
- **Web-Frontend und Backend:** Upload, Verarbeitungstatus, Moderation und Player
- **Streaming:** HLS oder DASH als mögliche adaptive Auslieferungsformate
- **Stabilisierung:** Geeignete FFmpeg-Filter, gegebenenfalls vid.stab

Diese Komponenten sind **Vorschläge**, keine bereits eingerichteten Abhängigkeiten. Codec-Auswahl, Hardwarebeschleunigung, Speicherstrategie und Hosting werden später anhand von Tests und Kosten entschieden.

## Qualitätsgrundsätze

- **Quelltreue vor Effektstärke:** Keine unnötigen Eingriffe in Farben, Schärfe, Bewegung oder Ton.
- **Automatik mit Grenzen:** Nicht jede Datei profitiert von Stabilisierung oder Rauschreduzierung.
- **Keine falschen Qualitätsversprechen:** Höhere Auflösung oder Bildrate allein macht ein Video nicht detailreicher.
- **Transparenz:** Original und technisch optimierte Variante klar kennzeichnen.
- **Messbarkeit:** Verarbeitungskosten, Dateigrößen, Fehler und sichtbare Qualität anhand geeigneter Testdateien vergleichen.

## Schutz, Recht und Moderation

Eine Plattform mit Erwachsenen-Inhalten benötigt vor einem öffentlichen Betrieb ein gesondertes Sicherheits- und Rechtskonzept. Unter anderem zu klären und umzusetzen:

- Wirksame Altersverifikation und Zugangskontrolle nach den jeweils geltenden Vorschriften, insbesondere in Deutschland
- Verifizierbare Volljährigkeit und Einwilligung sämtlicher dargestellter Personen sowie Upload-Berechtigungen
- Moderation und Prozesse zum schnellen Melden, Sperren und Entfernen rechtswidriger oder nicht einvernehmlicher Inhalte
- Datenschutz, begrenzte Aufbewahrung, sichere Speicherung, Zugriffsrechte und Löschprozesse
- Schutz vor unerlaubten Reuploads und Missbrauch; nachvollziehbare Freigabe vor Veröffentlichung

**Ein erfolgreich verarbeiteter Upload darf nicht automatisch als rechtlich freigegebener Inhalt gelten.** Auch eine Originalversion darf nur im Rahmen der jeweiligen Berechtigungen zugänglich sein.

## Geplanter MVP

Der erste technische Prototyp soll **lokal mit eigenen oder ausdrücklich zur Verarbeitung freigegebenen Testvideos** funktionieren:

1. Metadaten mit FFprobe erfassen.
2. Audio-Lautheit messen und bei Bedarf normalisieren.
3. Videos mit einem nachvollziehbaren Qualitätsprofil transkodieren.
4. Stabilisierung und Entrauschung selektiv testen.
5. Original und optimierte Ausgabe vergleichen.
6. Qualitäts- und Größenunterschiede protokollieren.

Ein öffentlicher Upload-Dienst oder eine Erwachsenenplattform ist **nicht** Bestandteil dieses ersten MVP.

## Aktueller Projektstand

- [x] Projektidee und Funktionsumfang definiert
- [x] Original sekundär, optimierte Wiedergabe primär festgelegt
- [x] KI-Upscaling und Frame-Interpolation bewusst ausgeschlossen
- [ ] Technisches Architekturdesign
- [ ] Lokale Verarbeitungspipeline
- [ ] Reproduzierbare Qualitätstests
- [ ] Web-Oberfläche und Streamingplayer
- [ ] Rechtliche, organisatorische und technische Freigabe für öffentlichen Betrieb

## Lizenz

Siehe [LICENSE](LICENSE). Die vorhandene Repository-Lizenz bleibt unverändert.

---

**Projekt 16 · Konzeptdokumentation · Stand: November 2026**
