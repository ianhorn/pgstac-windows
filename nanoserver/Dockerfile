# Use NanoServer as the base image
FROM mcr.microsoft.com/windows-cssc/python:3.11-nanoserver-ltsc2022 

# Set up environment variables
ENV POWERSHELL_VERSION=7.3.5
ENV POWERSHELL_DOWNLOAD_URL=https://github.com/PowerShell/PowerShell/releases/download/v${POWERSHELL_VERSION}/PowerShell-${POWERSHELL_VERSION}-win-x64.zip

# Create directories
RUN mkdir C:\\Temp

# Set working directory
WORKDIR C:\\Temp

# Download and install PowerShell
RUN curl -L -o PowerShell.zip %POWERSHELL_DOWNLOAD_URL% && \
    mkdir C:\\PowerShell && \
    tar -xf PowerShell.zip -C C:\\PowerShell && \
    del PowerShell.zip     
# Add PowerShell to PATH
ENV PATH="C:\\PowerShell;C:\\Python;C:\\Python\\scripts;${PATH}"

# Verify PowerShell installation
RUN C:\\PowerShell\\pwsh.exe -Command "Write-Output 'PowerShell Installed Successfully'"

WORKDIR C:\\