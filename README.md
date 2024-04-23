# Extract Assembly

``` bash
zip -FF NmapOne.zip --out NmapOneOut.zip
unzip NmapOneOut.zip
```

# Prepare & Install

```
@echo off

rem ****************************************************************************
rem * Prepare standalone Nmap on your EVILMACHINE
rem ****************************************************************************
rem Create folder for standalone distrib: C:\Wrk\SborkaNmap\Nmap_Standalone
rem Download Npcap & Nmap installers
rem Extract Npcap installer, for example 7z:  C:\Programs\7-Zip\7z.exe x -aos npcap-1.79.exe -oC:\Wrk\SborkaNmap\Nmap_Standalone\Npcap
rem Install Nmap on EVILMACHINE for exctract Nmap binary and copy: to C:\Wrk\SborkaNmap\Nmap_Standalone\Nmap
rem Copy files: C:\Wrk\SborkaNmap\Nmap_Standalone\Npcap\x64\Packet.dll, wpcap.dll to Nmap folder: C:\Wrk\SborkaNmap\Nmap_Standalone\Nmap

rem ****************************************************************************
rem * Install on VICTIMMACHINE
rem ****************************************************************************
@echo off

echo Install NPCAP driver
%CD%\Npcap\NPFInstall.exe -i
copy /Y %CD%\Npcap\npcap.sys %SystemRoot%\system32\DRIVERS\npcap.sys
sc start npcap

echo Install VC_redist x64 and x86 (need for Nmap)
VC_redist.x64.exe /quiet 
VC_redist.x86.exe /quiet 

echo Run NMAP for test
%CD%\Nmap\nmap.exe

echo Run Nmap for scan: nmap -sS -F 192.168.0.1
echo Enjoy!!!
```
