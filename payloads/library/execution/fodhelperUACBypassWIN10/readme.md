https://pentestit.de/bash-bunny-neue-uac-bypass-methode-windows-10/

Bash Bunny – Neue UAC-Bypass-Methode Windows 10
30/05/2017
Ein deutscher Student hat eine Variante des bereits im August 2016 vom Sicherheitsforscher Matt Nelson entdeckten UAC-Bypass-Methode veröffentlicht.

Während Nelsons Methode das eingebaute Event Viewer-Dienstprogramm (eventvwr.exe) verwendet, nutzt Christian die Datei fodhelper.exe für eine UAC-Bypass aus.

Was ist das eigentlich das Problem? Normalerweise werden Anwendungen in Windows 10 standardmäßig mit den Rechten eines normalen Benutzers ausgeführt. Wenn jedoch höhere Privilegien nötig sind, etwa um ein Setup-Programm auszuführen, verfügt die UAC über einen Auto-Elevation-Mechanismus, der die Rechte des Administrators bei Bedarf erhöht. Auto-Elevation funktioniert nur, wenn der angemeldete User prinzipiell Administrator ist. Meldet sich ein “normaler” Benutzer an, so gibt es ja im Hintergrund für diesen kein Admin-Token.

Microsoft nutzt dazu vertrauenswürdige Binärdateien, die an vertrauenswürdigen Orten wie z.B. in „C:\Windows\ System32“ abgelegt sind.

Genau wie eventvwr.exe ist fodhelper.exe auch eine vertrauenswürdige Binärdatei, was bedeutet, dass in Windows 10 kein UAC-Fenster angezeigt wird, wenn das Programm gestartet wird oder wenn andere Prozesse aus dem fodhelper.exe-übergeordneten Prozess hervorgehen.

Christian legte in Windows 10 zwei Registrierungsschlüssel an, in denen er benutzerdefinierte Befehle integrierte. Nun konnten beim Start der Datei fodhelper.exe diese Befehle in einem höheren Kontext ausgeführt werden. Der Forscher hat den Beweis des Konzeptes (PoC) auf GitHub veröffentlicht. Um zu verhindern, dass Malware diese UAC-Bypass-Technik ausnutzt, empfiehlt er, dass Benutzer für ihr Standard-Windows-Profil kein Administratorenkonto nutzen.

Ich habe (als Proof of Concept) ein Skript für den Bash Bunny verfasst, dass die Registrierungsschlüssel anlegt, die Datei fodhelper.exe ausführt und mit daraus resultierenden höheren Rechten einen neuen Nutzer anlegt.

https://youtu.be/FngI7SQxoPA
