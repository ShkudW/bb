# bb

```
@echo off
set "UNC_PATH=\\Server\Share"
set "LOG_FILE=%UNC_PATH%\executed.txt"

if not exist "%LOG_FILE%" type nul > "%LOG_FILE%"

for %%F in (bin1.exe bin2.exe bin3.exe bin4.exe bin5.exe) do (
    findstr /i /x /c:"%%F" "%LOG_FILE%" >nul
    
    if errorlevel 1 (
        echo %%F>>"%LOG_FILE%"
        
        "%UNC_PATH%\%%F"
        

        exit /b
    )
)

```
