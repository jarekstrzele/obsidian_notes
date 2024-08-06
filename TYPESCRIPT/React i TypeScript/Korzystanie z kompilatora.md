
- `npm install -g typescript`
- `tsc nazwaPliku.ts` -> generuje plik `.js`
- `node nazwaPliku.js`


----
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










