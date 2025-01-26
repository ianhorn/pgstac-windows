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

# Download PostgreSQL client binary
RUN curl -L -o C:\\temp\\postgresql-client.zip https://get.enterprisedb.com/postgresql/postgresql-16.2-1-windows-x64-binaries.zip && \
    mkdir C:\\pgsql && \
    C:\\PowerShell\\pwsh.exe -Command "Expand-Archive -Path 'C:\\temp\\postgresql-client.zip' -DestinationPath 'C:\\pgsql'" && \
    del C:\\temp\\postgresql-client.zip

# Add PostgreSQL client to the system PATH
ENV PATH="C:\\pgsql\\pgsql\\bin;%PATH%"

# Add PowerShell to PATH
ENV PATH="C:\\PowerShell;C:\\Python;C:\\Python\\scripts;${PATH}"

# Verify installation
RUN psql --version

# Verify PowerShell installation
RUN C:\\PowerShell\\pwsh.exe -Command "Write-Output 'PowerShell Installed Successfully'"

WORKDIR C:\\