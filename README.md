# E-portfolio & Projektarkiv – Jonas Sedig
**Civilingenjörsstudent inom Informationsteknik | KTH (Årskurs 2)**

Hej! Denna portfölj fungerar som en konkret samling av mina tekniska verk och praktiska prestationer. Mitt fokus ligger på nätverksteknik, maskinnära programmering och systemförståelse. 

### 📧 Kontakt & Länkar
- **E-post:** [jonas.sedig@icloud.com](mailto:jonas.sedig@icloud.com)
- **LinkedIn:** [linkedin.com/in/jonas-sedig](https://www.linkedin.com/in/jonas-sedig)
- **KTH Utbildningsplan:** [Civilingenjör Informationsteknik](https://www.kth.se/student/kurser/program/CINTE/20242/arskurs2)

---

### 🚀 Utvalda Prestationer & Tekniska Verk (Artefakter)

#### 🕹️ Lågnivåprogrammering: Pong-system för FPGA (Kurs: IS1200)
*Ett projekt som visar min förmåga att bygga applikationer i resursbegränsade miljöer direkt mot hårdvaruregister.*

- **Hårdvaruplattform:** DE10-Lite (FPGA) med en MIPS-baserad mjukprocessor.
- **Tekniker:** C, MIPS Assembler, VGA-synkronisering, IO-registerstyrning.
- **Visuellt bevis:** [Se demo-video på dtek-v emulator](https://youtu.be/HHLjiTD5eXM)
- **Källkod:** [gits-15.sys.kth.se/jonsed/Pong-IS1200](https://gits-15.sys.kth.se/jonsed/Pong-IS1200)

##### 🛠️ Arkitektur och Kodstruktur
Kärnan i projektet handlar om att hantera VGA-skärmens tidskritiska synkroniseringssignaler (H-SYNC och V-SYNC) utan färdiga operativsystembibliotek. Nedan visas ett konkret exempel på hur jag strukturerade initieringen av drivrutinen och renderingen av spelplanen i C:

```c
// Exempel på registerprogrammering för rendering av spelplan
void draw_paddle(int x_pos, int y_pos, uint32_t color) {
    volatile uint32_t* vga_mem = (volatile uint32_t*) VGA_BASE_ADDRESS;
    for (int i = 0; i < PADDLE_HEIGHT; i++) {
        for (int j = 0; j < PADDLE_WIDTH; j++) {
            // Beräkna pixeloffset i videominnet och skriv färgdata direkt till hårdvaran
            int offset = (y_pos + i) * SCREEN_WIDTH + (x_pos + j);
            *(vga_mem + offset) = color;
        }
    }
}
```

##### 💡 Analytisk Reflektion
Den största utmaningen var att optimera kollisionshanteringen så att den inte blockerade renderingsloopen, vilket initialt orsakade flimmer på VGA-skärmen. Genom att flytta input-avläsningen till hårdvaru-interrupts (avbrottshantering) istället för kontinuerlig polling lyckades jag frigöra tillräckligt med klockcykler för att uppnå a stabil bilduppdatering.

---

#### 🔌 Fysisk Hårdvara: Laborationsserie i Digital Design (Kurs: IE1204)
*En serie verk som demonstrerar min förmåga att gå från teoretisk logik till fysisk konstruktion och systematisk hårdvarufelsökning.*

- **Koncept:** CMOS-teknik, Karnaughdiagram (K-maps), sanningstabeller, multiplexers och sekvenskretsar.
- **Konkret Verk:** [Laborationsredovisningar (YouTube-spellista)](https://www.youtube.com/playlist?list=PLeNJYwtfAsrL5AWMiNV-1yNhxKpj67W1A)

##### 📐 Konstruktionsmetodik (Problem till Lösning)
Varje laboration byggde på att minimera boolesk algebra för att minimera antalet fysiska grindar. Nedan visas principskissen för den logiska designen för en 4-till-1 multiplexer som användes för att styra signalflödena på breadboardet:

```text
Teoretisk minimering via K-map:
Y = (A • B • S1) + (C • D • S2) ... 

Fysisk implementation på breadboard:
[Input signaler] ---> [AND-grindar (74LS08)] ---> [OR-grind (74LS32)] ---> [Utgång LED]
```

##### 💡 Analytisk Reflektion
Arbetet med fysiska IC-kretsar på breadboards gav mig en djup förståelse för signalintegritet och kontaktproblem. Att felsöka en krets där en glappkontakt eller en felaktig CMOS-nivå sänker hela logikflödet kräver ett extremt metodiskt tillvägagångssätt. Denna erfarenhet har gett mig en stabil grund för att förstå hårdvarans livscykelhantering och fysisk IT-infrastruktur.

---

### 🏆 Övriga Tekniska Färdigheter
- **Programmering & Verktyg:** Java, Python, C, MIPS Assembler, Git, Linux/Unix-miljöer, Wireshark, MATLAB.
- **Nätverkskompetens:** Djupgående förståelse för OSI-modellen, TCP/IP-stacken, routing samt brandväggskonfiguration.
- **Utmärkelser:** Mottagare av *Joachim Westerlunds Stipendium* för framstående studieresultat inom fysik och naturvetenskap.
