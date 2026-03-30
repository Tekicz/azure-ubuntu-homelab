# ☁️ Azure Cloud Home Lab: Web & Voice Services Infrastructure
**Live Demo / Dostęp do usług:**
* 🌐 **Web Server (Nginx):** `https://20.199.104.24`
* 📁 **Filebrowser:** `http://20.199.104.24:8080`
* 🎙️ **TeamSpeak 3:** `20.199.104.24` (Port 9987)

> **Uwaga:** Serwer może być okresowo wyłączany w celu optymalizacji kosztów w chmurze Azure. Poniżej znajdują się zrzuty ekranu udowadniające działanie infrastruktury.

## 📝 O projekcie
Projekt stanowi moje domowe laboratorium chmurowe (Proof of Concept). Został stworzony w celu praktycznego zastosowania wiedzy z zakresu sieci komputerowych, administracji systemem Linux oraz wdrażania usług w modelu IaaS w chmurze Microsoft Azure. 

Głównym celem było powołanie wirtualnej infrastruktury, zabezpieczenie jej za pomocą chmurowych i systemowych zapór sieciowych  oraz utrzymanie stabilnego działania usług webowych i komunikacji w czasie rzeczywistym.

## 🛠 Wykorzystane technologie
* **Chmura publiczna:** Microsoft Azure (Virtual Machines, Network Security Groups, Public IP)
* **System operacyjny:** Ubuntu Server (Linux CLI)
* **Usługi:** TeamSpeak 3 Server, Nginx (Web Server), Filebrowser
* **Sieci:** TCP/IP, DNS, reguły NAT / Firewall (UFW)

## 🏗 Architektura i Konfiguracja Sieci
Aplikacje działają na pojedynczej maszynie wirtualnej w środowisku Azure. Dostęp do usług jest ściśle kontrolowany na dwóch warstwach bezpieczeństwa: zewnętrznej (Azure NSG) oraz wewnętrznej (Linux UFW).

| Usługa / Zastosowanie | Protokół | Port | Opis |
| :--- | :--- | :--- | :--- |
| **SSH** | TCP | `22` | Bezpieczne zarządzanie serwerem  |
| **Nginx Web Server** | TCP | `80` / `443` | Dostęp do głównej strony internetowej. |
| **Filebrowser** | TCP | `8080` | Webowy interfejs do zarządzania plikami na serwerze. |
| **TeamSpeak 3 (Voice)** | UDP | `9987` | Przesyłanie strumienia głosu w czasie rzeczywistym. |
| **TeamSpeak 3 (Files)** | TCP | `30033` | Transfer plików wewnątrz komunikatora. |
| **TeamSpeak 3 (Query)**| TCP | `10011` | Zdalne zarządzanie instancją serwera głosowego. |
<img width="1473" height="658" alt="obraz" src="https://github.com/user-attachments/assets/8200084b-8e26-4f02-81d0-0e06418e0b9b" />


## ⚙️ Kluczowe etapy wdrożenia
1. **Provisioning maszyny:** Utworzenie instancji Ubuntu Server w wybranym regionie Azure.
2. **Hardening i OS Config:** Aktualizacja pakietów dystrybucji, wstępna konfiguracja uprawnień użytkowników.
3. **Instalacja usług:** Pobranie i uruchomienie binariów serwera TeamSpeak 3 oraz konfiguracja usługi Filebrowser.
4. **Zarządzanie Zaporą (Podwójna warstwa):**
   * Utworzenie i przypisanie polityk w **Azure Network Security Group (NSG)** w celu wpuszczenia ruchu z zewnątrz.
   * Konfiguracja systemowego firewalla **UFW (Uncomplicated Firewall)** wewnątrz systemu Ubuntu.

## 🔍 Troubleshooting i wyzwania (Czego się nauczyłem)
* **Diagnozowanie połączeń (Timeout):** W przypadku problemów z połączeniem z usługą na niestandardowym porcie (np. `8080`), kluczowa była weryfikacja używanego protokołu w przeglądarce (częsty błąd: wymuszanie `HTTPS` na usłudze działającej pod czystym `HTTP`) oraz weryfikacja przepływu ruchu przez obie warstwy zapór (Azure NSG -> Linux UFW).

## 👤 Autor
**Bartosz Staśkiewicz**
Student Inżynierii i Bezpieczeństwa Sieci Komputerowych
<img width="1873" height="1025" alt="obraz" src="https://github.com/user-attachments/assets/55ddeae7-1535-4e77-af4b-b5b2f34654c6" />
<img width="781" height="379" alt="obraz" src="https://github.com/user-attachments/assets/b5b31c37-3b78-4bd6-ba4b-0050fcfdf265" />
<img width="862" height="289" alt="obraz" src="https://github.com/user-attachments/assets/699419bf-1794-4077-971c-2918013dfebb" />
<img width="1862" height="940" alt="obraz" src="https://github.com/user-attachments/assets/34609e26-a638-4d25-a90b-cee3ce296660" />



