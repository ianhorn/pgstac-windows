FROM intland/postgres:windows-16.2-twx

# Create directories
RUN mkdir C:\\Temp

WORKDIR C:\\Temp

# Download the PostGIS installer
RUN curl -L -o postgis_bundle.exe https://ftp.postgresql.org/pub/postgis/pg16/v3.4.2/win64/postgis-bundle-pg16x64-setup-3.4.2-1.exe

# Run installer interactively
RUN cmd /c postgis_bundle.exe

# Ensure PostGIS binaries are on the PATH
ENV PATH="C:\\PostGIS\\bin;${PATH}"

# # Enable PostGIS extension
# RUN C:\\Program Files\\PostgreSQL\\16\\bin\\psql -U postgres -d postgres -c "CREATE EXTENSION IF NOT EXISTS postgis;"