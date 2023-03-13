# VI PRØVEDE AT LAVE ET MAVEN PROJEKT OM TIL ET GRADLE PROJEKT
## det virkede ikke :,(

### Hvordan ville man egentlig gøre det??? <br>

#### Du vil starte med at installere gradle.<br>

Bedste måde at gøre det på er at bruge en packet manager<br>
<ul>
  <li>For Windows er det anbefalet at bruge Chocolattey :yum:</li><br>
  dette kan gøres med kommandoen
  <li>Mac kan bruge Homebrew i stedet :coffee: </li> <br><br>
  
  Chocolattey kan instaleres med kommandoen: <br>
 ``` @"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"```
  
  Herfra kan man installere Gradle direkte fra command prompt ved at skrive<br>
  ```choco install gradle```
  > Mac brugere øøøh, idunno :broken_heart:
 <br>

### Hvordan ville i så konvertere programmet??!? <br>
  > Det burde være simpelt nok haha...
<p>
  <ul>
<li>Fork en kopi af jeres fortrukne Maven projekt</li>
    <li>kør gradle init og gradle build i terminalen</li>
    <li>byg jeres gradle.build til at matche jeres dependencies i pom.xml</li>
    f.eks. vil jeres dependencies i pom se sådan her ud i gradle.build:<br>
   <code>
    repositories {
     mavenCentral()}
dependencies{
     implementation 'dk.kea:SuperhelteProjekt:1.0-SNAPSHOT'
    testImplementation 'org.junit.jupiter:junit-jupiter:RELEASE'}
    </code>
  <ul>
    <br>
</p>

## FIK I LAVET NOGET GITHUB ACTIONS OVERHOVEDET?? :skull::skull::skull:
### Kinda
<p>
  
Vi lavede et script der opretter en fil der siger "hello world".<br>
Derefter begyndte vi at lave en yml fil der tester den er oprettet ordentligt!<br>
Vores YML fil ser sådan her ud: </p><br>
      <code>
        
      name: test hello world 

      on: 
        push:
          branches: 
            -'main'

        jobs: 
          test_hello: 
            name: test hello
            runs-on: ubuntu-latest 

        step: 
        - name: Checkout
          uses: actions/checkout@v3

          name: test if file exsist
          uses: andstor/file-existence-action@v2
          with: 
            file: "hello_world.txt"

          name: test inside file
          uses: ubuntu-latest
            run: |
              contains(cat hello_world.txt, 'Hello World')

          name: push changes 
            if: succes()
            run: |
              git 
      </code>

* **on: push: branches: 'main'** siger at koden kører når der bliver pushed til main
* **step: -name: chekout uses actions/checkout@v3** lader filen få adgang til repositoriet
* **test if file exists** tjekker at filen "hello_world.txt" eksisterer
* **test inside files** tester at der står "Hello World" inde i filen
* **push changes** pusher filen hvis de to test er succesfulde


<br><br>

## All in all, vi prøvede vores bedste, det var en god lære oplevelse


<br><br><br><br><br><br><br>
# In the land of the blind atleast we tried
<img src=https://cdn.britannica.com/66/103166-050-9423AD02/Stevie-Wonder.jpg>
