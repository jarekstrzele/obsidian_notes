
# Podstawa
- `npm install -g typescript`
- `tsc nazwaPliku.ts` -> generuje plik `.js`
- `node nazwaPliku.js`



------
# użycie `tsc --init` - uruchomianie w sposób zorganizowany `tsconfig.json`

==struktura projektu==

```
TwójProjekt/
├── src/          // Katalog z plikami TypeScript
│   ├── app.ts    // Przykładowy plik TypeScript
├── dist/         // Katalog na skompilowane pliki JavaScript
├── tsconfig.json // Plik konfiguracyjny TypeScript
```



`tsconfig.json`

```json
{
  "compilerOptions": {
    "target": "es6",           // Kompiluj do ECMAScript 6
    "module": "commonjs",      // Używaj systemu modułów CommonJS (popularne w Node.js)
    "outDir": "./dist",        // Wygenerowane pliki umieść w katalogu "dist"
    "rootDir": "./src",        // Pliki źródłowe znajdują się w katalogu "src"
    "strict": true,            // Włącz wszystkie rygorystyczne sprawdzenia typów
    "esModuleInterop": true,   // Umożliwia interoperacyjność z ECMAScript
    "skipLibCheck": true,      // Pomija sprawdzanie plików definicji bibliotek
    "forceConsistentCasingInFileNames": true // Wymusza zgodność wielkości liter w nazwach plików
  },
  "include": ["src"],           // Zawiera pliki do kompilacji (np. wszystkie pliki w katalogu "src")
  "exclude": ["node_modules", "dist"] // Wyklucza pliki z kompilacji
}

```


w głównej ścieżce: `
```powershell
tsc

```

---
# można dodać `package.json`
```json
{
    "name": "tsc-play",
    "dependencies": {
    "typescript": "^5.5.4"
    },
    "scripts": {
	    "build": "tsc src/przyklad.ts"
    }
    }
```

wykonaj komendę `npm run  build`


----
# BŁĄD 

Jeżeli pojawia się ==błąd==:
```
tsc : File C:\Users\jaros\AppData\Roaming\npm\tsc.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see 
about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170.
```

> Ten komunikat o błędzie wskazuje, że na Twoim systemie Windows ustawione są ograniczenia związane z uruchamianiem skryptów `PowerShell`, co uniemożliwia uruchomienie komendy `tsc` (kompilatora TypeScript). Możesz to naprawić, zmieniając politykę wykonywania skryptów `PowerShell`.

ROZWIĄZANIE:
- uruchom `PowerShell` jako admin

```PowerShell
PS C:\Windows\system32> Get-ExecutionPolicy
Restricted
PS C:\Windows\system32> Set-ExecutionPolicy RemoteSigned

Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution policy might expose
you to the security risks described in the about_Execution_Policies help topic at
https:/go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
PS C:\Windows\system32>
```

**Polityka `RemoteSigned`:** Umożliwia uruchamianie lokalnych skryptów bez podpisu, ale wymaga podpisu dla skryptów pobranych z internetu.`

POWRÓT do poprzednich ustaleń
`Set-ExecutionPolicy Restricted`

-------------








