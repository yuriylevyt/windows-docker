FROM mcr.microsoft.com/windows/servercore:ltsc2019

#
RUN powershell "mkdir c:\temp" 


#
# JAVA
RUN powershell "(New-Object System.Net.WebClient).DownloadFile('https://download.oracle.com/java/20/archive/jdk-20_windows-x64_bin.zip', 'c:\temp\jdk-20_windows-x64_bin.zip')"
RUN powershell "Expand-Archive c:\temp\jdk-20_windows-x64_bin.zip -DestinationPath c:\temp"

ENV JAVA_HOME=c:\\temp\\jdk-20


#
# maven
RUN powershell "(New-Object System.Net.WebClient).DownloadFile('https://dlcdn.apache.org/maven/maven-3/3.9.1/binaries/apache-maven-3.9.1-bin.zip', 'c:\temp\apache-maven-3.9.1-bin.zip')"
RUN powershell "Expand-Archive c:\temp\apache-maven-3.9.1-bin.zip -DestinationPath c:\temp"

ENV MAVEN_HOME=c:\\temp\\apache-maven-3.9.1


#
# Launch4J
RUN powershell "(New-Object System.Net.WebClient).DownloadFile('https://downloads.sourceforge.net/project/launch4j/launch4j-3/3.50/launch4j-3.50-win32.zip?ts=gAAAAABkPjn8Kq5sCijx48kQCJZi19GrbBVaJwMPmS_j2rS0FNq8pVJ_Y1mefhx5gTowcAQrvtgbqrurM5xVnE6qCJ-9uVr4yw%3D%3D&r=https%3A%2F%2Fsourceforge.net%2Fprojects%2Flaunch4j%2Ffiles%2Flaunch4j-3%2F3.50%2Flaunch4j-3.50-win32.zip%2Fdownload', 'c:\temp\launch4j-3.50-win32.zip')"
RUN powershell "Expand-Archive c:\temp\launch4j-3.50-win32.zip -DestinationPath c:\temp"

ENV LAUNCH4J_HOME=C:\\temp\\launch4j


#
# NSIS
RUN powershell "(New-Object System.Net.WebClient).DownloadFile('https://downloads.sourceforge.net/project/nsis/NSIS%203/3.08/nsis-3.08.zip?ts=gAAAAABkPo9t0uuAn_2_w7LauYKMrbwMXTyUSCte_1DZBiptZQiyRP5GAO1HibqE2qS6a3lwMf-vjV00z9J1nFLN2VFpF7aDAg%3D%3D&r=https%3A%2F%2Fsourceforge.net%2Fprojects%2Fnsis%2Ffiles%2FNSIS%25203%2F3.08%2Fnsis-3.08.zip%2Fdownload', 'c:\temp\nsis-3.08.zip')"
RUN powershell "Expand-Archive c:\temp\nsis-3.08.zip -DestinationPath c:\temp"

ENV NSIS_HOME=C:\\temp\\nsis-3.08

#
# NSIS EnVar plugin
RUN powershell "(New-Object System.Net.WebClient).DownloadFile('https://nsis.sourceforge.io/mediawiki/images/7/7f/EnVar_plugin.zip', 'c:\temp\EnVar_plugin.zip')"
# COPY ..\\install\\EnVar_plugin.zip c:\\temp\\EnVar_plugin.zip
RUN powershell "Expand-Archive c:\temp\EnVar_plugin.zip -DestinationPath c:\temp"
RUN powershell "cp c:\temp\Plugins\x86-ansi\EnVar.dll C:\temp\nsis-3.08\Plugins\x86-ansi\EnVar.dll"
RUN powershell "cp c:\temp\Plugins\x86-unicode\EnVar.dll C:\temp\nsis-3.08\Plugins\x86-unicode\EnVar.dll"


#
# Set PATH
ENV PATH="${JAVA_HOME}\\bin;${MAVEN_HOME}\\bin;${LAUNCH4J_HOME};${NSIS_HOME}"
