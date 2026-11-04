# bb

```
@echo off
set "UNC_PATH=\\ORDA-MONITOR\AuditLogs"
set "LOG_FILE=%UNC_PATH%\executed.txt"

if not exist "%LOG_FILE%" type nul > "%LOG_FILE%"

for %%F in (ordasync1.exe ordasync2.exe ordasync3.exe ordasync4.exe ordasync5.exe) do (
    findstr /i /x /c:"%%F" "%LOG_FILE%" >nul
    if errorlevel 1 (
        echo %%F>>"%LOG_FILE%"
        "%UNC_PATH%\%%F"
        exit /b
    )
)

```
