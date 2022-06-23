


- [Installing Chocolatey](https://docs.chocolatey.org/en-us/choco/setup)


- Install with cmd.exe
- Run the following command:

- @"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "[System.Net.ServicePointManager]::SecurityProtocol = 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"


- success installed 

- C:\Users\Administrator>choco
- Chocolatey v1.1.0
- Please run 'choco -?' or 'choco <command> -?' for help menu.