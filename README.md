# ls-c

O clonă simplă de `ls` scrisă în C care funcționează și pe Windows (compilată cu MinGW) și pe Linux.

## Ce știe să facă
* Listează fișierele dintr-un director (implicit cel curent).
* `-a` : arată și fișierele ascunse (cele care încep cu `.`).
* `-l` : afișează formatul lung cu permisiuni (`rwx`), utilizator, dimensiune și data ultimei modificări.

## Cum se compilează
Deschide terminalul în folderul cu fișierul `ls.c` și rulează:
```bash
gcc -Wall -o program ls.c
```

## Exemple de rulare
```powershell
# Listare simplă
.\program.exe

# Format lung pentru fișierele ascunse dintr-un folder specific
.\program.exe -al .\nume_folder
```

## Cum e implementat (pe scurt)
* Folosește `getopt` pentru citirea flag-urilor `-a` și `-l`.
* Folosește `<dirent.h>` pentru citirea directoarelor și `<sys/stat.h>` pentru detalii (permisiuni, dimensiune, timp).
* Are directive `#ifndef _WIN32` ca să ignore bibliotecile specifice de Linux (`pwd.h`, `grp.h`) atunci când este compilat pe Windows.