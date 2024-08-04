

# Domain Controller Checker

This project is a tool for checking whether computers in various projects are part of a domain. It reads configurations from a file, processes each project to determine which computers are not in the domain, and writes the results to output files.

## Features

- **Configuration File:** Reads project configurations from a specified file.
- **Domain Checking:** Uses LDAP queries to check if computers are in the domain.
- **Parallel Processing:** Processes multiple computers concurrently for efficiency.
- **Logging:** Logs important events and errors during the execution.

## Getting Started

### Prerequisites

- .NET Framework or .NET Core installed on your machine.
- Access to the Active Directory.

### Installation

1. **Clone the repository:**
   ```sh
   git clone https://github.com/enessubasi63/HostnameController.git
   cd domain-controller-checker
   ```

2. **Configure the Project:**
   - Create a configuration file named `config.txt` in the root directory.
   - Add project configurations in the format:
     ```
     ProjectName=NumberOfComputers
     ```
     Example:
     ```
     ProjectA=50
     ProjectB=150
     ```

3. **Build the Project:**
   ```sh
   dotnet build
   ```

4. **Run the Application:**
   ```sh
   dotnet run
   ```

### Configuration File

The configuration file (`config.txt`) should be placed in the root directory of the project. It should contain the project names and the number of computers to check in each project. The format should be as follows:
```
ProjectName1=NumberOfComputers1
ProjectName2=NumberOfComputers2
...
```

### Logging

The application logs its operations to a log file named `application_log.txt` located in the root directory. Each log entry includes a timestamp and a message indicating the operation being performed or any errors encountered.

## Code Explanation

### Main Class

- The `Program` class contains the main logic of the application.
- The `projects` dictionary stores the project names and the number of computers for each project.
- The `outputDirectory` variable specifies the directory where the output files will be saved.
- The `configFilePath` variable specifies the path to the configuration file.
- The `logFilePath` variable specifies the path to the log file.

### Methods

1. **Main Method:**
   - Starts the application, loads the configuration, creates the output directory, processes the projects, and logs the completion of the application.

2. **CreateOutputDirectory Method:**
   - Checks if the output directory exists and creates it if it does not.

3. **ProcessProjects Method:**
   - Iterates over each project, processes the computers, writes the non-domain computers to an output file, and logs the completion of the processing.

4. **ProcessComputer Method:**
   - Checks if a computer is in the domain and adds it to the list of non-domain computers if it is not.

5. **WriteNotInDomainComputers Method:**
   - Writes the list of non-domain computers to an output file and logs the operation.

6. **LoadConfig Method:**
   - Loads the project configurations from the configuration file and logs the operation.

7. **IsComputerInDomain Method:**
   - Checks if a computer is in the domain using LDAP queries and logs any errors encountered.

8. **Log Method:**
   - Writes a log entry to the log file.

---

# Domain Denetleyici

Bu proje, çeşitli projelerdeki bilgisayarların bir domain'e dahil olup olmadığını kontrol eden bir araçtır. Bir dosyadan yapılandırmaları okur, her projeyi işleyerek domain'de olmayan bilgisayarları belirler ve sonuçları çıkış dosyalarına yazar.

## Özellikler

- **Yapılandırma Dosyası:** Belirtilen dosyadan proje yapılandırmalarını okur.
- **Domain Kontrolü:** Bilgisayarların domain'de olup olmadığını kontrol etmek için LDAP sorgularını kullanır.
- **Paralel İşleme:** Verimlilik için birden fazla bilgisayarı aynı anda işler.
- **Loglama:** Uygulama sırasında önemli olayları ve hataları loglar.

## Başlarken

### Gereksinimler

- Makinenizde yüklü .NET Framework veya .NET Core.
- Active Directory erişimi.

### Kurulum

1. **Depoyu Kopyalayın:**
   ```sh
   git clone https://github.com/enessubasi63/HostnameController.git
   cd domain-controller-checker
   ```

2. **Projeyi Yapılandırın:**
   - Ana dizine `config.txt` adlı bir yapılandırma dosyası oluşturun.
   - Proje yapılandırmalarını şu formatta ekleyin:
     ```
     ProjeAdi=BilgisayarSayisi
     ```
     Örnek:
     ```
     ProjeA=50
     ProjeB=150
     ```

3. **Projeyi Derleyin:**
   ```sh
   dotnet build
   ```

4. **Uygulamayı Çalıştırın:**
   ```sh
   dotnet run
   ```

### Yapılandırma Dosyası

Yapılandırma dosyası (`config.txt`), projenin ana dizinine yerleştirilmelidir. Dosya, proje adlarını ve her projede kontrol edilecek bilgisayar sayılarını içermelidir. Format şu şekilde olmalıdır:
```
ProjeAdi1=BilgisayarSayisi1
ProjeAdi2=BilgisayarSayisi2
...
```

### Loglama

Uygulama, işlemlerini ve karşılaşılan hataları, ana dizinde bulunan `application_log.txt` adlı log dosyasına kaydeder. Her log girdisi, gerçekleştirilen işlemi veya karşılaşılan hataları belirten bir zaman damgası ve bir mesaj içerir.

## Kod Açıklaması

### Ana Sınıf

- `Program` sınıfı, uygulamanın ana mantığını içerir.
- `projects` sözlüğü, proje adlarını ve her proje için bilgisayar sayılarını saklar.
- `outputDirectory` değişkeni, çıkış dosyalarının kaydedileceği dizini belirtir.
- `configFilePath` değişkeni, yapılandırma dosyasının yolunu belirtir.
- `logFilePath` değişkeni, log dosyasının yolunu belirtir.

### Metotlar

1. **Main Metodu:**
   - Uygulamayı başlatır, yapılandırmayı yükler, çıkış dizinini oluşturur, projeleri işler ve uygulamanın tamamlandığını loglar.

2. **CreateOutputDirectory Metodu:**
   - Çıkış dizininin var olup olmadığını kontrol eder ve yoksa oluşturur.

3. **ProcessProjects Metodu:**
   - Her projeyi işler, bilgisayarları kontrol eder, domain'de olmayan bilgisayarları bir çıkış dosyasına yazar ve işlemin tamamlandığını loglar.

4. **ProcessComputer Metodu:**
   - Bir bilgisayarın domain'de olup olmadığını kontrol eder ve değilse, domain'de olmayan bilgisayarlar listesine ekler.

5. **WriteNotInDomainComputers Metodu:**
   - Domain'de olmayan bilgisayarları bir çıkış dosyasına yazar ve işlemi loglar.

6. **LoadConfig Metodu:**
   - Yapılandırma dosyasından proje yapılandırmalarını yükler ve işlemi loglar.

7. **IsComputerInDomain Metodu:**
   - Bir bilgisayarın domain'de olup olmadığını LDAP sorguları kullanarak kontrol eder ve karşılaşılan hataları loglar.

8. **Log Metodu:**
   - Log dosyasına bir log girdisi yazar.
