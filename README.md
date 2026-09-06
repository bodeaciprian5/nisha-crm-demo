# NISHA CRM — demo public

Prototip de CRM pentru un atelier de mobilier personalizat. Un singur fișier HTML, fără build,
fără dependențe, fără server.

**Demo live:** https://bodeaciprian5.github.io/nisha-crm-demo/

> Toate datele din demo sunt **fictive** — nume, telefoane, adrese și valori sunt generate
> pentru demonstrație. Nicio informație reală despre clienți sau echipă.

## Ce demonstrează

Fluxul complet al unei comenzi de mobilier la comandă, de la primul telefon până la restanțele
de după montaj — modelat ca **16 etape grupate în 5 faze**, cu responsabil fix pe fiecare.

| Fază | Etape |
|---|---|
| **Intrare** | Preluare client · Selecție & studiu de caz · Înregistrare & avans · Procedură de colaborare |
| **Relevare** | Măsurători · Listă de așteptare |
| **Proiect** | Design · Verificare proiect · Preofertare · Proiectare & redesenare |
| **Angajament** | Ofertă finală & contract · Comandă materiale |
| **Execuție** | De lansat în producție · Producție atelier · Montaj & predare · Restanțe |

Selecția clientului vine **înaintea** înregistrării, iar înregistrarea începe cu factura de avans.
Pipeline-ul se poate filtra pe fază, ca să nu ai 16 coloane deodată.

| Ecran | Ce face |
|---|---|
| **Pipeline** | Kanban pe 16 etape, filtrabil pe fază, drag & drop între coloane, plus vedere tabelară |
| **Clienți** | Segmentare pe tipologie: cu/fără proiect de design, stadiul spațiului |
| **Fișă client** | Panou lateral: date, stare la zi (plată, procedură, stadiu spațiu), parcurs, note vocale, task-uri, ofertare |
| **Task-uri** | Grupate pe responsabil, generate la tranziția de etapă |
| **Restanțe** | Snag list de montaj cu poze |
| **Remindere** | Follow-up automat cu termene și marcarea întârzierilor |
| **Echipă & roluri** | Cine deține ce etapă și ce are în lucru |
| **Reguli proces** | 19 reguli de business, aplicate ca validări în pipeline |

## Reguli implementate ca validări

Pipeline-ul nu e doar un board — încearcă să muți un client mai departe fără plata avansului
înregistrată, sau la măsurători cu șantierul la roșu, și te oprește cu motivul regulii.

- Factura de avans se emite la înregistrare; fără plată, fluxul nu ajunge la măsurători
- Procedura de colaborare trebuie acceptată de client înainte de programarea măsurătorii
- Trei stadii de spațiu: la roșu nu se măsoară, semi-finisat permite măsurătoarea inițială, finisat pe cea finală
- Comanda de materiale cere spațiu finisat, adică măsurătoarea finală făcută
- Prețurile finale sunt vizibile doar pentru anumite roluri — proiectanții nu văd tabul de ofertare
- Bifă GDPR obligatorie la înregistrare; termene depășite marcate vizual

## Ce nu face (e un prototip)

- **Fără persistență** — datele trăiesc în memoria paginii. La refresh revine la setul demo.
  Butonul *Export date* din bara laterală salvează starea curentă ca JSON.
- **Fără login** — schimbi persoana din selectorul „Vezi ca”. Drepturile pe rol vin cu backend-ul.
- **Fără server** — tot ce se vede în interfață există și în sursă.

Notele vocale se înregistrează cu MediaRecorder direct în browser și cer `https://` sau
`localhost` — pe demo-ul de GitHub Pages funcționează.

## Rulare locală

```bash
git clone https://github.com/bodeaciprian5/nisha-crm-demo.git
cd nisha-crm-demo
python3 -m http.server 8000    # apoi http://localhost:8000
```

## Stack

Vanilla HTML, CSS și JavaScript. Zero dependențe în afară de două fonturi Google
(Cormorant Garamond, Jost). ~1.900 de linii într-un singur fișier.
