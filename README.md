# NISHA CRM — demo public

Prototip de CRM pentru un atelier de mobilier personalizat. Un singur fișier HTML, fără build,
fără dependențe, fără server.

**Demo live:** https://bodeaciprian5.github.io/nisha-crm-demo/

> Toate datele din demo sunt **fictive** — nume, telefoane, adrese și valori sunt generate
> pentru demonstrație. Nicio informație reală despre clienți sau echipă.

## Ce demonstrează

Fluxul complet al unei comenzi de mobilier la comandă, de la primul telefon până la restanțele
de după montaj — modelat ca 11 etape cu responsabil fix pe fiecare.

| Ecran | Ce face |
|---|---|
| **Pipeline** | Kanban cu 11 etape, drag & drop între coloane, plus vedere tabelară |
| **Clienți** | Segmentare pe tipologie: cu/fără proiect de design, șantier la roșu/spațiu finisat |
| **Fișă client** | Panou lateral: date, parcurs în proces, note vocale, task-uri, ofertare |
| **Task-uri** | Grupate pe responsabil, generate la tranziția de etapă |
| **Restanțe** | Snag list de montaj cu poze |
| **Remindere** | Follow-up automat cu termene și marcarea întârzierilor |
| **Echipă & roluri** | Cine deține ce etapă și ce are în lucru |
| **Reguli proces** | Regulile de business, aplicate ca validări în pipeline |

## Reguli implementate ca validări

Pipeline-ul nu e doar un board — încearcă să muți un client în „Ofertare” fără avans încasat,
sau în „Măsurători” cu șantierul la roșu, și te oprește cu motivul regulii.

- Oferta nu se emite fără avans încasat (prag diferit pentru apartament vs. casă)
- Măsurătoarea cere spațiu finisat — șapă turnată și pereți gletuiți
- Bifă GDPR obligatorie la înregistrarea clientului
- Termene depășite marcate vizual pe fișă și în remindere
- Lucrările la peste 3 luni declanșează alerta de blocare a prețului la materiale

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
(Cormorant Garamond, Jost). ~1.400 de linii într-un singur fișier.
