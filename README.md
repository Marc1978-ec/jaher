@ECHO OFF
:PASSW
title   USUARIO Y PASSWORD
if %PROCESSOR_ARCHITECTURE%==x86 (goto Instalar32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto Instalar64)


CLS
:Instalar32
COLOR 1E
MODE CON cols=41 lines=6
CLS
ECHO   [====================================]
ECHO     UTILITARIOS JAHER      (30.1.2025)
ECHO.
set/p user=  "Escribe tu Usuario:       "
EditV32.exe -p   "Escribe tu Password:      " -m pass
ECHO.
ECHO   [====================================]
if %user%==usuario else if %user%==admin (goto verifica) 
:verifica
if %pass%==jaher2024** (goto ZONAS) else if %pass%==admin  (goto ZONAS) else goto error32


:error32
CLS
COLOR 4F
MODE CON cols=53 lines=8
ECHO.
ECHO   [================================================]
ECHO                -PASSWORD INCORRECTO-
ECHO.
ECHO                 VUELVA A INGRESARLO
ECHO   [================================================]
>nul ping -n 3 localhost
ECHO.
GOTO Instalar32


:Instalar64
COLOR 1E
MODE CON cols=41 lines=6
CLS
ECHO   [====================================]
ECHO     UTILITARIOS JAHER      (30.1.2025)
ECHO.
set/p user=  "Escribe tu Usuario:       "
EditV64.exe -p   "Escribe tu Password:      " -m pass
ECHO.
ECHO   [====================================]
if %user%==usuario else if %user%==admin (goto verifica) 
:verifica
if %pass%==jaher2024** (goto ZONAS) else if %pass%==admin  (goto ZONAS) else goto error64


:error64
CLS
COLOR 4F
MODE CON cols=53 lines=8
ECHO.
ECHO   [================================================]
ECHO                -PASSWORD INCORRECTO-
ECHO.
ECHO                 VUELVA A INGRESARLO
ECHO   [================================================]
>nul ping -n 3 localhost
GOTO Instalar64



:ZONAS
CLS
color 0F
mode con cols=80 lines=25
title                                   =  MEG@-PC  =
ECHO.
ECHO          FECHA:  30.1.2025                       
ECHO          [----------------------------------------------------------]
ECHO                         " DEPARTAMENTO DE SISTEMAS JAHER "
ECHO.
ECHO              " 1 "  Para   Instalar programas BASICOS (CAJA)
ECHO                     ------------------------------------------------
ECHO              " 2 "  Para   Instalar programas BASICOS (VENTAS)
ECHO                     ------------------------------------------------
ECHO              " 3 "  Para   Instalar programas BASICOS (ADMINISTRADOR)
ECHO                     ------------------------------------------------
ECHO              " 4 "  Para   Instalar programas Uno a Uno
ECHO                     ------------------------------------------------
ECHO              " 5 "  Para   Instalar UPDATES NEW
ECHO                     ------------------------------------------------
ECHO              " 6 "  Para   Instalar STOCK JAHER
ECHO                     ------------------------------------------------
ECHO              " 7 "  Para   Explorar Instaladores
ECHO              " 8 "  Para   Desinstalar
ECHO              " 9 "  Para   Salir
ECHO.
ECHO          [----------------------------------------------------------]
set /p jahadm=  El numero a ejecutar :  
ECHO          [----------------------------------------------------------]
if %jahadm%==1 GOTO PREC_CAJ
if %jahadm%==2 GOTO PREC_VTA
if %jahadm%==3 GOTO PREC_ADM
if %jahadm%==4 GOTO Programas1
if %jahadm%==5 GOTO UPDATES_TOTAL
if %jahadm%==6 GOTO FAV_ZONA_NUEVO
if %jahadm%==7 GOTO ESPLORAR
if %jahadm%==8 GOTO DESINSTALAR
if %jahadm%==9 GOTO Salir
if %jahadm%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO ZONAS


:LIMPIEZA
START "Borrar_Temp.bat" "%SYSTEMROOT%\Borrar_Temp.bat"
Exit

:Salir
Exit


:ESPLORAR
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto EXPLOR32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto EXPLOR64)
ECHO.

:EXPLOR32
ECHO.
START explorer.exe "%PROGRAMFILES%\JAHER"
GOTO MENU1_Z1

:EXPLOR64
ECHO.
START explorer.exe "%PROGRAMFILES(X86)%\JAHER"
GOTO MENU1_Z1


:error
CLS
COLOR F0
MODE CON cols=35 lines=8
ECHO.
ECHO  [=============================]
ECHO          Valor incorrecto.!
ECHO.
ECHO         Vuelva a Intentarlo
ECHO  [=============================]
ECHO.
TIMEOUT /T 05 
GOTO MENU1_Z1

ECHO ***************************** TIGHT VN ******************************************************

:TIG_ALL

CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto TIGH32_INST) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto TIGH64_INST)
ECHO.

:TIGH32_INST
CLS
Color 03
mode con cols=35 lines=7
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO           (( TightVN ))
ECHO                          (32Bit)
ECHO  [==============================]
TightVNC32bit.msi
ECHO.
DEL /F /S /Q  ""%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Start TightVNC Service.lnk"
COPY /D /V /Y "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\TightVNC\TightVNC Server (Service Mode)\Start TightVNC Service.lnk" "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs"
goto REINICIAR



:TIGH64_INST
CLS
Color 03
mode con cols=35 lines=7
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO           (( TightVN ))
ECHO                          (64Bit)
ECHO  [==============================]
TightVNC64bit.msi
ECHO.
ECHO.
DEL /F /S /Q  ""%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Start TightVNC Service.lnk"
COPY /D /V /Y "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\TightVNC\TightVNC Server (Service Mode)\Start TightVNC Service.lnk" "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs"
goto REINICIAR

:THEMES
Color 1f
mode con cols=80 lines=18
ECHO          [==========================================================]
ECHO                               I N S T A L A N D O
ECHO.
ECHO                            (( CORREO THUNDERBIRD ))
ECHO.
ECHO             " 1 "   Para    Instalar JAHER THEME 
ECHO                        ------------------
ECHO             " 2 "   Para    Instalar MOTOMARKET THEME 
ECHO                           ------------------
ECHO             " 3 "   Para    Menu Anterior.
ECHO                           ------------------
ECHO             " 4 "   Para    Menu Principal.
ECHO                           ------------------
ECHO             " 5 "   Para    Salir
ECHO.
ECHO          [==========================================================]
set /p backup=Ingresa el numero a su eleccion :    
ECHO          [==========================================================]
if %backup%==1 GOTO TEN_RUN
if %backup%==2 GOTO TUN_UNI
if %backup%==3 GOTO Programas2
if %backup%==4 GOTO ZONAS
if %backup%==5 GOTO Salir
if %backup%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO THEMES

ECHO ***************************** TIGHT VN ******************************************************
ECHO ************************* R E I N I C I A R *************************************************


:REINICIAR
CLS
Color 03
mode con cols=35 lines=4
ECHO  [==============================]
ECHO            REINICIANDO PC
ECHO  [==============================]
>nul ping -n 4 localhost
shutdown.exe -R -F -T 03 -C "Reiniciando en 3 segundos"
GOTO Salir


ECHO ************************* R E I N I C I A R *************************************************
ECHO ************************* F A V O R I T O S *************************************************

:FAV_ZONA_NUEVO
title                               UTILITARIOS JAHER
CLS
COLOR F0
mode con cols=80 lines=18
ECHO           [-----------------------------------------------------------] 
ECHO                              ACCESOS DIRECTOS JAHER
ECHO          [----------------------------------------------------------]
ECHO                          " DEPARTAMENTO DE SISTEMA JAHER "
ECHO.
ECHO              " 1 "  Para   Accesos Directos Standar
ECHO                     ------------------------------------------------
ECHO              " 2 "  Para   Acceso Directo Mutiplataforma
ECHO                     ------------------------------------------------
ECHO              " 4 "  Para   Menu Principal
ECHO              " 5 "  Para   Salir
ECHO.
ECHO          [----------------------------------------------------------]
ECHO.
set /p updt=  El numero a tu eleccion :    
ECHO.
if %updt%==1 GOTO FA_STANDAR 
if %updt%==2 GOTO FA_MULTIPLATAFORMA
if %updt%==4 GOTO ZONAS
if %updt%==5 GOTO Salir
if %updt%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO FAV_ZONA_NUEVO

:FA_STANDAR
CLS
Color 03
mode con cols=35 lines=4
ECHO  [==============================]
ECHO            CONFIGURANDO
ECHO  [==============================]
ECHO.
RD /S /Q "%ProgramData%\Microsoft\Windows\Start Menu\Programs\JAHER"
MD "C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar\JAHER"
MD "%ProgramData%\Microsoft\Windows\Start Menu\Programs\JAHER"
ECHO.
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\security\exception.sites"
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\deployment.properties"
DEL /F /S /Q "C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar\Internet Explorer.lnk"
reg add "HKCU\Software\Microsoft\Internet Explorer\Main" /v "Start Page" /t REG_SZ /d "https://www.jaher.com.ec/" /f
DEL /F /S /Q "%HomePath%\Links\*.*"
DEL /F /S /Q "%userprofile%\Favorites\Links\*.*"
DEL /F /S /Q "%userprofile%\Documents\bookmark.htm"
DEL /F /S /Q "%Public%\Documents\bookmark.htm"
DEL /F /S /Q "%Public%\desktop\STOCK_WEB_1.url"
DEL /F /S /Q "%Public%\desktop\STOCK_WEB_2.url"
DEL /F /S /Q "%Public%\desktop\STOCK_WEB_SOLARIS.url"
DEL /F /S /Q "%Public%\desktop\Internet Explorer.lnk"
DEL /F /S /Q "%userprofile%\Documents\bookmark.htm"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_WEB_1.url"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_WEB_2.url"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_WEB_SOLARIS.url"
DEL /F /S /Q "%userprofile%\desktop\Internet Explorer.lnk"
DEL /F /S /Q "%Public%\desktop\ACCESOS_STOCK_WEB_1.url"
DEL /F /S /Q "%Public%\desktop\ACCESOS_STOCK_WEB_2.url"
DEL /F /S /Q "%Public%\desktop\ACCESOS_STOCK_WEB_SOLARIS.url"
DEL /F /S /Q "%userprofile%\Desktop\ACCESOS_STOCK_WEB_1.url"
DEL /F /S /Q "%userprofile%\Desktop\ACCESOS_STOCK_WEB_2.url"
DEL /F /S /Q "%userprofile%\Desktop\ACCESOS_STOCK_WEB_SOLARIS.url
ECHO.
DEL /F /S /Q "%Public%\desktop\STOCK_JAHER_1.lnk"
DEL /F /S /Q "%Public%\desktop\STOCK_JAHER_2.lnk"
DEL /F /S /Q "%Public%\desktop\STOCK_JAHER_SOLARIS.lnk"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_JAHER_1.lnk"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_JAHER_2.lnk"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_JAHER_SOLARIS.lnk"
DEL /F /S /Q "C:\Users\%USERNAME%\Desktop\STOCK_JAHER_1.lnk"
DEL /F /S /Q "C:\Users\%USERNAME%\Desktop\STOCK_JAHER_2.lnk"
DEL /F /S /Q "C:\Users\%USERNAME%\Desktop\STOCK_JAHER_SOLARIS.lnk"
ECHO.
DEL /F /S /Q "C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Windows\SendTo\STOCK_JAHER_1.lnk"
DEL /F /S /Q "C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Windows\SendTo\STOCK_JAHER_2.lnk"
DEL /F /S /Q "C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Windows\SendTo\STOCK_JAHER_SOLARIS.lnk"
ECHO  [==============================]
ECHO           AUTO CONFIG AD 
ECHO  [==============================]
ECHO.
COPY /D /V /Y "Link\stock_L1.jnlp" "C:\APPL" 
COPY /D /V /Y "Link\stock_L2.jnlp" "C:\APPL" 
COPY /D /V /Y "Link\stock_S1.jnlp" "C:\APPL"
COPY /D /V /Y "Link\Stock_logook.ico" "C:\APPL"
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%Public%\desktop\STOCK_JAHER_1.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\stock_L1.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Stock_logook.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%Public%\desktop\STOCK_JAHER_2.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\stock_L2.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Stock_logook.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%Public%\desktop\STOCK_JAHER_SOLARIS.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\stock_S1.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Stock_logook.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%ProgramData%\Microsoft\Windows\Start Menu\Programs\JAHER\STOCK_JAHER_1.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\stock_L1.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Stock_logook.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%ProgramData%\Microsoft\Windows\Start Menu\Programs\JAHER\STOCK_JAHER_2.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\stock_L2.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Stock_logook.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%ProgramData%\Microsoft\Windows\Start Menu\Programs\JAHER\STOCK_JAHER_SOLARIS.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\stock_S1.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Stock_logook.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
ECHO.
Java_Conf.exe
GOTO ZONAS

:FA_MULTIPLATAFORMA
CLS
Color 03
mode con cols=35 lines=4
ECHO  [==============================]
ECHO            CONFIGURANDO
ECHO  [==============================]
ECHO.
RD /S /Q "%ProgramData%\Microsoft\Windows\Start Menu\Programs\JAHER"
MD "C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar\JAHER"
MD "%ProgramData%\Microsoft\Windows\Start Menu\Programs\JAHER"
ECHO.
DEL /F /S /Q "%HomePath%\Links\*.*"
DEL /F /S /Q "%userprofile%\Favorites\Links\*.*"
DEL /F /S /Q "%userprofile%\Documents\bookmark.htm"
DEL /F /S /Q "%Public%\Documents\bookmark.htm"
DEL /F /S /Q "%Public%\desktop\STOCK_WEB_1.url"
DEL /F /S /Q "%Public%\desktop\STOCK_WEB_2.url"
DEL /F /S /Q "%Public%\desktop\STOCK_WEB_SOLARIS.url"
DEL /F /S /Q "%Public%\desktop\Internet Explorer.lnk"
DEL /F /S /Q "%userprofile%\Documents\bookmark.htm"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_WEB_1.url"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_WEB_2.url"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_WEB_SOLARIS.url"
DEL /F /S /Q "%userprofile%\desktop\Internet Explorer.lnk"
DEL /F /S /Q "%Public%\desktop\ACCESOS_STOCK_WEB_1.url"
DEL /F /S /Q "%Public%\desktop\ACCESOS_STOCK_WEB_2.url"
DEL /F /S /Q "%Public%\desktop\ACCESOS_STOCK_WEB_SOLARIS.url"
DEL /F /S /Q "%userprofile%\Desktop\ACCESOS_STOCK_WEB_1.url"
DEL /F /S /Q "%userprofile%\Desktop\ACCESOS_STOCK_WEB_2.url"
DEL /F /S /Q "%userprofile%\Desktop\ACCESOS_STOCK_WEB_SOLARIS.url
ECHO.
DEL /F /S /Q "%Public%\desktop\STOCK_JAHER_1.lnk"
DEL /F /S /Q "%Public%\desktop\STOCK_JAHER_2.lnk"
DEL /F /S /Q "%Public%\desktop\STOCK_JAHER_SOLARIS.lnk"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_JAHER_1.lnk"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_JAHER_2.lnk"
DEL /F /S /Q "%userprofile%\Desktop\STOCK_JAHER_SOLARIS.lnk"
DEL /F /S /Q "C:\Users\%USERNAME%\Desktop\STOCK_JAHER_1.lnk"
DEL /F /S /Q "C:\Users\%USERNAME%\Desktop\STOCK_JAHER_2.lnk"
DEL /F /S /Q "C:\Users\%USERNAME%\Desktop\STOCK_JAHER_SOLARIS.lnk"
ECHO.
DEL /F /S /Q "C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Windows\SendTo\STOCK_JAHER_1.lnk"
DEL /F /S /Q "C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Windows\SendTo\STOCK_JAHER_2.lnk"
DEL /F /S /Q "C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Windows\SendTo\STOCK_JAHER_SOLARIS.lnk"
ECHO  [==============================]
ECHO           AUTO CONFIG AD 
ECHO  [==============================]
ECHO.
COPY /D /V /Y "Link\efigie.jnlp" "C:\APPL"
COPY /D /V /Y "Link\Stock_logook.ico" "C:\APPL"  
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%Public%\desktop\STOCK_JAHER.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\efigie.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Stock_logook.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%ProgramData%\Microsoft\Windows\Start Menu\Programs\JAHER\STOCK_JAHER.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\efigie.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Stock_logook.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
Java_Conf.exe
ECHO.
GOTO ZONAS




ECHO ************************* F A V O R I T O S *************************************************

ECHO *************************PRE CONFIGURACION*************************************************
:PREC_CAJ
TASKKILL /F /IM explorer.exe
CLS
Color 07
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.          CONFIGURAR SEGURIDAD USUARIO
@ECHO.     [====================================]
@ECHO.
REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v EnableLUA /t REG_DWORD  /d 0 /f
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.             CONFIGURAR ENERGIA PC
@ECHO.     [====================================]
@ECHO.
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
powercfg /setactive 758807b5-8e85-43b8-85e2-8b5c0e838670
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.          CONFIGURAR FIREWALL WINDOWS              
@ECHO.     [====================================]
@ECHO. 
netsh advfirewall set allprofiles state off
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.                 CONFIGURAR HORA
@ECHO.     [====================================]
@ECHO.
REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DateTime\Servers /v 1 /t REG_SZ  /d ntp1.jaher.com.ec /f
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.         CONFIGURAR OPCIONES DE INTERNET             
@ECHO.     [====================================]
@ECHO.
certutil -f -v -addstore -enterprise root SecurityAppliance_SSL_CA_FINAL.pem
MD "C:\Instaladores_JH"
COPY /D /V /Y "SecurityAppliance_SSL_CA_FINAL.pem" "C:\Instaladores_JH"
ECHO.
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.            FAVORITOS MICROSOFT EDGE             
@ECHO.     [====================================]
ECHO.
TASKKILL /F /IM msedge.exe
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks.bak"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks.msbak"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Favicons-journal"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Favicons"
ECHO.
COPY /D /V /Y "EdgVTA\Bookmarks" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Bookmarks.bak" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Bookmarks.msbak" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Favicons-journal" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Favicons" "%LocalAppData%\Microsoft\Edge\User Data\Default"
ECHO.
GOTO JAHER_CAJ10


:PREC_VTA
TASKKILL /F /IM explorer.exe
CLS
Color 07
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.          CONFIGURAR SEGURIDAD USUARIO
@ECHO.     [====================================]
@ECHO.
REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v EnableLUA /t REG_DWORD  /d 0 /f
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.             CONFIGURAR ENERGIA PC
@ECHO.     [====================================]
@ECHO.
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
powercfg /setactive 758807b5-8e85-43b8-85e2-8b5c0e838670
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.          CONFIGURAR FIREWALL WINDOWS              
@ECHO.     [====================================]
@ECHO. 
netsh advfirewall set allprofiles state off
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.                 CONFIGURAR HORA
@ECHO.     [====================================]
@ECHO.
REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DateTime\Servers /v 1 /t REG_SZ  /d ntp1.jaher.com.ec /f
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.         CONFIGURAR OPCIONES DE INTERNET             
@ECHO.     [====================================]
@ECHO.
certutil -f -v -addstore -enterprise root SecurityAppliance_SSL_CA_FINAL.pem
MD "C:\Instaladores_JH"
COPY /D /V /Y "SecurityAppliance_SSL_CA_FINAL.pem" "C:\Instaladores_JH"
ECHO.
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.            FAVORITOS MICROSOFT EDGE             
@ECHO.     [====================================]
ECHO.
TASKKILL /F /IM msedge.exe
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks.bak"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks.msbak"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Favicons-journal"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Favicons"
ECHO.
COPY /D /V /Y "EdgVTA\Bookmarks" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Bookmarks.bak" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Bookmarks.msbak" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Favicons-journal" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Favicons" "%LocalAppData%\Microsoft\Edge\User Data\Default"
ECHO.
GOTO JAHER_VTA10

:PREC_ADM
TASKKILL /F /IM explorer.exe
CLS
Color 07
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.          CONFIGURAR SEGURIDAD USUARIO
@ECHO.     [====================================]
@ECHO.
REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v EnableLUA /t REG_DWORD  /d 0 /f
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.             CONFIGURAR ENERGIA PC
@ECHO.     [====================================]
@ECHO.
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
powercfg /setactive 758807b5-8e85-43b8-85e2-8b5c0e838670
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.          CONFIGURAR FIREWALL WINDOWS              
@ECHO.     [====================================]
@ECHO. 
netsh advfirewall set allprofiles state off
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.                 CONFIGURAR HORA
@ECHO.     [====================================]
@ECHO.
REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DateTime\Servers /v 1 /t REG_SZ  /d ntp1.jaher.com.ec /f
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.         CONFIGURAR OPCIONES DE INTERNET             
@ECHO.     [====================================]
@ECHO.
certutil -f -v -addstore -enterprise root SecurityAppliance_SSL_CA_FINAL.pem
MD "C:\Instaladores_JH"
COPY /D /V /Y "SecurityAppliance_SSL_CA_FINAL.pem" "C:\Instaladores_JH"
ECHO.
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.            FAVORITOS MICROSOFT EDGE             
@ECHO.     [====================================]
ECHO.
TASKKILL /F /IM msedge.exe
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks.bak"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks.msbak"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Favicons-journal"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Favicons"
ECHO.
COPY /D /V /Y "EdgADM\Bookmarks" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgADM\Bookmarks.bak" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgADM\Bookmarks.msbak" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgADM\Favicons-journal" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgADM\Favicons" "%LocalAppData%\Microsoft\Edge\User Data\Default"
ECHO.
GOTO JAHER_ADM10

ECHO *************************PRE CONFIGURACION************************************************
ECHO *************************CAJA 10 *********************************************************

:JAHER_CAJ10
CLS
MODE CON cols=40 lines=9
COLOR 07
ECHO.
ECHO  [************************************]
ECHO              - IMPORTANTE -
ECHO.
ECHO      CUANDO TERMINE POR COMPLETO EL 
ECHO       INSTALADOR SE AUTO REINICIARA 
ECHO              EL COMPUTADOR 
ECHO  [************************************] 
>nul ping -n 10 localhost  
MODE CON cols=40 lines=5  
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
DISM /Online /Enable-Feature /FeatureName:NetFx3 /All
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
START /WAIT "NetFram3.5.0.exe" "NetFram3.5.0.exe"
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
NetFram4.8.1.exe /SILENT /VERYSILENT /NORESTART
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJ WIN 10)
powershell.exe -ep bypass -file EliAppWinApp.ps1
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
Cursores.exe
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
COPY /D /V /Y "Escr\Calculator.lnk" "%Public%\desktop"
COPY /D /V /Y "Escr\Paint.lnk" "%Public%\desktop"
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
Wallpaper_JAHER.exe
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
JAHER_NEW.deskthemepack
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
START "JAHER_NEW.theme" "%localappdata%\Microsoft\Windows\Themes\JAHER_NEW\JAHER_NEW.theme"
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
taskkill /f /im SystemSettings.exe
CLS
GOTO CONFCAJ_10


:CONFCAJ_10
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto CONFCAJ_10_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto CONFCAJ_10_64)
ECHO.

:CONFCAJ_10_32
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
ECHO.
Thunderbird_32bit.exe -ms
ECHO.
MD "C:\curl"
curl_win32.exe
regedit /s "RCAJ32.reg"
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
LibreOffice_32.msi /passive 
ECHO.
GOTO INSTALSTANDAR_NORMAL


:CONFCAJ_10_64
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
ECHO.
Thunderbird_64bit.exe -ms
ECHO.
MD "C:\curl"
curl_win64.exe
regedit /s "RCAJ64.reg"
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
LibreOffice_64.msi /passive 
ECHO.
GOTO INSTALSTANDAR_NORMAL


ECHO ************************************************************************* CAJA 10 ************
ECHO ************************************************************************* VTA 10 *************
:JAHER_VTA10
CLS
MODE CON cols=40 lines=9
COLOR 07
ECHO.
ECHO  [************************************]
ECHO              - IMPORTANTE -
ECHO.
ECHO      CUANDO TERMINE POR COMPLETO EL 
ECHO       INSTALADOR SE AUTO REINICIARA 
ECHO              EL COMPUTADOR 
ECHO  [************************************] 
>nul ping -n 10 localhost  
MODE CON cols=40 lines=5  
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( VTA WIN 10)
DISM /Online /Enable-Feature /FeatureName:NetFx3 /All 
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( VTA WIN 10)
START /WAIT "NetFram3.5.0.exe" "NetFram3.5.0.exe"
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( VTA WIN 10)
NetFram4.8.1.exe /SILENT /VERYSILENT /NORESTART
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( ADM WIN 10)
powershell.exe -ep bypass -file EliAppWinApp.ps1
CLS
ECHO Instalando...
ECHO.
ECHO  * ********** ( VTA WIN 10)
Cursores.exe
CLS
ECHO Instalando...
ECHO.
ECHO  * ********** ( VTA WIN 10)
ECHO.
Wallpaper_JAHER.exe
CLS
ECHO Instalando...
ECHO.
ECHO  * ********** ( VTA WIN 10)
ECHO.
JAHER_NEW.deskthemepack
CLS
ECHO Instalando...
ECHO.
ECHO  * ********** ( VTA WIN 10)
ECHO.
START "JAHER_NEW.theme" "%localappdata%\Microsoft\Windows\Themes\JAHER_NEW\JAHER_NEW.theme"
CLS
ECHO Instalando...
ECHO.
ECHO  * ********** ( VTA WIN 10)
ECHO.
taskkill /f /im "SystemSettings.exe"
CLS
ECHO Instalando...
ECHO.
ECHO  * ********** ( VTA WIN 10)
COPY /D /V /Y "Escr\Calculator.lnk" "%Public%\desktop"
COPY /D /V /Y "Escr\Paint.lnk" "%Public%\desktop"
GOTO CONFVTA_10

:CONFVTA_10
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto CONFVTA_10_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto CONFVTA_10_64)
ECHO.


:CONFVTA_10_32
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
LibreOffice_32.msi /passive 
ECHO.
GOTO INSTALSTANDAR_NORMAL

:CONFVTA_10_64
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
LibreOffice_64.msi /passive 
ECHO.
GOTO INSTALSTANDAR_NORMAL



ECHO ************************************************************************* VTA 10 ************
ECHO ************************************************************************* ADM 10 ************

:JAHER_ADM10
CLS
MODE CON cols=40 lines=9
COLOR 07
ECHO.
ECHO  [************************************]
ECHO              - IMPORTANTE -
ECHO.
ECHO      CUANDO TERMINE POR COMPLETO EL 
ECHO       INSTALADOR SE AUTO REINICIARA 
ECHO              EL COMPUTADOR 
ECHO  [************************************] 
>nul ping -n 10 localhost    
MODE CON cols=40 lines=5 
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( CAJA WIN 10)
DISM /Online /Enable-Feature /FeatureName:NetFx3 /All
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( ADM WIN 10)
START /WAIT "NetFram3.5.0.exe" "NetFram3.5.0.exe"
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( ADM WIN 10)
NetFram4.8.1.exe /SILENT /VERYSILENT /NORESTART
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( ADM WIN 10)
powershell.exe -ep bypass -file EliAppWinApp.ps1
ECHO.
CLS
ECHO Instalando...
ECHO.
ECHO  * ******* ( ADM WIN 10)
Cursores.exe
CLS
ECHO Instalando...
ECHO.
ECHO  * ******* ( ADM WIN 10)
Wallpaper_JAHER.exe
CLS
ECHO Instalando...
ECHO.
ECHO  * ******* ( ADM WIN 10)
ECHO.
JAHER_NEW.deskthemepack
CLS
ECHO Instalando...
ECHO.
ECHO  * ********** ( VTA WIN 10)
ECHO.
START "JAHER_NEW.theme" "%localappdata%\Microsoft\Windows\Themes\JAHER_NEW\JAHER_NEW.theme"
CLS
ECHO Instalando...
ECHO.
ECHO  * ******* ( ADM WIN 10)
ECHO.
taskkill /f /im SystemSettings.exe
CLS
ECHO Instalando...
ECHO.
ECHO  * ******* ( ADM WIN 10)
ECHO.
taskkill /f /im msedge.exe
RD /S /Q "%localappdata%\Microsoft\Edge\User Data"
Edge_Fav.exe
CLS
ECHO Instalando...
ECHO.
ECHO  * ******* ( ADM WIN 10)
ECHO.
COPY /D /V /Y "Escr\Calculator.lnk" "%Public%\desktop"
COPY /D /V /Y "Escr\Paint.lnk" "%Public%\desktop"
DEL /F /S /Q "%Public%\desktop\MARCACION.RDP"
CLS
ECHO.
DEL /F /S /Q "%Public%\Documents\bookmark.htm"
COPY /D /V /Y "Link\bookmark.htm" "%Public%\Documents"
DEL /F /S /Q "%userprofile%\Favorites\Links\*.*"
COPY /D /V /Y "Link\bookmark.htm" "%userprofile%\Favorites\Links"
ECHO.
MD "C:\APPL"
ECHO.
COPY /D /V /Y "Link\Marcacion.ico" "C:\APPL"
COPY /D /V /Y "Link\marcacionL1.jnlp" "C:\APPL"
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%Public%\desktop\Marcacion.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\marcacionL1.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Marcacion.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
GOTO INSTALSTANDAR_NORMAL


ECHO ***************************************** ADM 10 *******************************************
ECHO ================================== INSTALADOR NORMAL ======================================


:INSTALSTANDAR_NORMAL
COLOR 03
MODE CON cols=65 lines=5 
CLS
ECHO.
ECHO Instalando...
ECHO.
PowerShell -NoProfile -ExecutionPolicy Bypass -Command "& {Start-Process PowerShell -ArgumentList '-NoProfile -ExecutionPolicy Bypass -File ""%~dp0.\rules.ps1""' -Verb RunAs}"
echo Rules should be included in Firewall.
echo.
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO ( Optimo Windows )
ECHO [== 1 %% ]
REGEDIT /S "Privaciti.reg"
ECHO.
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO ( Instalado JAVA )
ECHO [== 1 %% ]
REGEDIT /S "OptimoW10.reg"
REGEDIT /S "Impresoras.reg"
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO ( Instalado JAVA )
ECHO [====== 10 %% ]
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\security\exception.sites"
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\deployment.properties"
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO ( Instalado JAVA )
ECHO [======== 15 %% ]
Java_Conf.exe
CLS
ECHO Instalando...
ECHO.
ECHO ( K-Lite Codec )
ECHO [========== 17 %% ]
Codec_Pack.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /SP-
CLS
ECHO Instalando...
ECHO.
ECHO ( M. Visual C )
ECHO [========== 18 %% ]
VBCRedist_AIO_x86_x64.exe /SILENT /VERYSILENT /NORESTART
CLS
ECHO Instalando...
ECHO.
ECHO ( M. Visual C )
ECHO [========== 18 %% ]
MsiExec.exe /X{20097EC4-1DC2-402C-AFE1-3FF215D33C6E} /quiet
MsiExec.exe /X{20097EC4-1DC2-402C-AFE1-3FF215D33C6E} /q
start "" /WAIT "Sophos\SophosConnect.msi" /passive
CLS
ECHO Instalando...
ECHO.
ECHO  ( DirecX )
ECHO [=================== 22 %% ]
DirecX2010.exe
CLS
MODE CON cols=50 lines=5 
CLS
ECHO Instalando...
ECHO.
ECHO  ( M. VISUAL EXTRA)
ECHO [=========================== 25 %% ]
VBCRedist.exe /passive /norestart
CLS
RD /S /Q "C:\APPL"
MD "C:\APPL"
CLS
mode con cols=35 lines=4
ECHO  [==============================]
ECHO            CONFIGURANDO
ECHO  [==============================]
ECHO.
ASSOC .pdf=MSEdgePDF
ASSOC .htm=MSEdgeHTM
ASSOC .html=MSEdgeHTML
ASSOC .mht=MSEdgeMHT
MD "C:\APPL"
MD "C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar\JAHER"
MD "%ProgramData%\Microsoft\Windows\Start Menu\Programs\JAHER"
ECHO.
reg add "HKCU\Software\Microsoft\Internet Explorer\Main" /v "Start Page" /t REG_SZ /d "https://www.jaher.com.ec/" /f
ECHO.
COPY /D /V /Y "Link\stock_L1.jnlp" "C:\APPL" 
COPY /D /V /Y "Link\stock_L2.jnlp" "C:\APPL" 
COPY /D /V /Y "Link\stock_S1.jnlp" "C:\APPL"
COPY /D /V /Y "Link\marcacionL1.jnlp" "C:\APPL"
COPY /D /V /Y "Link\marcacionL2.jnlp" "C:\APPL"
COPY /D /V /Y "Link\marcacionS1.jnlp" "C:\APPL"
COPY /D /V /Y "Link\Marcacion.ico" "C:\APPL"
COPY /D /V /Y "Link\Stock_logook.ico" "C:\APPL"
COPY /D /V /Y "Link\efigie.jnlp" "C:\APPL"
COPY /D /V /Y "Link\Stock_logook.ico" "C:\APPL"  
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%Public%\desktop\STOCK_JAHER.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\efigie.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Stock_logook.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%ProgramData%\Microsoft\Windows\Start Menu\Programs\JAHER\STOCK_JAHER.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\efigie.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Stock_logook.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
Java_Conf.exe
ECHO.
GOTO MOZI_RUN

:MOZI_RUN
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto MOZI_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto MOZI_64)

:MOZI_32
COLOR 03
MODE CON cols=65 lines=5 
CLS
ECHO Instalando...
ECHO.
ECHO  ( JAVA 32BIT )
ECHO [============================= 29 %% ]
Java_32.exe /s
CLS
ECHO Instalando...
ECHO.
ECHO  ( Mozilla )
ECHO [============================= 29 %% ]
Firefox_32.msi -ms
CLS
ECHO Instalando...
ECHO.
ECHO  ( Mozilla M. )
ECHO [============================== 30 %% ]
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ( Mozilla M. )
ECHO [================================ 31 %% ]
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ( Mozilla M. )
ECHO [================================== 33 %% ]
START FirefoxMarcadores_32 FirefoxMarcadores_32.exe /REALTIME
ECHO.
%SystemRoot%/SysWOW32/OneDriveSetup.exe /uninstall
CLS  
ECHO Instalando...
ECHO.
ECHO  ( Adobe Reader )
ECHO [==================================== 35 %% ]
AdbeRdr.exe /sPB
CLS
ECHO Instalando...
ECHO.
ECHO  ( Adobe Pack )
ECHO [====================================== 38 %% ]
AdbeRdr_FontPack.msi /passive
CLS
ECHO Instalando...
ECHO.
ECHO  ( Adobe Pack )
ECHO [======================================== 40 %% ]
REGEDIT /S "AdobeConfig.reg"
GOTO CONTI

:MOZI_64
COLOR 03
MODE CON cols=65 lines=5 
CLS
ECHO Instalando...
ECHO.
ECHO  ( JAVA 64BIT )
ECHO [============================= 29 %% ]
Java_64.exe /s
CLS
ECHO Instalando...
ECHO.
ECHO  ( Mozilla )
ECHO [============================= 29 %% ]
Firefox_64.msi -ms
CLS
ECHO Instalando...
ECHO.
ECHO  ( Mozilla M. )
ECHO [============================== 30 %% ]
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ( Mozilla M. )
ECHO [================================ 31 %% ]
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ( Mozilla M. )
ECHO [================================== 33 %% ]
START FirefoxMarcadores_64 FirefoxMarcadores_64.exe /REALTIME
ECHO.
%SystemRoot%/SysWOW32/OneDriveSetup.exe /uninstall
CLS  
ECHO Instalando...
ECHO.
ECHO  ( Adobe Reader )
ECHO [==================================== 35 %% ]
AdbeRdr.exe /sPB
CLS
ECHO Instalando...
ECHO.
ECHO  ( Adobe Pack )
ECHO [====================================== 38 %% ]
AdbeRdr_FontPack.msi /passive
CLS
ECHO Instalando...
ECHO.
ECHO  ( Adobe Pack )
ECHO [======================================== 40 %% ]
REGEDIT /S "AdobeConfig.reg"
GOTO CONTI

:CONTI
CLS
ECHO Instalando...
ECHO.
ECHO  ( WinRAR. )
ECHO [============================================== 80 %% ]
WinRAR.exe
CLS
ECHO Instalando...
ECHO.
ECHO  ( EXTRAS. )
ECHO [================================================ 1f %% ]
[-HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run]
REG DELETE HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run /f
COPY /D /V /Y "Borrar_Temp.bat" "C:\Windows"
schtasks /Create /TN "Depurar" /SC ONLOGON /TR "%SYSTEMROOT%\Borrar_Temp.bat" /RL HIGHEST /F
CLS
ECHO.
assoc .pdf=AcroExch.Document.DC
assoc .url=InternetShortcut
ECHO.
REM disable java update by policy 
reg add "HKLM\SOFTWARE\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T
REG_DWORD /D 0 /F
if defined programfiles(x86) reg add "HKLM\SOFTWARE\Wow6432Node\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T REG_DWORD /D 0 /F
REM Remove java update scheduler
REG DELETE "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v
"SunJavaUpdateSched" /f
if defined programfiles(x86) reg delete "HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run" /v "SunJavaUpdateSched" /f
REM NoSoloHacking.info
REM kill java updater if started
taskkill /IM jucheck.exe /F
taskkill IM juscheck.exe /F
ECHO.
Java_Conf.exe
ECHO.
GOTO FIR_DELMAINTENCE

ECHO ================================== INSTALADOR NORMAL ======================================
ECHO ================================== ELININAR MANTENCE FIREFOX ==============================

:FIR_DELMAINTENCE
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto FIRVT_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto FIRVT_64)
ECHO.

:FIRVT_32
CLS
ECHO Instalando...
ECHO.
ECHO  ( Mozilla U. )
ECHO [================================================== 100 %% ]
"%PROGRAMFILES%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
GOTO TIG_ALL

:FIRVT_64
CLS
ECHO Instalando...
ECHO.
ECHO  ( Mozilla U. )
ECHO [================================================== 100 %% ]
"%PROGRAMFILES(X86)%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
GOTO TIG_ALL

ECHO ================================== ELININAR MANTENCE FIREFOX ==============================

ECHO ================================== I N S T A L A D O R =====================================



ECHO           [----------------------------------------------------(MENU_1) 

:Programas1
title                               UTILITARIOS JAHER
CLS
COLOR 0B
mode con cols=80 lines=27
ECHO           [-----------------------------------------------------------] 
ECHO                            MENU INSTALACION PROGRAMA
ECHO           [-----------------------------------------------------------] 
ECHO                             PROGRAMAS E X T R A S - 1
ECHO                       ----------------------------------------------
ECHO               " 1 "  Para    Instalar WinRAR.
ECHO                       ----------------------------------------------
ECHO               " 2 "  Para    Instalando Mozilla.
ECHO                       ----------------------------------------------
ECHO               " 3 "  Para    Instalar Java.
ECHO                       ----------------------------------------------
ECHO               " 4 "  Para    Instalando UPDATE TOTAL.
ECHO                       ----------------------------------------------
ECHO               " 5 "  Para    Reparar Update OFFICE 2013
ECHO                       ----------------------------------------------
ECHO               " 6 "  Para    Instalar Cursores.
ECHO                       ==============================================
ECHO               " 7 "  Para    Menu Principal.
ECHO               " 8 "  Para    Menu Anterior.
ECHO               " 9 "  Para    Menu Siguiente.
ECHO                       ==============================================
ECHO               " 10 "  Para    Salir.
ECHO           [-----------------------------------------------------------]
ECHO.
set /p extr=  Ingresa el numero a tu eleccion :   
ECHO. 
if %extr%==1 GOTO EX101
if %extr%==2 GOTO EX102
if %extr%==3 GOTO EX103
if %extr%==4 GOTO EX104
if %extr%==5 GOTO EX105
if %extr%==6 GOTO EX106
if %extr%==7 GOTO ZONAS
if %extr%==8 GOTO Programas7
if %extr%==9 GOTO Programas2
if %extr%==10 GOTO Salir
if %extr%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO Programas1



:Programas2
title                               UTILITARIOS JAHER
CLS
COLOR 0B
mode con cols=80 lines=27
ECHO           [-----------------------------------------------------------] 
ECHO                            MENU INSTALACION PROGRAMA
ECHO           [-----------------------------------------------------------] 
ECHO                             PROGRAMAS E X T R A S - 2
ECHO                       ----------------------------------------------
ECHO               " 1 "  Para    Instalar Autoborrado Temporales.
ECHO                       ----------------------------------------------
ECHO               " 2 "  Para    Instalar Adobe Acrobat DC.
ECHO                       ----------------------------------------------
ECHO               " 3 "  Para    Instalar Mozilla Thunderbird.
ECHO                       ----------------------------------------------
ECHO               " 4 "  Para    Instalar Visual Studio C++.
ECHO                       ----------------------------------------------
ECHO               " 5 "  Para    Instalar TightVNC.
ECHO                       ----------------------------------------------
ECHO               " 6 "  Para    EXTRAER LA LICENCIA DE WINDOWS 10 
ECHO                       ==============================================
ECHO               " 7 "  Para    Menu Principal.
ECHO               " 8 "  Para    Menu Anterior.
ECHO               " 9 "  Para    Menu Siguiente.
ECHO                       ==============================================
ECHO               " 10 "  Para    Salir.
ECHO           [-----------------------------------------------------------]
ECHO.
set /p maspab=  Ingresa el numero a tu eleccion :    
ECHO.
if %maspab%==1 GOTO EX201
if %maspab%==2 GOTO EX202
if %maspab%==3 GOTO EX203
if %maspab%==4 GOTO EX204
if %maspab%==5 GOTO EX205
if %maspab%==6 GOTO EX206
if %maspab%==7 GOTO ZONAS
if %maspab%==8 GOTO Programas1
if %maspab%==9 GOTO Programas3
if %maspab%==10 GOTO Salir
if %maspab%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO Programas2



:Programas3
title                               UTILITARIOS JAHER
CLS
COLOR 0B
mode con cols=80 lines=27
ECHO           [-----------------------------------------------------------] 
ECHO                            MENU INSTALACION PROGRAMA
ECHO           [-----------------------------------------------------------] 
ECHO                             PROGRAMAS E X T R A S - 3
ECHO                       ----------------------------------------------
ECHO               " 1 "  Para    Instalar LibreOffice.
ECHO                       ----------------------------------------------
ECHO               " 2 "  Para    RESTAURACION WINDOW
ECHO                       ----------------------------------------------
ECHO               " 3 "  Para    Instalar NETFramework.
ECHO                       ----------------------------------------------
ECHO               " 4 "  Para    Wallpapers JAHER.
ECHO                       ----------------------------------------------
ECHO               " 5 "  Para    Informacion del COMPUTADOR. 
ECHO                       ----------------------------------------------
ECHO               " 6 "  Para    FAVORITOS EN MICROSOFT EDGE
ECHO                       ==============================================
ECHO               " 7 "  Para    Menu Principal.
ECHO               " 8 "  Para    Menu Anterior.
ECHO               " 9 "  Para    Menu Siguiente.
ECHO                       ==============================================
ECHO               " 10 "  Para    Salir.
ECHO           [-----------------------------------------------------------]
ECHO.
set /p maspa=  Ingresa el numero a tu eleccion :    
ECHO.
if %maspa%==1 GOTO EX301
if %maspa%==2 GOTO EX302
if %maspa%==3 GOTO EX303
if %maspa%==4 GOTO EX304
if %maspa%==5 GOTO EX305
if %maspa%==6 GOTO EX306
if %maspa%==7 GOTO ZONAS
if %maspa%==8 GOTO Programas2
if %maspa%==9 GOTO Programas4
if %maspa%==10 GOTO Salir
if %maspa%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO Programas3


:Programas4
title                               UTILITARIOS JAHER
CLS
COLOR 0B
mode con cols=80 lines=27
ECHO           [-----------------------------------------------------------] 
ECHO                            MENU INSTALACION PROGRAMA
ECHO           [-----------------------------------------------------------] 
ECHO                             PROGRAMAS E X T R A S - 4
ECHO                       ----------------------------------------------
ECHO               " 1 "  Para    EVITAR SOLICITUD PASSWORD
ECHO                       ----------------------------------------------
ECHO               " 2 "  Para    ACCESOS DIRECTOS CAJA - ESCRITORIO
ECHO                       ----------------------------------------------
ECHO               " 3 "  Para    ACCESOS DIRECTOS ADM - ESCRITORIO
ECHO                       ----------------------------------------------
ECHO               " 4 "  Para    ACCESOS DIRECTOS VTA - ESCRITORIO
ECHO                       ----------------------------------------------
ECHO               " 5 "  Para    DESINSTALADOR DE PROGRAMAS. 
ECHO                       ----------------------------------------------
ECHO               " 6 "  Para    DESINSTALADOR DE OFFICE.
ECHO                       ==============================================
ECHO               " 7 "  Para    Menu Principal.
ECHO               " 8 "  Para    Menu Anterior.
ECHO               " 9 "  Para    Menu Siguiente.
ECHO                       ==============================================
ECHO               " 10 "  Para    Salir.
ECHO           [-----------------------------------------------------------]
ECHO.
set /p maspab=  Ingresa el numero a tu eleccion :    
ECHO.
if %maspab%==1 GOTO EX401
if %maspab%==2 GOTO EX402
if %maspab%==3 GOTO EX403
if %maspab%==4 GOTO EX404
if %maspab%==5 GOTO EX405
if %maspab%==6 GOTO EX406
if %maspab%==7 GOTO ZONAS
if %maspab%==8 GOTO Programas3
if %maspab%==9 GOTO Programas5
if %maspab%==10 GOTO Salir
if %maspab%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO Programas4

:Programas5
title                               UTILITARIOS JAHER
CLS
COLOR 0B
mode con cols=80 lines=27
ECHO           [-----------------------------------------------------------] 
ECHO                            MENU INSTALACION PROGRAMA
ECHO           [-----------------------------------------------------------] 
ECHO                             PROGRAMAS E X T R A S - 5
ECHO                       ----------------------------------------------
ECHO               " 1 "  Para    REPARADOR RED E IMPRESORAS
ECHO                       ----------------------------------------------
ECHO               " 2 "  Para    Instalar GPEDIT EN WINDOWS HOME
ECHO                       ----------------------------------------------
ECHO               " 3 "  Para    Reparar WINDOWS
ECHO                       ----------------------------------------------
ECHO               " 4 "  Para    REPARADOR DE PST (OutLook)
ECHO                       ----------------------------------------------
ECHO               " 5 "  Para    OPTIMIZADOR WINDOWS 10
ECHO                       ----------------------------------------------
ECHO               " 6 "  Para    INSTALACION SOPHOS 
ECHO                       ==============================================
ECHO               " 7 "  Para    Menu Principal.
ECHO               " 8 "  Para    Menu Anterior.
ECHO               " 9 "  Para    Menu Siguiente.
ECHO                       ==============================================
ECHO               " 10 "  Para    Salir.
ECHO           [-----------------------------------------------------------]
ECHO.
set /p maspab=  Ingresa el numero a tu eleccion :    
ECHO.
if %maspab%==1 GOTO EX501
if %maspab%==2 GOTO EX502
if %maspab%==3 GOTO EX503
if %maspab%==4 GOTO EX504
if %maspab%==5 GOTO EX505
if %maspab%==6 GOTO EX506
if %maspab%==7 GOTO ZONAS
if %maspab%==8 GOTO Programas4
if %maspab%==9 GOTO Programas6
if %maspab%==10 GOTO Salir
if %maspab%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO Programas5


:Programas6
title                               UTILITARIOS JAHER
CLS
COLOR 0B
mode con cols=80 lines=27
ECHO           [-----------------------------------------------------------] 
ECHO                            MENU INSTALACION PROGRAMA
ECHO           [-----------------------------------------------------------] 
ECHO                             PROGRAMAS E X T R A S - 6
ECHO                       ----------------------------------------------
ECHO               " 1 "  Para    Reparar TEXTO
ECHO                       ----------------------------------------------
ECHO               " 2 "  Para    Instalar (( GLPI )) - (PASO A PASO)
ECHO                       ----------------------------------------------
ECHO               " 3 "  Para    Eliminar APPS Windows
ECHO                       ----------------------------------------------
ECHO               " 4 "  Para    Instalar CrystalDiskInfo
ECHO                       ----------------------------------------------
ECHO               " 5 "  Para    Eliminar JAVA
ECHO                       ----------------------------------------------
ECHO               " 6 "  Para    Instalar FAVORITOS EDGE
ECHO                       ==============================================
ECHO               " 7 "  Para    Menu Principal.
ECHO               " 8 "  Para    Menu Anterior.
ECHO               " 9 "  Para    Menu Siguiente.
ECHO                       ==============================================
ECHO               " 10 "  Para    Salir.
ECHO           [-----------------------------------------------------------]
ECHO.
set /p maspab=  Ingresa el numero a tu eleccion :    
ECHO.
if %maspab%==1 GOTO EX601
if %maspab%==2 GOTO EX602
if %maspab%==3 GOTO EX603
if %maspab%==4 GOTO EX604
if %maspab%==5 GOTO EX605
if %maspab%==6 GOTO EX606
if %maspab%==7 GOTO ZONAS
if %maspab%==8 GOTO Programas5
if %maspab%==9 GOTO Programas7
if %maspab%==10 GOTO Salir
if %maspab%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO Programas6

:Programas7
title                               UTILITARIOS JAHER
CLS
COLOR 0B
mode con cols=80 lines=27
ECHO           [-----------------------------------------------------------] 
ECHO                            MENU INSTALACION PROGRAMA
ECHO           [-----------------------------------------------------------] 
ECHO                             PROGRAMAS E X T R A S - 7
ECHO                       ----------------------------------------------
ECHO               " 1 "  Para    Instalando MARCACION ZONA 1
ECHO                       ----------------------------------------------
ECHO               " 2 "  Para    Instalando MARCACION ZONA 2
ECHO                       ----------------------------------------------
ECHO               " 3 "  Para    Instalando MARCACION SOLARIS
ECHO                       ----------------------------------------------
ECHO               " 4 "  Para    Que (Net Framewords) tengo...
ECHO                       ----------------------------------------------
ECHO               " 5 "  Para    REPARAR HIPERVINCULOS OUTLOOK
ECHO                       ----------------------------------------------
ECHO               " 6 "  Para    K-LITE CODEC
ECHO                       ==============================================
ECHO               " 7 "  Para    Menu Principal.
ECHO               " 8 "  Para    Menu Anterior.
ECHO               " 9 "  Para    Menu Siguiente.
ECHO                       ==============================================
ECHO               " 10 "  Para    Salir.
ECHO           [-----------------------------------------------------------]
ECHO.
set /p maspab=  Ingresa el numero a tu eleccion :    
ECHO.
if %maspab%==1 GOTO EX701
if %maspab%==2 GOTO EX702
if %maspab%==3 GOTO EX703
if %maspab%==4 GOTO EX704
if %maspab%==5 GOTO EX705
if %maspab%==6 GOTO EX706
if %maspab%==7 GOTO ZONAS
if %maspab%==8 GOTO Programas6
if %maspab%==9 GOTO Programas1
if %maspab%==10 GOTO Salir
if %maspab%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO Programas7


:EX101
WinRAR.exe
ECHO.
GOTO Programas1


:EX102
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto MOZ32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto MOZ64)
ECHO.

:MOZ32
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 50%% ( MOZILLA UNINSTAL. )
ECHO --------------------------------------------
START /HIGH /WAIT "helper.exe" "%PROGRAMFILES%\Mozilla Firefox\uninstall\helper.exe" /s
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( Mozilla M. )
ECHO --------------------------------------------
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 100%% ( Mozilla M. )
ECHO --------------------------------------------
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
GOTO MOZ_MENU

:MOZ64
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 50%% ( MOZILLA UNINSTAL. )
ECHO --------------------------------------------
START /HIGH /WAIT "helper.exe" "%PROGRAMFILES(X86)%\Mozilla Firefox\uninstall\helper.exe" /s
START /HIGH /WAIT "helper.exe" "C:\Program Files\Mozilla Firefox\uninstall\helper.exe" /s
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( Mozilla M. )
ECHO --------------------------------------------
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 100%% ( Mozilla M. )
ECHO --------------------------------------------
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
GOTO MOZ_MENU

:MOZ_MENU
if %PROCESSOR_ARCHITECTURE%==x86 (goto MOZILLA32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto MOZILLA64)

:MOZILLA32
CLS
Color 03
mode con cols=35 lines=8
ECHO.
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO      (( Mozilla Firefox ))
ECHO                           (06)
ECHO  [=============================]
Firefox_32.msi -ms
CLS
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO      (( Mozilla Firefox ))
ECHO                           (05)
ECHO  [=============================]
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO      (( Mozilla Firefox ))
ECHO                           (04)
ECHO  [=============================]
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO.
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO      (( Mozilla Firefox ))
ECHO                           (03)
ECHO  [=============================]
START FirefoxMarcadores_32 FirefoxMarcadores_32.exe /REALTIME
ECHO.
GOTO FIR_DELM

:MOZILLA64
CLS
Color 03
mode con cols=35 lines=8
ECHO.
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO      (( Mozilla Firefox ))
ECHO                           (06)
ECHO  [=============================]
Firefox_64.msi -ms
CLS
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO      (( Mozilla Firefox ))
ECHO                           (05)
ECHO  [=============================]
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO      (( Mozilla Firefox ))
ECHO                           (04)
ECHO  [=============================]
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO.
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO      (( Mozilla Firefox ))
ECHO                           (03)
ECHO  [=============================]
START FirefoxMarcadores_64 FirefoxMarcadores_64.exe /REALTIME
ECHO.
GOTO FIR_DELM

:FIR_DELM
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto FIRVTD_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto FIRVTD_64)
ECHO.

:FIRVTD_32
Color 03
mode con cols=35 lines=8
ECHO.
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO      (( Mozilla Firefox ))
ECHO                           (01)
ECHO  [=============================]
"%PROGRAMFILES%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
ECHO.
GOTO Programas1

:FIRVTD_64
Color 03
mode con cols=35 lines=8
ECHO.
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO      (( Mozilla Firefox ))
ECHO                           (01)
ECHO  [=============================]
"%PROGRAMFILES(X86)%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
ECHO.
GOTO Programas1



:EX103
CLS
Color 03
mode con cols=35 lines=6
CLS
ECHO  [=============================]
ECHO    J A V A
ECHO.
ECHO                 (Desinstalando)
ECHO  [=============================]
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180241f0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180241f0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180261f0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180261f0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180271f0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180271f0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180281F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180281F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180291F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180291F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180301F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180301F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180311F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180311F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180321F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180321F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180321F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180321F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180331F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180331F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180331F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180331F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180333F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180333F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180333F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180333F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180341F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180341F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180341F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180341F0} /q
ECHO.
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180351F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180351F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180351F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180351F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180361F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180361F0} /q
ECHO.
MsiExec.exe /X{71124AE4-039E-4CA4-87B4-2F32180371F0} /quiet
MsiExec.exe /X{71124AE4-039E-4CA4-87B4-2F32180371F0} /q
ECHO.
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F32180381F0} /quiet
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F32180381F0} /q
ECHO.
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F64180381F0} /quiet
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F64180381F0} /q
ECHO.
MsiExec.exe /X{71024AE4-039E-4CA4-87B4-2F32180401F0} /quiet
MsiExec.exe /X{71024AE4-039E-4CA4-87B4-2F64180401F0} /q
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto JAV_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto JAV_64)

:JAV_32
CLS
ECHO  [=============================]
ECHO    J A V A
ECHO.
ECHO                         (32Bit)
ECHO  [=============================]
Java_32.exe /s
CLS
ECHO  [=============================]
ECHO    J A V A
ECHO.
ECHO                         (32Bit)
ECHO  [=============================]
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\security\exception.sites"
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\deployment.properties"
CLS
ECHO  [=============================]
ECHO    J A V A
ECHO.
ECHO                         (32Bit)
ECHO  [=============================]
Java_Conf.exe
ECHO.
REM disable java update by policy 
reg add "HKLM\SOFTWARE\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T
REG_DWORD /D 0 /F
if defined programfiles(x86) reg add "HKLM\SOFTWARE\Wow6432Node\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T REG_DWORD /D 0 /F
REM Remove java update scheduler
REG DELETE "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v
"SunJavaUpdateSched" /f
if defined programfiles(x86) reg delete "HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run" /v "SunJavaUpdateSched" /f
REM NoSoloHacking.info
REM kill java updater if started
taskkill /IM jucheck.exe /F
taskkill IM juscheck.exe /F
GOTO Programas1

:JAV_64
CLS
ECHO  [=============================]
ECHO    J A V A
ECHO.
ECHO                         (64Bit)
ECHO  [=============================]
Java_64.exe /s
CLS
ECHO  [=============================]
ECHO    J A V A
ECHO.
ECHO                         (64Bit)
ECHO  [=============================]
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\security\exception.sites"
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\deployment.properties"
CLS
ECHO  [=============================]
ECHO    J A V A
ECHO.
ECHO                         (64Bit)
ECHO  [=============================]
Java_Conf.exe
ECHO.
REM disable java update by policy 
reg add "HKLM\SOFTWARE\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T
REG_DWORD /D 0 /F
if defined programfiles(x86) reg add "HKLM\SOFTWARE\Wow6432Node\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T REG_DWORD /D 0 /F
REM Remove java update scheduler
REG DELETE "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v
"SunJavaUpdateSched" /f
if defined programfiles(x86) reg delete "HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run" /v "SunJavaUpdateSched" /f
REM NoSoloHacking.info
REM kill java updater if started
taskkill /IM jucheck.exe /F
taskkill IM juscheck.exe /F
GOTO Programas1


:EX104
taskkill /f /im explorer.exe
CLS
color 0E
MODE CON cols=100 lines=8
title                                           =  MEG@-PC  =
ECHO. 
ECHO                                        I M P O R T A N T E
ECHO. 
ECHO                          ( AL TERMINAR EL PROCESO SE REINICIA EL EQUIPO )                       
ECHO                    [----------------------------------------------------------]
TIMEOUT /T 05 
GOTO RUNUPT

:RUNUPT
CLS
color 03
mode con cols=100 lines=30
title                                           =  MEG@-PC  =
ECHO. 
ECHO                                       UPDATE TOTAL SOFTWARE PC 
ECHO                                    ( REQUIERE ACCESO A INTERNET )                       
ECHO                    [----------------------------------------------------------]
ECHO.
ECHO.
REM Comando para solicitar derechos elevados
NET SESSION >nul 2>&1
IF %ERRORLEVEL% EQU 0 (
    goto gotAdmin
) else (
    powershell -Command "Start-Process cmd -ArgumentList '/c %~nx0' -Verb RunAs"
    goto :eof
)

:gotAdmin
REM Ejecutar winget upgrade --all
winget upgrade --all
CLS
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\security\exception.sites"
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\deployment.properties"
CLS
Java_Conf.exe
ECHO.
REM disable java update by policy 
reg add "HKLM\SOFTWARE\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T
REG_DWORD /D 0 /F
if defined programfiles(x86) reg add "HKLM\SOFTWARE\Wow6432Node\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T REG_DWORD /D 0 /F
REM Remove java update scheduler
REG DELETE "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v
"SunJavaUpdateSched" /f
if defined programfiles(x86) reg delete "HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run" /v "SunJavaUpdateSched" /f
REM NoSoloHacking.info
REM kill java updater if started
taskkill /IM jucheck.exe /F
taskkill IM juscheck.exe /F
CLS
cleanmgr /sagerun
CLS
goto REINICIAR

:EX1044
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto PROKEY32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto PROKEY64)
ECHO.

:PROKEY32
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO           (( Produkey ))
ECHO  [=============================]
ProduKey.exe /S /NCRC
ECHO.
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO            (( RUN ))
ECHO  [=============================]
START /WAIT "ProduKey" "%PROGRAMFILES%\NirSoft\ProduKey\ProduKey.exe"
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( UNINSTAL ))
ECHO  [=============================]
"%PROGRAMFILES%\NirSoft\ProduKey\uninst.exe" /S /NCRC
CLS
goto Programas1

:PROKEY64
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO           (( Produkey ))
ECHO  [=============================]
ProduKey.exe /S /NCRC
ECHO.
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO            (( RUN ))
ECHO  [=============================]
START /WAIT "ProduKey" "%PROGRAMFILES(x86)%\NirSoft\ProduKey\ProduKey.exe"
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( UNINSTAL ))
ECHO  [=============================]
"%PROGRAMFILES(x86)%\NirSoft\ProduKey\uninst.exe" /S /NCRC
CLS
goto Programas1



:EX105
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO         (( OFFICE 2013 ))
ECHO  [=============================]
@ECHO.
"C:\Program Files\Microsoft Office 15\ClientX64\officec2rclient.exe" /update user updatetoversion=15.0.5571.1000
ECHO.
CLS
GOTO Salir




:EX106
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO       (( C U R S O R E S ))
ECHO  [=============================]
Cursores.exe
CLS
GOTO Programas1



ECHO           [----------------------------------------------------(MENU_1) 
ECHO           [----------------------------------------------------(MENU_2) 

:EX201
Color 1f
mode con cols=80 lines=18
ECHO          [==========================================================]
ECHO                               I N S T A L A N D O
ECHO.
ECHO                           (( BORRADOR TEMPORALES ))
ECHO.
ECHO             " 1 "   Para    Instalar - Borrar Temporales - 
ECHO                        ------------------
ECHO             " 2 "   Para    Eliminar - Borrar Temporales - 
ECHO                           ------------------
ECHO             " 3 "   Para    Menu Anterior.
ECHO                           ------------------
ECHO             " 4 "   Para    Menu Principal.
ECHO                           ------------------
ECHO             " 5 "   Para    Salir
ECHO.
ECHO          [==========================================================]
set /p wp=Ingresa el numero a su eleccion :    
ECHO          [==========================================================]
if %wp%==1 GOTO INSTA_BORRAR
if %wp%==2 GOTO BORRAR_BORRAR
if %wp%==3 GOTO Programas2
if %wp%==4 GOTO ZONAS
if %wp%==5 GOTO Salir
if %wp%==0 exit else GOTO error

:INSTA_BORRAR
CLS
Color 03
mode con cols=35 lines=5
ECHO.
ECHO  [==============================]
ECHO     ( AUTO BORRAR TEMPORALES )
ECHO  [==============================]
DEL /F /S /Q "%SYSTEMROOT%\Btemp.cmd"
DEL /F /S /Q "%SYSTEMROOT%\Borrar_Temp.bat"
REG DELETE "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v Btemp /f
REG DELETE "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v Borrar_Temp /f
REG DELETE "HKCR\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v Btemp /f
REG DELETE "HKCR\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v Borrar_Temp /f
[-HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run]
COPY /D /V /Y "Borrar_Temp.bat" "C:\Windows"
schtasks /Create /TN "Depurar" /SC ONLOGON /TR "%SYSTEMROOT%\Borrar_Temp.bat" /RL HIGHEST /F
regedit.exe /s "Borrar_Temp.reg"
ECHO.
GOTO Programas2

:BORRAR_BORRAR
CLS
Color 03
mode con cols=35 lines=5
ECHO.
ECHO  [==============================]
ECHO     ( ELIMINAR BORRAR TEMPORALES )
ECHO  [==============================]
REG DELETE "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v Btemp /f
REG DELETE "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v Borrar_Temp /f
REG DELETE "HKCR\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v Btemp /f
REG DELETE "HKCR\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v Borrar_Temp /f
[-HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run]
schtasks /Delete /TN "Depurar" /F
DEL /F /S /Q "%SYSTEMROOT%\Btemp.cmd"
DEL /F /S /Q "%SYSTEMROOT%\Borrar_Temp.bat"
ECHO.
GOTO Programas2


:EX202
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto ADOB_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto ADOB_64)
ECHO.

:ADOB_32
CLS
Color C
mode con cols=35 lines=6
ECHO  [=============================]
ECHO       D E S I N S T A L A R
ECHO.
ECHO       (( Adobe Acrobat DC ))
ECHO  [=============================]
TASKKILL /F /IM Teams.exe
msiexec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC0F074E4100} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-FFFF-7B44-AC0F074E4100} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC13154E5A00} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC15014EA700} /quiet
MsiExec.exe /uninstall {AC76BA86-1034-1033-7760-BC15014EA700} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
ECHO.
MsiExec.exe /uninstall {AC76BA86-1034-1033-7760-BC15014EA700} /quiet
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO       (( Adobe Acrobat DC ))
ECHO  [=============================]
AdbeRdr.exe /sPB
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO       (( Adobe Acrobat DC ))
ECHO  [=============================]
AdbeRdr_FontPack.msi /passive
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO       (( Adobe Acrobat DC ))
ECHO  [=============================]
REGEDIT /S "AdobeConfig.reg"
CLS
GOTO Programas2


:ADOB_64
CLS
Color C
mode con cols=35 lines=6
ECHO  [=============================]
ECHO       D E S I N S T A L A R
ECHO.
ECHO       (( Adobe Acrobat DC ))
ECHO  [=============================]
TASKKILL /F /IM Teams.exe
msiexec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC0F074E4100} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-FFFF-7B44-AC0F074E4100} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC13154E5A00} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC15014EA700} /quiet
MsiExec.exe /uninstall {AC76BA86-1034-1033-7760-BC15014EA700} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
ECHO.
MsiExec.exe /uninstall {AC76BA86-1034-1033-7760-BC15014EA700} /quiet
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO       (( Adobe Acrobat DC ))
ECHO  [=============================]
AdbeRdr.exe /sPB
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO       (( Adobe Acrobat DC ))
ECHO  [=============================]
AdbeRdr_FontPack.msi /passive
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO       (( Adobe Acrobat DC ))
ECHO  [=============================]
REGEDIT /S "AdobeConfig.reg"
CLS
GOTO Programas2



:EX203
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto TUN32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto TUN64)
ECHO.

:TUN32
CLS
Color 03
mode con cols=35 lines=4
ECHO  [=============================]
ECHO            Thunderbird
ECHO  [=============================]
Thunderbird_32bit.exe -ms
ECHO.
"%PROGRAMFILES%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
ECHO.
goto Programas2



:TUN64
CLS
Color 03
mode con cols=35 lines=4
ECHO  [=============================]
ECHO            Thunderbird
ECHO  [=============================]
Thunderbird_64bit.exe -ms
ECHO.
"%PROGRAMFILES(X86)%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
ECHO.
goto Programas2



:EX204
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto VISUALR32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto VISUALR64)
ECHO.

:VISUALR32
CLS
Color 03
mode con cols=35 lines=8
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          VISUAL SERVICES  32Bit
ECHO  [=============================]
VBCRedist_AIO_x86_x64.exe /SILENT /VERYSILENT /NORESTART
CLS
Color 03
mode con cols=35 lines=8
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          VISUAL SERVICES  32Bit
ECHO  [=============================]
VBCRedist_32bit.exe /passive /norestart
CLS
GOTO Programas2



:VISUALR64
CLS
Color 03
mode con cols=35 lines=8
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          VISUAL SERVICES  64Bit
ECHO  [=============================]
VBCRedist_AIO_x86_x64.exe /SILENT /VERYSILENT /NORESTART
CLS
Color 03
mode con cols=35 lines=8
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          VISUAL SERVICES  64Bit
ECHO  [=============================]
VBCRedist_64bit.exe /passive /norestart
CLS
GOTO Programas2


:EX205
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto VN_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto VN_64)
ECHO.

:VN_32
CLS
Color 03
mode con cols=35 lines=7
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO           (( TightVNC ))
ECHO                         (32Bit)
ECHO  [=============================]
START /WAIT TightVNC32bit.msi
CLS
goto Programas2



:VN_64
CLS
Color 03
mode con cols=35 lines=7
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO           (( TightVNC ))
ECHO                         (64Bit)
ECHO  [=============================]
START /WAIT TightVNC64bit.msi
CLS
goto Programas2


:EX206
CLS
Color B
mode con cols=90 lines=15
ECHO  [=======================================================]
ECHO                   DETALLES DEL COMPUTADOR
systeminfo | find /i "Sistema Operativo"
wmic path softwarelicensingservice get oa3xoriginalproductkey
PAUSE
CLS
GOTO Programas2

ECHO           [----------------------------------------------------(MENU_2) 
ECHO           [----------------------------------------------------(MENU_3) 


:EX301
CLS
ECHO Instalando...
ECHO.
ECHO  **** 40%% ( LibreOffice UNINSTAL. )
ECHO --------------------------------------------
msiexec.exe /uninstall {235CBF9C-D3E1-4703-A729-7AC6F101C15E} /quiet
msiexec.exe /uninstall {4DEFF29A-B682-4B51-B1DD-F040F1618B26} /quiet
msiexec.exe /uninstall {6110D2CC-70B4-415E-AF5A-7BB496AB264B} /quiet
msiexec.exe /uninstall {953D746F-FA08-462B-A66E-7A7FFF322580} /quiet
msiexec.exe /uninstall {50EB7256-5011-4480-8E89-B3AE0C30AFF0} /quiet
msiexec.exe /uninstall {4DACF7A7-C851-4943-A63D-3CAE495C48E0} /quiet
msiexec.exe /uninstall {B8FF8670-C6F4-4868-9DB2-C23324C0E575} /quiet
msiexec.exe /uninstall {C1f8E424-81E6-4830-9C05-F6422C48E120} /quiet
MsiExec.exe /uninstall {39F3F171-354C-4167-B68D-ADAD29373D48} /quiet
MsiExec.exe /uninstall {40A61477-2858-4B2B-B6B4-3C525AFE06EB} /quiet
MsiExec.exe /uninstall {21758F4A-B641-4C80-B947-7AB093F57166} /quiet
MsiExec.exe /uninstall {769A10E9-E05D-468D-9961-50986AF92F51} /quiet
MsiExec.exe /uninstall {46DD6A0D-F05F-47B3-B70A-33C82706C38F} /quiet
MsiExec.exe /uninstall {26A24AE4-039D-4CA4-87B4-2F32180251f0} /quiet
MsiExec.exe /uninstall {23832566-6B34-49F9-AA56-A089300DB1f8} /quiet
MsiExec.exe /uninstall {94714B78-E526-489A-9151-60F247D1494F} /quiet
MsiExec.exe /uninstall {CDB86A61-E8B1-46A2-A00D-A0EB4A1f0E8A} /quiet
MsiExec.exe /uninstall {A16DD7A5-8D02-4BEE-8F1D-AAEF1AD1f673} /quiet
MsiExec.exe /uninstall {42E0B35A-DD45-4C91-BBC0-40A84E53645F} /quiet
MsiExec.exe /uninstall {5293FBD5-2E2D-4FC6-8C46-33698183A48C} /quiet
MsiExec.exe /uninstall {965CFD57-1160-42B2-8478-C132E091EECC} /quiet
MsiExec.exe /uninstall {6B0D0A6A-842C-4966-A088-6072DF955609} /quiet
MsiExec.exe /uninstall {D0EC94FD-ABA0-4AB8-8E93-00309A731B9B} /quiet
ECHO.
MsiExec.exe /uninstall {48BC7493-49EB-4B6F-AAEC-208D8F7215EB} /quiet
MsiExec.exe /uninstall {D42AA5F9-659A-40AF-9E04-AC68E6BEEA7A} /quiet
ECHO.
MsiExec.exe /uninstall {1D5E2ADE-DBA1-4F9F-ADD5-E08D159F8D94} /quiet
MsiExec.exe /uninstall {498E0881-C850-4B88-94BB-54C669CF6410} /quiet
ECHO.
MsiExec.exe /uninstall {1CC94CCB-0957-4A62-8B29-D215EDF8D483} /quiet
MsiExec.exe /uninstall {1383640B-0CCD-4DC5-98AF-A632F2057EC3} /quiet
ECHO.
MsiExec.exe /uninstall {C724CD98-7AEB-4F85-8C10-9721600CE0DA} /quiet
MsiExec.exe /uninstall {49591DCF-B568-41D2-8FE8-13C4E1DDD435} /quiet
MsiExec.exe /uninstall {E94C39EC-73F1-42F0-A782-5AE3B3DE558D} /quiet
ECHO.
MsiExec.exe /uninstall {4805C027-FD23-4164-AA52-3918C827136C} /quiet
MsiExec.exe /uninstall {B8BF99B6-750E-45C5-A07D-AF394E5B6139} /quiet
ECHO.
MsiExec.exe /uninstall {A4DA17A3-D3F5-45F9-951E-915F5AF3348B} /quiet
MsiExec.exe /uninstall {61C7ACC0-A7E0-43FB-80A4-C15D0F546355} /quiet
ECHO.
MsiExec.exe /uninstall {6A18B106-D595-4C2E-A208-5F0BA29A3DB4} /quiet
MsiExec.exe /uninstall {D073FF3E-2179-4425-BD5A-EF9D2727D13F} /quiet
ECHO.
MsiExec.exe /uninstall {56FA9B54-4677-4E88-B7BA-0774B050BB5B} /quiet
MsiExec.exe /uninstall {F6DC68A0-DC06-4155-91CA-CC7E5A9A80A5} /quiet
ECHO.
MsiExec.exe /uninstall {76B644F9-E684-4C7A-9ABB-F9C230E1897E} /quiet
MsiExec.exe /uninstall {B33AB53C-67EE-44AE-AC56-0C60E5702CDE} /quiet
ECHO.
MsiExec.exe /uninstall {FBC3A468-54FD-410A-9D07-34F0025CD6BE} /quiet
MsiExec.exe /uninstall {6FD4C38E-90C0-408E-BAA3-13C7FBA0096E} /quiet
ECHO.
MsiExec.exe /uninstall {18A8D4E2-C6ED-4F1D-92A4-115AA9DEA86C} /quiet
MsiExec.exe /uninstall {5A433714-C509-4707-BF0C-410D3FBCE8B3} /quiet
ECHO.
MsiExec.exe /uninstall {BDC760B0-64AF-419B-AD0A-28A92BE878FE} /quiet
MsiExec.exe /uninstall {6A2ACEC0-5875-4F4E-A2C8-F4479E3A7229} /quiet
ECHO Instalando...
GOTO LIBREOFFICERUN


:LIBREOFFICERUN
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto CONFRUN_10_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto CONFRUN_10_64)
ECHO.


:CONFRUN_10_32
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( LibreOffice 32bit)
LibreOffice_32.msi /passive 
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( LibreOffice 32bit)
LibreOffice_helppack.msi /passive 
GOTO Programas3

:CONFRUN_10_64
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( LibreOffice 64bit)
LibreOffice_64.msi /passive 
CLS
ECHO Instalando...
ECHO.
ECHO  * ********* ( LibreOffice 64bit)
LibreOffice_helppack.msi /passive 
GOTO Programas3





:EX302
RefreshWindowsTool.exe
goto SALIR


:EX303
CLS
Color 03
MODE CON cols=40 lines=4
ECHO  [====================================]
ECHO            I N S T A L A N D O
ECHO  [====================================]
DISM /Online /Enable-Feature /FeatureName:NetFx3 /All
CLS
Color 03
MODE CON cols=40 lines=4
ECHO  [====================================]
ECHO            I N S T A L A N D O
ECHO  [====================================]
START /WAIT "NetFram3.5.0.exe" "NetFram3.5.0.exe"
ECHO.
CLS
Color 03
MODE CON cols=40 lines=4
ECHO  [====================================]
ECHO            I N S T A L A N D O
ECHO  [====================================]
NetFram4.8.1.exe /SILENT /VERYSILENT /NORESTART
ECHO.
goto Programas3



:EX304
Color 1f
mode con cols=80 lines=18
ECHO          [==========================================================]
ECHO                               I N S T A L A N D O
ECHO.
ECHO                                 (( WALLPAPER ))
ECHO.
ECHO             " 1 "   Para    Instalar Wallpaper JAHER 
ECHO                        ------------------
ECHO             " 2 "   Para    Instalar Wallpaper MOTOMARKET 
ECHO                           ------------------
ECHO             " 3 "   Para    Menu Anterior.
ECHO                           ------------------
ECHO             " 4 "   Para    Menu Principal.
ECHO                           ------------------
ECHO             " 5 "   Para    Salir
ECHO.
ECHO          [==========================================================]
set /p wp=Ingresa el numero a su eleccion :    
ECHO          [==========================================================]
if %wp%==1 GOTO JAHER_WALL
if %wp%==2 GOTO MOTOMARKET_WALL
if %wp%==3 GOTO Programas3
if %wp%==4 GOTO ZONAS
if %wp%==5 GOTO Salir
if %wp%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO EX304

:JAHER_WALL
ECHO.
Wallpaper_JAHER.exe
ECHO.
JAHER_NEW.deskthemepack
ECHO.
START "JAHER_NEW.theme" "%localappdata%\Microsoft\Windows\Themes\JAHER_NEW\JAHER_NEW.theme"
ECHO.
GOTO Programas3

:MOTOMARKET_WALL
ECHO.
Wallpaper_JAHER.exe
ECHO.
MOTOMARKET.deskthemepack
ECHO.
START "MOTOMARKET.theme" "%localappdata%\Microsoft\Windows\Themes\MOTOMARKE\MOTOMARKET.theme"
ECHO.
GOTO Programas3


:EX305
CLS
Color 03
mode con cols=48 lines=20
@ECHO.    [======================================]
@ECHO.
@ECHO.                 %computername%
@ECHO.               %TIME%
@ECHO.            %DATE%
wmic baseboard get manufacturer
wmic baseboard get product
wmic baseboard get version
wmic baseboard get serialnumber
@ECHO.
@ECHO.    [======================================]
pause
GOTO Programas3




:EX306
Color 1f
mode con cols=80 lines=18
ECHO          [==========================================================]
ECHO                               I N S T A L A N D O
ECHO.
ECHO                         (( FAVORITOS MICROSFOT EDGE ))
ECHO.
ECHO             " 1 "   Para    Favoritos Administracion 
ECHO                        ------------------
ECHO             " 2 "   Para    Favoritos Ventas, Caja y Cob 
ECHO                           ------------------
ECHO             " 3 "   Para    Menu Anterior.
ECHO                           ------------------
ECHO             " 4 "   Para    Menu Principal.
ECHO                           ------------------
ECHO             " 5 "   Para    Salir
ECHO.
ECHO          [==========================================================]
set /p wp=Ingresa el numero a su eleccion :    
ECHO          [==========================================================]
if %wp%==1 GOTO FAV_EDGE_ADM
if %wp%==2 GOTO FAV_EDGE_VTA
if %wp%==3 GOTO Programas3
if %wp%==4 GOTO ZONAS
if %wp%==5 GOTO Salir
if %wp%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO EX306

:FAV_EDGE_ADM
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.            FAVORITOS MICROSOFT EDGE             
@ECHO.     [====================================]
TASKKILL /F /IM msedge.exe
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks.bak"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks.msbak"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Favicons-journal"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Favicons"
ECHO.
COPY /D /V /Y "EdgADM\Bookmarks" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgADM\Bookmarks.bak" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgADM\Bookmarks.msbak" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgADM\Favicons-journal" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgADM\Favicons" "%LocalAppData%\Microsoft\Edge\User Data\Default"
ECHO.
GOTO Programas3

:FAV_EDGE_VTA
CLS
mode con cols=47 lines=6
@ECHO.
@ECHO.
@ECHO.     [====================================]
@ECHO.            FAVORITOS MICROSOFT EDGE             
@ECHO.     [====================================]
TASKKILL /F /IM msedge.exe
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks.bak"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Bookmarks.msbak"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Favicons-journal"
DEL /F /S /Q "%LocalAppData%\Microsoft\Edge\User Data\Default\Favicons"
ECHO.
COPY /D /V /Y "EdgVTA\Bookmarks" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Bookmarks.bak" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Bookmarks.msbak" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Favicons-journal" "%LocalAppData%\Microsoft\Edge\User Data\Default"
COPY /D /V /Y "EdgVTA\Favicons" "%LocalAppData%\Microsoft\Edge\User Data\Default"
ECHO.
GOTO Programas3



ECHO           [----------------------------------------------------(MENU_3) 
ECHO           [----------------------------------------------------(MENU_4) 


:EX401
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        DESACTIVANDO PASSW
ECHO.
ECHO       (( ADMINISTRADOR ))
ECHO  [=============================]
wmic UserAccount set PasswordExpires=False
ECHO.
REGEDIT /S pass.reg
ECHO.
GOTO Programas4



:EX402
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO     ( Escritorio CAJA JAHER )
ECHO  [=============================]
DEL /F /S /Q "%Public%\desktop\Calculator.lnk"
DEL /F /S /Q "%Public%\desktop\Paint.lnk"
DEL /F /S /Q "%Public%\desktop\PREEVALUADOR.lnk"
DEL /F /S /Q "%Public%\desktop\*.RDP"
ECHO.
COPY /D /V /Y "Escr\Calculator.lnk" "%Public%\desktop"
COPY /D /V /Y "Escr\Paint.lnk" "%Public%\desktop"
COPY /D /V /Y "Link\STOCK_JAHER_1.ico" "%Public%\desktop"
COPY /D /V /Y "Link\STOCK_JAHER_2.ico" "%Public%\desktop"
COPY /D /V /Y "Link\STOCK_JAHER_SOLARIS.ico" "%Public%\desktop"
ECHO.
GOTO Programas4



:EX403
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO     ( Escritorio ADM JAHER )
ECHO  [=============================]
DEL /F /S /Q "%Public%\desktop\Calculator.lnk"
DEL /F /S /Q "%Public%\desktop\Internet Explorer.lnk"
DEL /F /S /Q "%Public%\desktop\Paint.lnk"
DEL /F /S /Q "%Public%\desktop\PREEVALUADOR.lnk"
DEL /F /S /Q "%Public%\desktop\*.RDP"
COPY /D /V /Y "Escr\Calculator.lnk" "%Public%\desktop"
COPY /D /V /Y "Escr\Paint.lnk" "%Public%\desktop"
COPY /D /V /Y "Escr\MARCACION.RDP" "%Public%\desktop"
COPY /D /V /Y "Link\STOCK_JAHER_1.ico" "%Public%\desktop"
COPY /D /V /Y "Link\STOCK_JAHER_2.ico" "%Public%\desktop"
COPY /D /V /Y "Link\STOCK_JAHER_SOLARIS.ico" "%Public%\desktop"
ECHO.
CLS
GOTO Programas4



:EX404
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO     ( Escritorio VTA JAHER )
ECHO  [=============================]
DEL /F /S /Q "%Public%\desktop\Calculator.lnk"
DEL /F /S /Q "%Public%\desktop\Internet Explorer.lnk"
DEL /F /S /Q "%Public%\desktop\Paint.lnk"
DEL /F /S /Q "%Public%\desktop\PREEVALUADOR.lnk"
DEL /F /S /Q "%Public%\desktop\*.RDP"
COPY /D /V /Y "Escr\Calculator.lnk" "%Public%\desktop"
COPY /D /V /Y "Escr\Paint.lnk" "%Public%\desktop"
COPY /D /V /Y "Link\STOCK_JAHER_1.ico" "%Public%\desktop"
COPY /D /V /Y "Link\STOCK_JAHER_2.ico" "%Public%\desktop"
COPY /D /V /Y "Link\STOCK_JAHER_SOLARIS.ico" "%Public%\desktop"
ECHO.
CLS
GOTO Programas4



:EX405
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        E J E C U T A N D O
ECHO.
ECHO     DESINSTALADOR DE PROGRAMAS
ECHO  [=============================]
Ayuda.diagcab
ECHO.
GOTO Programas4



:EX406
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        E J E C U T A N D O
ECHO.
ECHO     DESINSTALADOR DE OFFICE
ECHO  [=============================]
ElOffice.diagcab
ECHO.
GOTO Programas4

ECHO           [----------------------------------------------------(MENU_4)
ECHO           [----------------------------------------------------(MENU_5)

:EX501
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        E J E C U T A N D O
ECHO.
ECHO   REPARADOR DE RED E IMPRESORAS
ECHO  [=============================]
AyudaRed.diagcab
ECHO.
GOTO Programas5


:EX502
CLS
Color 03
mode con cols=60 lines=12
ECHO  [====================================================]    
ECHO                    E J E C U T A N D O
ECHO.
ECHO          I N S T A L A D O R   -   G P E D I T
ECHO    [====================================================]
pushd "%~dp0" 

dir /b %SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~3*.mum >List.txt 
dir /b %SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~3*.mum >>List.txt 

for /f %%i in ('findstr /i . List.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i" 
ECHO.
GOTO Programas5

:EX503
CLS
title     REPAIRED WINDOW
COLOR 1E
MODE CON cols=73 lines=14
CLS
ECHO     [==============================================================]
ECHO          REPARADOR....01
ECHO     [==============================================================]
DISM/Online /cleanup-image /CheckHealth
CLS
ECHO     [==============================================================]
ECHO          REPARADOR....02
ECHO     [==============================================================]
DISM/online /cleanup-image /scanHealth
CLS
ECHO     [==============================================================]
ECHO          REPARADOR....03
ECHO     [==============================================================]
DISM/online /cleanup-image /RestoreHealth
CLS
ECHO     [==============================================================]
ECHO          REPARADOR....04
ECHO     [==============================================================]
sfc/scannow
ECHO
shutdown -r -f -t 3
exit
GOTO Programas5

:EX504
Color 1f
mode con cols=80 lines=23
ECHO          [==========================================================]
ECHO                               R E P A R A D O R
ECHO.
ECHO                                 (( OutLook ))
ECHO.
ECHO             " 1 "   Para    PARA OFFICE 2019 
ECHO                           ------------------
ECHO             " 2 "   Para    PARA OFFICE 2016 
ECHO                           ------------------
ECHO             " 3 "   Para    PARA OFFICE 2013
ECHO                           ------------------
ECHO             " 4 "   Para    PARA OFFICE 2010
ECHO                           ------------------
ECHO             " 5 "   Para    PARA OFFICE 2007
ECHO                           ------------------
ECHO             " 6 "   Para    Menu Principal.
ECHO                           ------------------
ECHO             " 7 "   Para    Salir
ECHO.
ECHO          [==========================================================]
set /p ou=Ingresa el numero a su eleccion :    
ECHO          [==========================================================]
if %ou%==1 GOTO RUN_2019
if %ou%==2 GOTO RUN_2019
if %ou%==3 GOTO RUN_2013
if %ou%==4 GOTO RUN_2010
if %ou%==5 GOTO RUN_2007
if %ou%==6 GOTO Programas2
if %ou%==7 GOTO Salir
if %ou%==0 exit else GOTO error

:RUN_2019
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto OUT_2019_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto OUT_2019_64)
ECHO.

:OUT_2019_32
START "SCANPST.EXE" "%PROGRAMFILES%\Microsoft Office\root\Office16\SCANPST.EXE"
GOTO EX504

:OUT_2019_64
START "SCANPST.EXE" "%PROGRAMFILES(X86)%\Microsoft Office\root\Office16\SCANPST.EXE"
GOTO EX504

:RUN_2013
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto OUT_2013_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto OUT_2013_64)
ECHO.

:OUT_2013_32
START "SCANPST.EXE" "%PROGRAMFILES%\Microsoft Office\root\Office15\SCANPST.EXE"
GOTO EX504

:OUT_2013_64
START "SCANPST.EXE" "%PROGRAMFILES(X86)%\Microsoft Office\root\Office15\SCANPST.EXE"
GOTO EX504

:RUN_2010
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto OUT_2010_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto OUT_2010_64)
ECHO.

:OUT_2010_32
START "SCANPST.EXE" "%PROGRAMFILES%\Microsoft Office\root\Office14\SCANPST.EXE"
GOTO EX504

:OUT_2010_64
START "SCANPST.EXE" "%PROGRAMFILES(X86)%\Microsoft Office\root\Office14\SCANPST.EXE"
GOTO EX504

:RUN_2007
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto OUT_2007_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto OUT_2007_64)
ECHO.

:OUT_2007_32
START "SCANPST.EXE" "%PROGRAMFILES%\Microsoft Office\root\Office12\SCANPST.EXE"
GOTO EX504

:OUT_2007_64
START "SCANPST.EXE" "%PROGRAMFILES(X86)%\Microsoft Office\root\Office12\SCANPST.EXE"
GOTO EX504


:EX505
TASKKILL /F /IM explorer.exe
REGEDIT /S "OptimoW10_SIN.reg"
:checkPrivileges
NET FILE 1>NUL 2>NUL
if '%errorlevel%' == '0' ( goto gotPrivileges ) else ( goto getPrivileges )
:getPrivileges
if '%1'=='ELEV' (echo ELEV & shift /1 & goto gotPrivileges)

setlocal DisableDelayedExpansion
set "batchPath=%~0"
setlocal EnableDelayedExpansion
ECHO Set UAC = CreateObject^("Shell.Application"^) > "%temp%\OEgetPrivileges.vbs"
ECHO args = "ELEV " >> "%temp%\OEgetPrivileges.vbs"
ECHO For Each strArg in WScript.Arguments >> "%temp%\OEgetPrivileges.vbs"
ECHO args = args ^& strArg ^& " "  >> "%temp%\OEgetPrivileges.vbs"
ECHO Next >> "%temp%\OEgetPrivileges.vbs"
ECHO UAC.ShellExecute "!batchPath!", args, "", "runas", 1 >> "%temp%\OEgetPrivileges.vbs"
"%SystemRoot%\System32\WScript.exe" "%temp%\OEgetPrivileges.vbs" %*
exit /B
:gotPrivileges
if '%1'=='ELEV' shift /1
setlocal & pushd .
cd /d %~dp0
:Start
sc stop DiagTrack
sc config DiagTrack start= disabled
sc stop dmwappushservice
sc config dmwappushservice start= disabled
reg add HKLM\SYSTEM\CurrentControlSet\Control\WMI\AutoLogger\AutoLogger-Diagtrack-Listener\ /v Start /t REG_DWORD /d 0 /f
reg add HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection\ /v AllowTelemetry /t REG_DWORD /d 0 /f
reg add HKLM\SOFTWARE\Microsoft\WindowsSelfHost\UI\Visibility\ /v DiagnosticErrorText /t REG_DWORD /d 0 /f
reg add HKLM\SOFTWARE\Microsoft\WindowsSelfHost\UI\Strings\ /v DiagnosticErrorText /t REG_SZ /d "" /f
reg add HKLM\SOFTWARE\Microsoft\WindowsSelfHost\UI\Strings\ /v DiagnosticLinkText /t REG_SZ /d "" /f    

:checkPrivileges
NET FILE 1>NUL 2>NUL
if '%errorlevel%' == '0' ( goto gotPrivileges ) else ( goto getPrivileges )
:getPrivileges
if '%1'=='ELEV' (echo ELEV & shift /1 & goto gotPrivileges)

setlocal DisableDelayedExpansion
set "batchPath=%~0"
setlocal EnableDelayedExpansion
ECHO Set UAC = CreateObject^("Shell.Application"^) > "%temp%\OEgetPrivileges.vbs"
ECHO args = "ELEV " >> "%temp%\OEgetPrivileges.vbs"
ECHO For Each strArg in WScript.Arguments >> "%temp%\OEgetPrivileges.vbs"
ECHO args = args ^& strArg ^& " "  >> "%temp%\OEgetPrivileges.vbs"
ECHO Next >> "%temp%\OEgetPrivileges.vbs"
ECHO UAC.ShellExecute "!batchPath!", args, "", "runas", 1 >> "%temp%\OEgetPrivileges.vbs"
"%SystemRoot%\System32\WScript.exe" "%temp%\OEgetPrivileges.vbs" %*
exit /B
ECHO.
:gotPrivileges
if '%1'=='ELEV' shift /1
setlocal & pushd .
cd /d %~dp0

:Start
sc stop MapsBroker
sc config MapsBroker start= disabled
sc stop DoSvc
sc config DoSvc start= disabled  
START "explorer" "%SystemRoot%\explorer.exe"
CLS
ECHO.
ECHO Instalando...
ECHO.
PowerShell -NoProfile -ExecutionPolicy Bypass -Command "& {Start-Process PowerShell -ArgumentList '-NoProfile -ExecutionPolicy Bypass -File ""%~dp0.\rules.ps1""' -Verb RunAs}"
echo Rules should be included in Firewall.
echo.
GOTO Programas5

:EX506
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        E J E C U T A N D O
ECHO.
ECHO          S O P H O S
ECHO  [=============================]
MsiExec.exe /X{20097EC4-1DC2-402C-AFE1-3FF215D33C6E} /quiet
MsiExec.exe /X{20097EC4-1DC2-402C-AFE1-3FF215D33C6E} /q
start "" /WAIT "Sophos\SophosConnect.msi" /passive
GOTO Programas5

ECHO           [----------------------------------------------------(MENU_5)
ECHO           [----------------------------------------------------(MENU_6)
:EX601
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO      (( REPARAR TEXTO ))
ECHO  [=============================]
REGEDIT /S "Reparar_TXT.reg"
ECHO.
GOTO Programas6

:EX602
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto GLPI_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto GLPI_64)
ECHO.

:GLPI_32
CLS
Color 04
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        ELIMINANDO PROGRAMA
ECHO.
ECHO   (( FusionInventory-Agent  ))
ECHO  [=============================]
START /HIGH /WAIT "Uninstall.exe" "%PROGRAMFILES%\FusionInventory-Agent\Uninstall.exe" /S
msiexec.exe /uninstall {CF9A3F4C-6BF4-1014-BBBD-E6E599B62783} /quiet
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( GLPI  ))
ECHO  [=============================]
start "" notepad.exe "C:\Program Files\JAHER\VENTORY\RUTA.txt"
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( GLPI  ))
ECHO  [=============================]
start "" /WAIT "VENTORY\GLPI-Agent-x86.msi"
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( GLPI  ))
ECHO  [=============================]
COPY /D /V /Y "VENTORY\toolbox-plugin.local" "%ProgramFiles%\GLPI-Agent\etc"
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( GLPI  ))
ECHO  [=============================]
start "" /WAIT "services.msc"
CLS
Color 02
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( GLPI  ))
ECHO  [=============================]
start msedge /WAIT "http://localhost:62354/toolbox"
GOTO Programas6


:GLPI_64
CLS
Color 04
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        ELIMINANDO PROGRAMA
ECHO.
ECHO   (( FusionInventory-Agent  ))
ECHO  [=============================]
START /HIGH /WAIT "Uninstall.exe" "%PROGRAMFILES%\FusionInventory-Agent\Uninstall.exe" /S
msiexec.exe /uninstall {CF9A3F4C-6BF4-1014-BBBD-E6E599B62783} /quiet
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( GLPI  ))
ECHO  [=============================]
start "" notepad.exe "C:\Program Files (x86)\JAHER\VENTORY\RUTA.txt"
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( GLPI  ))
ECHO  [=============================]
start "" /WAIT "VENTORY\GLPI-Agent-x64.msi"
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( GLPI  ))
ECHO  [=============================]
COPY /D /V /Y "VENTORY\toolbox-plugin.local" "%ProgramFiles%\GLPI-Agent\etc"
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( GLPI  ))
ECHO  [=============================]
start "" /WAIT "services.msc"
CLS
Color 02
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( GLPI  ))
ECHO  [=============================]
start msedge /WAIT "http://localhost:62354/toolbox"
GOTO Programas6

:EX603
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO            ELIMINAR
ECHO.
ECHO      (( APP DE WINDOWS ))
ECHO  [=============================]
start "" /WAIT "HR\10AppsManager.exe"
@echo off
:: Requiere derechos de administración
echo Reparando Microsoft Store...
powershell -Command "& {Start-Process powershell -ArgumentList 'wsreset.exe', 'Dism /Online /Cleanup-Image /RestoreHealth', 'sfc /scannow' -NoNewWindow -Verb RunAs}"
timeout /t 30 /nobreak
echo Reparación completada. Ahora reinstalando aplicaciones...

:: Reinstalar Microsoft Store y otras aplicaciones
powershell -Command "& {
    # Reinstalar Microsoft Store
    Get-AppxPackage -allusers *Microsoft.WindowsStore* | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppxManifest.xml"}

    # Reinstalar Cámara
    Get-AppxPackage -allusers *Microsoft.WindowsCamera* | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppxManifest.xml"}

    # Reinstalar Calculadora
    Get-AppxPackage -allusers *Microsoft.WindowsCalculator* | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppxManifest.xml"}

    # Reinstalar Paint
    Get-AppxPackage -allusers *Microsoft.MSPaint* | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppxManifest.xml"}

    # Reinstalar Sticky Notes
    Get-AppxPackage -allusers *Microsoft.MicrosoftStickyNotes* | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppxManifest.xml"}
}"

echo Reinstalación completada.
GOTO Programas6

:EX604
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto CRYST32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto CRYST64)
ECHO.

:CRYST32
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO       (( CrystalDiskInfo ))
ECHO  [=============================]
CrystalDiskInfo.exe /SILENT
ECHO.
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO            (( RUN ))
ECHO  [=============================]
START /WAIT "DiskInfo32" "%PROGRAMFILES%\CrystalDiskInfo\DiskInfo32.exe"
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( UNINSTAL ))
ECHO  [=============================]
"%PROGRAMFILES%\CrystalDiskInfo\unins000.exe" /S /NCRC
CLS
goto Programas6

:CRYST64
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO       (( CrystalDiskInfo ))
ECHO  [=============================]
CrystalDiskInfo.exe /SILENT
ECHO.
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO            (( RUN ))
ECHO  [=============================]
START "" /WAIT "C:\Program Files\CrystalDiskInfo\DiskInfo64.exe"
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO        I N S T A L A N D O
ECHO.
ECHO          (( UNINSTAL ))
ECHO  [=============================]
"C:\Program Files\CrystalDiskInfo\unins000.exe" /S /NCRC
CLS
goto Programas6

:EX605
CLS
Color 03
mode con cols=35 lines=6
ECHO  [=============================]
ECHO         ABRIR CONFIGURACION
ECHO.
ECHO         (( POWER SHELL ))
ECHO  [=============================]
JavaUninstallTool.exe
ECHO.
GOTO Programas6

:EX606
CLS
ECHO Instalando...
ECHO.
ECHO  * ******* ( MARCADOR MICROSOFT EDGE )
ECHO.
taskkill /f /im msedge.exe
RD /S /Q "%localappdata%\Microsoft\Edge\User Data"
Edge_Fav.exe
ECHO.
GOTO Programas6

ECHO           [----------------------------------------------------(MENU_6)
ECHO           [----------------------------------------------------(MENU_7)

:EX701
ECHO.
MD "C:\APPL"
COPY /D /V /Y "Link\Marcacion.ico" "C:\APPL"
COPY /D /V /Y "Link\marcacionL1.jnlp" "C:\APPL"
DEL /F /S /Q "%Public%\desktop\MARCACION.RDP"
DEL /F /S /Q "%Public%\desktop\Marcacion.lnk"
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%Public%\desktop\Marcacion.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\marcacionL1.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Marcacion.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
GOTO Programas7

:EX702
ECHO.
MD "C:\APPL"
COPY /D /V /Y "Link\Marcacion.ico" "C:\APPL"
COPY /D /V /Y "Link\marcacionL2.jnlp" "C:\APPL"
DEL /F /S /Q "%Public%\desktop\MARCACION.RDP"
DEL /F /S /Q "%Public%\desktop\Marcacion.lnk"
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%Public%\desktop\Marcacion.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\marcacionL2.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Marcacion.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
GOTO Programas7


:EX703
ECHO.
MD "C:\APPL"
COPY /D /V /Y "Link\Marcacion.ico" "C:\APPL"
COPY /D /V /Y "Link\marcacionS1.jnlp" "C:\APPL"
DEL /F /S /Q "%Public%\desktop\MARCACION.RDP"
DEL /F /S /Q "%Public%\desktop\Marcacion.lnk"
ECHO.
set SCRIPT="%TEMP%\%RANDOM%-%RANDOM%-%RANDOM%-%RANDOM%.vbs"
echo Set oWS = WScript.CreateObject("WScript.Shell") >> %SCRIPT%
echo sLinkFile = "%Public%\desktop\Marcacion.lnk" >> %SCRIPT%
echo Set oLink = oWS.CreateShortcut(sLinkFile) >> %SCRIPT%
echo oLink.TargetPath = "C:\APPL\marcacionS1.jnlp" >> %SCRIPT%
echo oLink.WorkingDirectory = "C:\APPL" >> %SCRIPT%
echo oLink.IconLocation = "C:\APPL\Marcacion.ico" >> %SCRIPT%
echo oLink.Save >> %SCRIPT%
cscript /nologo %SCRIPT%
del %SCRIPT%
GOTO Programas7

:EX704
CLS
ECHO Instalando...
ECHO.
ECHO  * ******* ( QUE NET FRAMEWORDS TENGO )
ECHO.
START /WAIT "dotnetver.exe" "HR\dotnetver.exe" 
GOTO Programas7

:EX705
CLS
ECHO Instalando...
ECHO.
ECHO  * ******* ( REPARAR OUTLOOK )
ECHO.
REGEDIT /S "fixit_html.reg"
GOTO Programas7

:EX706
CLS
CLS
ECHO Instalando...
ECHO.
ECHO ( K-Lite Codec )
"%PROGRAMFILES%\K-Lite Codec Pack\unins000.exe"  /SILENT
"%PROGRAMFILES(X86)%\K-Lite Codec Pack\unins000.exe"  /SILENT
ECHO.
Codec_Pack.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /SP-
GOTO Programas7


ECHO           [----------------------------------------------------(DESINSTALADORES)

:UPDATES_TOTAL
CLS
COLOR 47
MODE CON cols=40 lines=9
TASKKILL /F /IM explorer.exe
ECHO.
ECHO  [************************************]
ECHO              - IMPORTANTE -
ECHO.
ECHO      CUANDO TERMINE POR COMPLETO EL 
ECHO       INSTALADOR SE AUTO REINICIARA 
ECHO              EL COMPUTADOR 
ECHO  [************************************] 
>nul ping -n 10 localhost 
CLS
if %PROCESSOR_ARCHITECTURE%==x86 (goto UNIS_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto UNIS_64)
ECHO.



:UNIS_32
TASKKILL /F /IM explorer.exe
TASKKILL /F /IM firefox.exe
TASKKILL /F /IM Teams.exe
REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DateTime\Servers /v 1 /t REG_SZ  /d ntp1.jaher.com.ec /f
MODE CON cols=50 lines=5 
CLS
ECHO.
"%PROGRAMFILES%\K-Lite Codec Pack\unins000.exe" /SILENT
ECHO Instalando...
ECHO.
ECHO  * 10%% ( JAVA UNINSTAL. )
ECHO --------------------------------------------
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180241f0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180241f0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180261f0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180261f0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180271f0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180271f0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180281F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180281F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180291F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180291F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180301F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180301F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180311F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180311F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180321F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180321F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180321F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180321F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180331F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180331F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180331F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180331F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180333F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180333F0} /q
ECHO.
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180341F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180341F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180341F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180341F0} /q
ECHO.
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180351F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180351F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180351F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180351F0} /q
ECHO.
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F32180381F0} /quiet
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F32180381F0} /q
ECHO.
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F64180381F0} /quiet
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F64180381F0} /q
ECHO.
MsiExec.exe /X{71024AE4-039E-4CA4-87B4-2F32180401F0} /quiet
MsiExec.exe /X{71024AE4-039E-4CA4-87B4-2F64180401F0} /q
CLS
ECHO Instalando...
ECHO.
ECHO  * 10%% ( JAVA UNINSTAL. )
ECHO --------------------------------------------
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\security\exception.sites"
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\deployment.properties"
CLS
ECHO Instalando...
ECHO.
ECHO  *** 30%% ( ADOBE DC UNINSTAL. )
ECHO --------------------------------------------
msiexec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC0F074E4100} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-FFFF-7B44-AC0F074E4100} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC13154E5A00} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC15014EA700} /quiet
MsiExec.exe /uninstall {AC76BA86-1034-1033-7760-BC15014EA700} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
ECHO.
MsiExec.exe /uninstall {AC76BA86-1034-1033-7760-BC15014EA700} /quiet
CLS
ECHO Instalando...
ECHO.
CLS
ECHO Instalando...
ECHO.
ECHO  **** 40%% ( LibreOffice UNINSTAL. )
ECHO --------------------------------------------
msiexec.exe /uninstall {235CBF9C-D3E1-4703-A729-7AC6F101C15E} /quiet
msiexec.exe /uninstall {4DEFF29A-B682-4B51-B1DD-F040F1618B26} /quiet
msiexec.exe /uninstall {6110D2CC-70B4-415E-AF5A-7BB496AB264B} /quiet
msiexec.exe /uninstall {953D746F-FA08-462B-A66E-7A7FFF322580} /quiet
msiexec.exe /uninstall {50EB7256-5011-4480-8E89-B3AE0C30AFF0} /quiet
msiexec.exe /uninstall {4DACF7A7-C851-4943-A63D-3CAE495C48E0} /quiet
msiexec.exe /uninstall {B8FF8670-C6F4-4868-9DB2-C23324C0E575} /quiet
msiexec.exe /uninstall {C1f8E424-81E6-4830-9C05-F6422C48E120} /quiet
MsiExec.exe /uninstall {39F3F171-354C-4167-B68D-ADAD29373D48} /quiet
MsiExec.exe /uninstall {40A61477-2858-4B2B-B6B4-3C525AFE06EB} /quiet
MsiExec.exe /uninstall {21758F4A-B641-4C80-B947-7AB093F57166} /quiet
MsiExec.exe /uninstall {769A10E9-E05D-468D-9961-50986AF92F51} /quiet
MsiExec.exe /uninstall {46DD6A0D-F05F-47B3-B70A-33C82706C38F} /quiet
MsiExec.exe /uninstall {26A24AE4-039D-4CA4-87B4-2F32180251f0} /quiet
MsiExec.exe /uninstall {23832566-6B34-49F9-AA56-A089300DB1f8} /quiet
MsiExec.exe /uninstall {94714B78-E526-489A-9151-60F247D1494F} /quiet
MsiExec.exe /uninstall {CDB86A61-E8B1-46A2-A00D-A0EB4A1f0E8A} /quiet
MsiExec.exe /uninstall {A16DD7A5-8D02-4BEE-8F1D-AAEF1AD1f673} /quiet
MsiExec.exe /uninstall {42E0B35A-DD45-4C91-BBC0-40A84E53645F} /quiet
MsiExec.exe /uninstall {5293FBD5-2E2D-4FC6-8C46-33698183A48C} /quiet
MsiExec.exe /uninstall {965CFD57-1160-42B2-8478-C132E091EECC} /quiet
MsiExec.exe /uninstall {6B0D0A6A-842C-4966-A088-6072DF955609} /quiet
MsiExec.exe /uninstall {D0EC94FD-ABA0-4AB8-8E93-00309A731B9B} /quiet
ECHO.
MsiExec.exe /uninstall {48BC7493-49EB-4B6F-AAEC-208D8F7215EB} /quiet
MsiExec.exe /uninstall {D42AA5F9-659A-40AF-9E04-AC68E6BEEA7A} /quiet
ECHO.
MsiExec.exe /uninstall {1D5E2ADE-DBA1-4F9F-ADD5-E08D159F8D94} /quiet
MsiExec.exe /uninstall {498E0881-C850-4B88-94BB-54C669CF6410} /quiet
ECHO.
MsiExec.exe /uninstall {C724CD98-7AEB-4F85-8C10-9721600CE0DA} /quiet
MsiExec.exe /uninstall {49591DCF-B568-41D2-8FE8-13C4E1DDD435} /quiet
ECHO.
MsiExec.exe /uninstall {4805C027-FD23-4164-AA52-3918C827136C} /quiet
MsiExec.exe /uninstall {B8BF99B6-750E-45C5-A07D-AF394E5B6139} /quiet
ECHO.
MsiExec.exe /uninstall {A4DA17A3-D3F5-45F9-951E-915F5AF3348B} /quiet
MsiExec.exe /uninstall {61C7ACC0-A7E0-43FB-80A4-C15D0F546355} /quiet
ECHO.
MsiExec.exe /uninstall {6A18B106-D595-4C2E-A208-5F0BA29A3DB4} /quiet
MsiExec.exe /uninstall {D073FF3E-2179-4425-BD5A-EF9D2727D13F} /quiet
ECHO.
MsiExec.exe /uninstall {56FA9B54-4677-4E88-B7BA-0774B050BB5B} /quiet
MsiExec.exe /uninstall {F6DC68A0-DC06-4155-91CA-CC7E5A9A80A5} /quiet
ECHO.
MsiExec.exe /uninstall {76B644F9-E684-4C7A-9ABB-F9C230E1897E} /quiet
MsiExec.exe /uninstall {B33AB53C-67EE-44AE-AC56-0C60E5702CDE} /quiet
ECHO.
MsiExec.exe /uninstall {FBC3A468-54FD-410A-9D07-34F0025CD6BE} /quiet
MsiExec.exe /uninstall {6FD4C38E-90C0-408E-BAA3-13C7FBA0096E} /quiet
ECHO.
MsiExec.exe /uninstall {18A8D4E2-C6ED-4F1D-92A4-115AA9DEA86C} /quiet
MsiExec.exe /uninstall {5A433714-C509-4707-BF0C-410D3FBCE8B3} /quiet
ECHO.
MsiExec.exe /uninstall {BDC760B0-64AF-419B-AD0A-28A92BE878FE} /quiet
MsiExec.exe /uninstall {6A2ACEC0-5875-4F4E-A2C8-F4479E3A7229} /quiet
CLS
ECHO Instalando...
ECHO.
ECHO  **** 40%% ( LibreOffice UNINSTAL. )
ECHO --------------------------------------------
MsiExec.exe /uninstall {CDB86A61-E8B1-46A2-A00D-A0EB4A1f0E8A} /quiet
MsiExec.exe /uninstall {A16DD7A5-8D02-4BEE-8F1D-AAEF1AD1f673} /quiet
MsiExec.exe /uninstall {42E0B35A-DD45-4C91-BBC0-40A84E53645F} /quiet
MsiExec.exe /uninstall {5293FBD5-2E2D-4FC6-8C46-33698183A48C} /quiet
MsiExec.exe /uninstall {9B8D9C01-5BC5-4CD4-9A7B-166EFDC4697D} /quiet
MsiExec.exe /uninstall {965CFD57-1160-42B2-8478-C132E091EECC} /quiet
MsiExec.exe /uninstall {6B0D0A6A-842C-4966-A088-6072DF955609} /quiet
MsiExec.exe /uninstall {D0EC94FD-ABA0-4AB8-8E93-00309A731B9B} /quiet
MsiExec.exe /uninstall {28201B87-B12B-459F-8742-25D3C1CDD496} /quiet
ECHO.
MsiExec.exe /uninstall {48BC7493-49EB-4B6F-AAEC-208D8F7215EB} /quiet
MsiExec.exe /uninstall {D42AA5F9-659A-40AF-9E04-AC68E6BEEA7A} /quiet
ECHO.
MsiExec.exe /uninstall {1D5E2ADE-DBA1-4F9F-ADD5-E08D159F8D94} /quiet
MsiExec.exe /uninstall {498E0881-C850-4B88-94BB-54C669CF6410} /quiet
CLS
ECHO Instalando...
ECHO.
CLS
ECHO Instalando...
ECHO.
ECHO  ****** 60%% ( ONLYOFFICE UNINSTAL. )
ECHO --------------------------------------------
MsiExec.exe /uninstall {6655A542-8D82-40BB-9812-7CD1C8935488} /quiet
CLS
ECHO Instalando...
ECHO.
ECHO  ****** 70%% ( Chrome UNINSTAL. )
ECHO --------------------------------------------
MsiExec.exe /X{C27ED456-1fA7-3541-BB95-16033B22B71E} /qn
MsiExec.exe /X{7F544E85-3FC4-3F6B-BE1C-679880E73AD3} /qn
MsiExec.exe /X{50ADB1A8-7D22-3FA4-9F99-AD149455FE09} /qn
MsiExec.exe /X{6A6D3422-8127-3867-A83C-56B555636ECA} /qn
MsiExec.exe /I{60EC980A-BDA2-4CB6-A427-B07A5498B4CA} /qn
MsiExec.exe /X{E6D120AA-150F-3059-8C1C-DAFAA59BD326} /qn
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( MOZILLA UNINSTAL. )
ECHO --------------------------------------------
START /HIGH /WAIT "helper.exe" "%PROGRAMFILES%\Mozilla Firefox\uninstall\helper.exe" /s
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( Mozilla M. )
ECHO --------------------------------------------
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 90%% ( Mozilla M. )
ECHO --------------------------------------------
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ********* 100%% ( WinRAR UNINSTAL. )
ECHO --------------------------------------------
START /HIGH /WAIT "Uninstall.exe" "%PROGRAMFILES%\WinRAR\Uninstall.exe" /S
CLS
ECHO Instalando...
ECHO.
ECHO  ********* 100%% ( OneDrive. )
ECHO --------------------------------------------
taskkill /f /im OneDrive.exe
%SystemRoot%/System32/OneDriveSetup.exe /uninstall
GOTO UPDATES_RUN



:UNIS_64
TASKKILL /F /IM explorer.exe
TASKKILL /F /IM firefox.exe
TASKKILL /F /IM Teams.exe
REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DateTime\Servers /v 1 /t REG_SZ  /d ntp1.jaher.com.ec /f
MODE CON cols=50 lines=5 
CLS
ECHO.
"%PROGRAMFILES(X86)%\K-Lite Codec Pack\unins000.exe" /SILENT
ECHO Instalando...
ECHO.
ECHO  * 10%% ( JAVA UNINSTAL. )
ECHO --------------------------------------------
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180241f0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180241f0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180261f0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180261f0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180271f0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180271f0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180281F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180281F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180291F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180291F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180301F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180301F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180311F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180311F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180321F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180321F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180321F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180321F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180331F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180331F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180331F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180331F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180333F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180333F0} /q
ECHO.
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180341F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180341F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180341F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180341F0} /q
ECHO.
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180351F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F32180351F0} /q
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180351F0} /quiet
MsiExec.exe /X{26A24AE4-039D-4CA4-87B4-2F64180351F0} /q
ECHO.
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F32180381F0} /quiet
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F32180381F0} /q
ECHO.
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F64180381F0} /quiet
MsiExec.exe /X{77924AE4-039E-4CA4-87B4-2F64180381F0} /q
ECHO.
MsiExec.exe /X{71024AE4-039E-4CA4-87B4-2F32180401F0} /quiet
MsiExec.exe /X{71024AE4-039E-4CA4-87B4-2F64180401F0} /q
CLS
ECHO Instalando...
ECHO.
ECHO  * 10%% ( JAVA UNINSTAL. )
ECHO --------------------------------------------
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\security\exception.sites"
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\deployment.properties"
CLS
ECHO Instalando...
ECHO.
ECHO  *** 30%% ( ADOBE DC UNINSTAL. )
ECHO --------------------------------------------
msiexec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC0F074E4100} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-FFFF-7B44-AC0F074E4100} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC13154E5A00} /quiet
msiexec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-2530-0000-AC15014EA700} /quiet
MsiExec.exe /uninstall {AC76BA86-1034-1033-7760-BC15014EA700} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
MsiExec.exe /uninstall {AC76BA86-7AD7-1034-7B44-AC0F074E4100} /quiet
ECHO.
MsiExec.exe /uninstall {AC76BA86-1034-1033-7760-BC15014EA700} /quiet
CLS
ECHO Instalando...
ECHO.
CLS
ECHO Instalando...
ECHO.
ECHO  **** 40%% ( LibreOffice UNINSTAL. )
ECHO --------------------------------------------
msiexec.exe /uninstall {235CBF9C-D3E1-4703-A729-7AC6F101C15E} /quiet
msiexec.exe /uninstall {4DEFF29A-B682-4B51-B1DD-F040F1618B26} /quiet
msiexec.exe /uninstall {6110D2CC-70B4-415E-AF5A-7BB496AB264B} /quiet
msiexec.exe /uninstall {953D746F-FA08-462B-A66E-7A7FFF322580} /quiet
msiexec.exe /uninstall {50EB7256-5011-4480-8E89-B3AE0C30AFF0} /quiet
msiexec.exe /uninstall {4DACF7A7-C851-4943-A63D-3CAE495C48E0} /quiet
msiexec.exe /uninstall {B8FF8670-C6F4-4868-9DB2-C23324C0E575} /quiet
msiexec.exe /uninstall {C1f8E424-81E6-4830-9C05-F6422C48E120} /quiet
MsiExec.exe /uninstall {39F3F171-354C-4167-B68D-ADAD29373D48} /quiet
MsiExec.exe /uninstall {40A61477-2858-4B2B-B6B4-3C525AFE06EB} /quiet
MsiExec.exe /uninstall {21758F4A-B641-4C80-B947-7AB093F57166} /quiet
MsiExec.exe /uninstall {769A10E9-E05D-468D-9961-50986AF92F51} /quiet
MsiExec.exe /uninstall {46DD6A0D-F05F-47B3-B70A-33C82706C38F} /quiet
MsiExec.exe /uninstall {26A24AE4-039D-4CA4-87B4-2F32180251f0} /quiet
MsiExec.exe /uninstall {23832566-6B34-49F9-AA56-A089300DB1f8} /quiet
MsiExec.exe /uninstall {94714B78-E526-489A-9151-60F247D1494F} /quiet
MsiExec.exe /uninstall {CDB86A61-E8B1-46A2-A00D-A0EB4A1f0E8A} /quiet
MsiExec.exe /uninstall {A16DD7A5-8D02-4BEE-8F1D-AAEF1AD1f673} /quiet
MsiExec.exe /uninstall {42E0B35A-DD45-4C91-BBC0-40A84E53645F} /quiet
MsiExec.exe /uninstall {5293FBD5-2E2D-4FC6-8C46-33698183A48C} /quiet
MsiExec.exe /uninstall {965CFD57-1160-42B2-8478-C132E091EECC} /quiet
MsiExec.exe /uninstall {6B0D0A6A-842C-4966-A088-6072DF955609} /quiet
MsiExec.exe /uninstall {D0EC94FD-ABA0-4AB8-8E93-00309A731B9B} /quiet
ECHO.
MsiExec.exe /uninstall {48BC7493-49EB-4B6F-AAEC-208D8F7215EB} /quiet
MsiExec.exe /uninstall {D42AA5F9-659A-40AF-9E04-AC68E6BEEA7A} /quiet
ECHO.
MsiExec.exe /uninstall {1D5E2ADE-DBA1-4F9F-ADD5-E08D159F8D94} /quiet
MsiExec.exe /uninstall {498E0881-C850-4B88-94BB-54C669CF6410} /quiet
ECHO.
MsiExec.exe /uninstall {C724CD98-7AEB-4F85-8C10-9721600CE0DA} /quiet
MsiExec.exe /uninstall {49591DCF-B568-41D2-8FE8-13C4E1DDD435} /quiet
ECHO.
MsiExec.exe /uninstall {4805C027-FD23-4164-AA52-3918C827136C} /quiet
MsiExec.exe /uninstall {B8BF99B6-750E-45C5-A07D-AF394E5B6139} /quiet
ECHO.
MsiExec.exe /uninstall {A4DA17A3-D3F5-45F9-951E-915F5AF3348B} /quiet
MsiExec.exe /uninstall {61C7ACC0-A7E0-43FB-80A4-C15D0F546355} /quiet
ECHO.
MsiExec.exe /uninstall {6A18B106-D595-4C2E-A208-5F0BA29A3DB4} /quiet
MsiExec.exe /uninstall {D073FF3E-2179-4425-BD5A-EF9D2727D13F} /quiet
ECHO.
MsiExec.exe /uninstall {56FA9B54-4677-4E88-B7BA-0774B050BB5B} /quiet
MsiExec.exe /uninstall {F6DC68A0-DC06-4155-91CA-CC7E5A9A80A5} /quiet
ECHO.
MsiExec.exe /uninstall {76B644F9-E684-4C7A-9ABB-F9C230E1897E} /quiet
MsiExec.exe /uninstall {B33AB53C-67EE-44AE-AC56-0C60E5702CDE} /quiet
ECHO.
MsiExec.exe /uninstall {FBC3A468-54FD-410A-9D07-34F0025CD6BE} /quiet
MsiExec.exe /uninstall {6FD4C38E-90C0-408E-BAA3-13C7FBA0096E} /quiet
ECHO.
MsiExec.exe /uninstall {18A8D4E2-C6ED-4F1D-92A4-115AA9DEA86C} /quiet
MsiExec.exe /uninstall {5A433714-C509-4707-BF0C-410D3FBCE8B3} /quiet
ECHO.
MsiExec.exe /uninstall {BDC760B0-64AF-419B-AD0A-28A92BE878FE} /quiet
MsiExec.exe /uninstall {6A2ACEC0-5875-4F4E-A2C8-F4479E3A7229} /quiet
CLS
ECHO.
ECHO  **** 40%% ( LibreOffice UNINSTAL. )
ECHO --------------------------------------------
MsiExec.exe /uninstall {CDB86A61-E8B1-46A2-A00D-A0EB4A1f0E8A} /quiet
MsiExec.exe /uninstall {A16DD7A5-8D02-4BEE-8F1D-AAEF1AD1f673} /quiet
MsiExec.exe /uninstall {42E0B35A-DD45-4C91-BBC0-40A84E53645F} /quiet
MsiExec.exe /uninstall {5293FBD5-2E2D-4FC6-8C46-33698183A48C} /quiet
MsiExec.exe /uninstall {9B8D9C01-5BC5-4CD4-9A7B-166EFDC4697D} /quiet
MsiExec.exe /uninstall {965CFD57-1160-42B2-8478-C132E091EECC} /quiet
MsiExec.exe /uninstall {6B0D0A6A-842C-4966-A088-6072DF955609} /quiet
MsiExec.exe /uninstall {D0EC94FD-ABA0-4AB8-8E93-00309A731B9B} /quiet
MsiExec.exe /uninstall {28201B87-B12B-459F-8742-25D3C1CDD496} /quiet
ECHO.
MsiExec.exe /uninstall {48BC7493-49EB-4B6F-AAEC-208D8F7215EB} /quiet
MsiExec.exe /uninstall {D42AA5F9-659A-40AF-9E04-AC68E6BEEA7A} /quiet
ECHO.
MsiExec.exe /uninstall {1D5E2ADE-DBA1-4F9F-ADD5-E08D159F8D94} /quiet
MsiExec.exe /uninstall {498E0881-C850-4B88-94BB-54C669CF6410} /quiet
ECHO.
MsiExec.exe /uninstall {56658FF2-07C2-49A7-B19F-CA61549A913B} /quiet
ECHO.
MsiExec.exe /uninstall {063CC195-EEF8-4601-89C6-CB18230BD5E6} /quiet
MsiExec.exe /uninstall {546961EA-2B75-4B71-B580-D61DDFA2BA83} /quiet
CLS
ECHO Instalando...
ECHO.
ECHO  ****** 60%% ( ONLYOFFICE UNINSTAL. )
ECHO --------------------------------------------
MsiExec.exe /uninstall {6655A542-8D82-40BB-9812-7CD1C8935488} /quiet
CLS
CLS
ECHO Instalando...
ECHO.
ECHO  ****** 60%% ( Chrome UNINSTAL. )
ECHO --------------------------------------------
MsiExec.exe /X{C27ED456-1fA7-3541-BB95-16033B22B71E} /qn
MsiExec.exe /X{7F544E85-3FC4-3F6B-BE1C-679880E73AD3} /qn
MsiExec.exe /X{50ADB1A8-7D22-3FA4-9F99-AD149455FE09} /qn
MsiExec.exe /X{6A6D3422-8127-3867-A83C-56B555636ECA} /qn
MsiExec.exe /I{60EC980A-BDA2-4CB6-A427-B07A5498B4CA} /qn
MsiExec.exe /X{E6D120AA-150F-3059-8C1C-DAFAA59BD326} /qn
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( MOZILLA UNINSTAL. )
ECHO --------------------------------------------
START /HIGH /WAIT "helper.exe" "C:\Program Files\Mozilla Firefox\uninstall\helper.exe" /s
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( Mozilla M. )
ECHO --------------------------------------------
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 90%% ( Mozilla M. )
ECHO --------------------------------------------
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ********* 100%% ( WinRAR UNINSTAL. )
ECHO --------------------------------------------
START /HIGH /WAIT "Uninstall.exe" "C:\Program Files\WinRAR\Uninstall.exe" /S
CLS
ECHO Instalando...
ECHO.
ECHO  ********* 100%% ( OneDrive. )
ECHO --------------------------------------------
taskkill /f /im OneDrive.exe
%SystemRoot%/SysWOW64/OneDriveSetup.exe /uninstall
GOTO UPDATES_RUN

ECHO           [----------------------------------------------------(DESINSTALADORES)


:UPDATES_RUN
title                               UTILITARIOS JAHER
CLS
COLOR 0F
mode con cols=80 lines=18
ECHO           [-----------------------------------------------------------] 
ECHO                              UPDATE PROGRAMAS PARA LA PC
ECHO                                    ( 30.1.2025 )
ECHO          [----------------------------------------------------------]
ECHO                          " DEPARTAMENTO DE SISTEMA JAHER "
ECHO.
ECHO              " 1 "  Para   Instalar UPDATE BASICOS ( CAJA )
ECHO                     ------------------------------------------------
ECHO              " 2 "  Para   Instalar UPDATE BASICOS (VENTAS - COBRANZA)
ECHO                     ------------------------------------------------
ECHO              " 3 "  Para   Instalar UPDATE BASICOS (ADMINISTRADOR)
ECHO                     ------------------------------------------------
ECHO              " 4 "  Para   Menu Principal
ECHO              " 5 "  Para   Salir
ECHO.
ECHO          [----------------------------------------------------------]
ECHO.
set /p updt=  El numero a tu eleccion :    
ECHO.
if %updt%==1 GOTO UPDCAJ 
if %updt%==2 GOTO UPDCON
if %updt%==3 GOTO UPDSIN
if %updt%==4 GOTO ZONAS
if %updt%==5 GOTO Salir
if %updt%==0 exit else GOTO error

:error
CLS
color 0E
MODE CON cols=44 lines=15
ECHO.
ECHO  [======================================]
ECHO  [                                      ]
ECHO  [       Valor incorrecto.!             ]
ECHO  [                                      ]
ECHO  [       Vuelva a Intentarlo            ]
ECHO  [                                      ]
ECHO  [======================================]
ECHO.
TIMEOUT /T 05 
GOTO UPDATES_RUN


ECHO           [--------------------(FIERE CON OFFICE)-----------------------]

:FIR_DELCON
CLS
MODE CON cols=50 lines=5 
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto FIRVTDA_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto FIRVTDA_64)
ECHO.

:FIRVTDA_32
CLS
ECHO Instalando...
ECHO.
ECHO  ********* 90%% ( Mozilla U. )
ECHO --------------------------------------------
"%PROGRAMFILES%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  *********** 100%% ( LibreOffice )
ECHO --------------------------------------------
LibreOffice_32.msi /passive 
CLS
ECHO Instalando...
ECHO.
ECHO  *********** 100%% ( LibreOffice )
ECHO --------------------------------------------
LibreOffice_helppack.msi /passive 
CLS
ECHO Instalando...
ECHO.
ECHO  *********** 100%% ( K-Lite Codec )
ECHO --------------------------------------------
Codec_Pack.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /SP-
ECHO.
assoc .pdf=AcroExch.Document.DC
assoc .url=InternetShortcut
REM disable java update by policy 
reg add "HKLM\SOFTWARE\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T
REG_DWORD /D 0 /F
if defined programfiles(x86) reg add "HKLM\SOFTWARE\Wow6432Node\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T REG_DWORD /D 0 /F
REM Remove java update scheduler
REG DELETE "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v
"SunJavaUpdateSched" /f
if defined programfiles(x86) reg delete "HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run" /v "SunJavaUpdateSched" /f
REM NoSoloHacking.info
REM kill java updater if started
taskkill /IM jucheck.exe /F
taskkill IM juscheck.exe /F
@ECHO.
certutil -f -v -addstore -enterprise root SecurityAppliance_SSL_CA_FINAL.pem
MD "C:\Instaladores_JH"
COPY /D /V /Y "SecurityAppliance_SSL_CA_FINAL.pem" "C:\Instaladores_JH"
ECHO.
JAHER_NEW.deskthemepack
MOTOMARKET.deskthemepack
REG DELETE HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run /f
[-HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run]
COPY /D /V /Y "Borrar_Temp.bat" "C:\Windows"
schtasks /Create /TN "Depurar" /SC ONLOGON /TR "%SYSTEMROOT%\Borrar_Temp.bat" /RL HIGHEST /F
regedit.exe /s "Borrar_Temp.reg"
ECHO.
ECHO.
DEL /F /S /Q  "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Start TightVNC Service.lnk"
DEL /F /S /Q  "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\1 Start TightVNC Service.lnk"
DEL /F /S /Q  "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\OneDrive.lnk"
COPY /D /V /Y "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\TightVNC\TightVNC Server (Service Mode)\Start TightVNC Service.lnk" "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs"
GOTO REINICIAR

:FIRVTDA_64
CLS
ECHO Instalando...
ECHO.
ECHO  ********* 90%% ( Mozilla U. )
ECHO --------------------------------------------
"%PROGRAMFILES(X86)%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  *********** 100%% ( LibreOffice )
ECHO --------------------------------------------
LibreOffice_64.msi /passive 
CLS
ECHO Instalando...
ECHO.
ECHO  *********** 100%% ( LibreOffice )
ECHO --------------------------------------------
LibreOffice_helppack.msi /passive 
CLS
ECHO Instalando...
ECHO.
ECHO  *********** 100%% ( K-Lite Codec )
ECHO --------------------------------------------
Codec_Pack.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /SP-
ECHO.
assoc .pdf=AcroExch.Document.DC
assoc .url=InternetShortcut
REM disable java update by policy 
reg add "HKLM\SOFTWARE\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T
REG_DWORD /D 0 /F
if defined programfiles(x86) reg add "HKLM\SOFTWARE\Wow6432Node\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T REG_DWORD /D 0 /F
REM Remove java update scheduler
REG DELETE "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v
"SunJavaUpdateSched" /f
if defined programfiles(x86) reg delete "HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run" /v "SunJavaUpdateSched" /f
REM NoSoloHacking.info
REM kill java updater if started
taskkill /IM jucheck.exe /F
taskkill IM juscheck.exe /F
@ECHO.
certutil -f -v -addstore -enterprise root SecurityAppliance_SSL_CA_FINAL.pem
MD "C:\Instaladores_JH"
COPY /D /V /Y "SecurityAppliance_SSL_CA_FINAL.pem" "C:\Instaladores_JH"
ECHO.
JAHER_NEW.deskthemepack
MOTOMARKET.deskthemepack
REG DELETE HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run /f
[-HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run]
COPY /D /V /Y "Borrar_Temp.bat" "C:\Windows"
schtasks /Create /TN "Depurar" /SC ONLOGON /TR "%SYSTEMROOT%\Borrar_Temp.bat" /RL HIGHEST /F
ECHO.
ECHO.
DEL /F /S /Q  "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Start TightVNC Service.lnk"
DEL /F /S /Q  "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\1 Start TightVNC Service.lnk"
DEL /F /S /Q  "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\OneDrive.lnk"
COPY /D /V /Y "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\TightVNC\TightVNC Server (Service Mode)\Start TightVNC Service.lnk" "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs"
GOTO REINICIAR

ECHO           [--------------------(FIERE CON OFFICE)-----------------------]
ECHO           [--------------------(FIERE SIN OFFICE)-----------------------]

:FIR_DELSIN
CLS
MODE CON cols=50 lines=5 
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto FIRVTDS_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto FIRVTDS_64)
ECHO.

:FIRVTDS_32
CLS
ECHO Instalando...
ECHO.
ECHO  *********** 100%% ( LibreOffice )
ECHO --------------------------------------------
"%PROGRAMFILES%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
ECHO.
assoc .pdf=AcroExch.Document.DC
assoc .url=InternetShortcut
REM disable java update by policy 
reg add "HKLM\SOFTWARE\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T
REG_DWORD /D 0 /F
if defined programfiles(x86) reg add "HKLM\SOFTWARE\Wow6432Node\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T REG_DWORD /D 0 /F
REM Remove java update scheduler
REG DELETE "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v
"SunJavaUpdateSched" /f
if defined programfiles(x86) reg delete "HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run" /v "SunJavaUpdateSched" /f
REM NoSoloHacking.info
REM kill java updater if started
taskkill /IM jucheck.exe /F
taskkill IM juscheck.exe /F
@ECHO.
certutil -f -v -addstore -enterprise root SecurityAppliance_SSL_CA_FINAL.pem
MD "C:\Instaladores_JH"
COPY /D /V /Y "SecurityAppliance_SSL_CA_FINAL.pem" "C:\Instaladores_JH"
ECHO.
JAHER_NEW.deskthemepack
MOTOMARKET.deskthemepack
REG DELETE HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run /f
[-HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run]
COPY /D /V /Y "Borrar_Temp.bat" "C:\Windows"
schtasks /Create /TN "Depurar" /SC ONLOGON /TR "%SYSTEMROOT%\Borrar_Temp.bat" /RL HIGHEST /F
CLS
ECHO Instalando...
ECHO.
ECHO  *********** 100%% ( K-Lite Codec )
ECHO --------------------------------------------
Codec_Pack.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /SP-
ECHO.
ECHO.
DEL /F /S /Q  ""%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Start TightVNC Service.lnk"
COPY /D /V /Y "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\TightVNC\TightVNC Server (Service Mode)\Start TightVNC Service.lnk" "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs"
GOTO REINICIAR

:FIRVTDS_64
CLS
ECHO Instalando...
ECHO.
ECHO  *********** 100%% ( LibreOffice )
ECHO --------------------------------------------
"%PROGRAMFILES(X86)%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
ECHO.
assoc .pdf=AcroExch.Document.DC
assoc .url=InternetShortcut
REM disable java update by policy 
reg add "HKLM\SOFTWARE\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T
REG_DWORD /D 0 /F
if defined programfiles(x86) reg add "HKLM\SOFTWARE\Wow6432Node\JavaSoft\Java Update\Policy" /V EnableJavaUpdate /T REG_DWORD /D 0 /F
REM Remove java update scheduler
REG DELETE "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /v
"SunJavaUpdateSched" /f
if defined programfiles(x86) reg delete "HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run" /v "SunJavaUpdateSched" /f
REM NoSoloHacking.info
REM kill java updater if started
taskkill /IM jucheck.exe /F
taskkill IM juscheck.exe /F
@ECHO.
certutil -f -v -addstore -enterprise root SecurityAppliance_SSL_CA_FINAL.pem
MD "C:\Instaladores_JH"
COPY /D /V /Y "SecurityAppliance_SSL_CA_FINAL.pem" "C:\Instaladores_JH"
ECHO.
JAHER_NEW.deskthemepack
MOTOMARKET.deskthemepack
REG DELETE HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run /f
[-HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run]
COPY /D /V /Y "Borrar_Temp.bat" "C:\Windows"
schtasks /Create /TN "Depurar" /SC ONLOGON /TR "%SYSTEMROOT%\Borrar_Temp.bat" /RL HIGHEST /F
CLS
ECHO Instalando...
ECHO.
ECHO  *********** 100%% ( K-Lite Codec )
ECHO --------------------------------------------
Codec_Pack.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /SP-
ECHO.
ECHO.
DEL /F /S /Q  "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Start TightVNC Service.lnk"
DEL /F /S /Q  "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\1 Start TightVNC Service.lnk"
DEL /F /S /Q  "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\OneDrive.lnk"
COPY /D /V /Y "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\TightVNC\TightVNC Server (Service Mode)\Start TightVNC Service.lnk" "%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs"
GOTO REINICIAR
ECHO.
ECHO           [--------------------(FIERE SIN OFFICE)-----------------------]
ECHO.
ECHO           [--------------------(CON OFFICE)-----------------------]
ECHO.

:UPDCON
CLS
COLOR 07
MODE CON cols=50 lines=9
TASKKILL /F /IM explorer.exe
ECHO.
ECHO  [************************************]
ECHO              - IMPORTANTE -
ECHO.
ECHO      CUANDO TERMINE POR COMPLETO EL 
ECHO       INSTALADOR SE AUTO REINICIARA 
ECHO              EL COMPUTADOR 
ECHO  [************************************] 
>nul ping -n 10 localhost 
CLS 
Color 1B   
MODE CON cols=50 lines=5 
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  * 10%% ( Instalado )
ECHO --------------------------------------------
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\security\exception.sites"
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\deployment.properties"
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  ** 20%% ( WinRAR. )
ECHO --------------------------------------------
WinRAR.exe
GOTO MZ_RUN

:MZ_RUN
if %PROCESSOR_ARCHITECTURE%==x86 (goto MZ_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto MZ_64)

:MZ_32
COLOR 07
ECHO.
ECHO Instalando...
ECHO.
ECHO  *** 30%% ( Instalado JAVA 32bit)
ECHO --------------------------------------------
Java_32.exe /s
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  **** 40%% ( Instalado JAVA 32bit)
ECHO --------------------------------------------
Java_Conf.exe
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
Firefox_32.msi -ms
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
START FirefoxMarcadores_64 FirefoxMarcadores_64.exe /REALTIME
ECHO.
%SystemRoot%/SysWOW32/OneDriveSetup.exe /uninstall
CLS  
ECHO Instalando...
ECHO.
ECHO  ****** 60%% ( Adobe Reader )
ECHO --------------------------------------------
AdbeRdr.exe /sPB
CLS
ECHO Instalando...
ECHO.
ECHO  ******* 70%% ( Adobe Pack )
ECHO --------------------------------------------
AdbeRdr_FontPack.msi /passive
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( Adobe Pack )
ECHO --------------------------------------------
REGEDIT /S "AdobeConfig.reg"
GOTO FIR_DELCON


:MZ_64
COLOR 07
ECHO.
ECHO Instalando...
ECHO.
ECHO  *** 30%% ( Instalado JAVA 64bit)
ECHO --------------------------------------------
Java_64.exe /s
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  **** 40%% ( Instalado JAVA 64bit)
ECHO --------------------------------------------
Java_Conf.exe
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
Firefox_64.msi -ms
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
START FirefoxMarcadores_64 FirefoxMarcadores_64.exe /REALTIME
ECHO.
%SystemRoot%/SysWOW32/OneDriveSetup.exe /uninstall
CLS  
ECHO Instalando...
ECHO.
ECHO  ****** 60%% ( Adobe Reader )
ECHO --------------------------------------------
AdbeRdr.exe /sPB
CLS
ECHO Instalando...
ECHO.
ECHO  ******* 70%% ( Adobe Pack )
ECHO --------------------------------------------
AdbeRdr_FontPack.msi /passive
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( Adobe Pack )
ECHO --------------------------------------------
REGEDIT /S "AdobeConfig.reg"
GOTO FIR_DELCON

ECHO           [--------------------(CON OFFICE)-----------------------]
ECHO           [--------------------(SIN OFFICE)-----------------------]


:UPDSIN
CLS
COLOR 07
MODE CON cols=50 lines=9
TASKKILL /F /IM explorer.exe
ECHO.
ECHO  [************************************]
ECHO              - IMPORTANTE -
ECHO.
ECHO      CUANDO TERMINE POR COMPLETO EL 
ECHO       INSTALADOR SE AUTO REINICIARA 
ECHO              EL COMPUTADOR 
ECHO  [************************************] 
>nul ping -n 10 localhost 
CLS  
MODE CON cols=50 lines=5 
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  * 10%% ( Instalado )
ECHO --------------------------------------------
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\security\exception.sites"
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\deployment.properties"
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  ** 20%% ( WinRAR. )
ECHO --------------------------------------------
WinRAR.exe
GOTO MZ_RUN

:MZ_RUN
if %PROCESSOR_ARCHITECTURE%==x86 (goto MZ_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto MZ_64)

:MZ_32
COLOR 07
ECHO.
ECHO Instalando...
ECHO.
ECHO  *** 30%% ( Instalado JAVA 32bit)
ECHO --------------------------------------------
Java_32.exe /s
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  **** 40%% ( Instalado JAVA 32bit)
ECHO --------------------------------------------
Java_Conf.exe
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
Firefox_32.msi -ms
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
START FirefoxMarcadores_64 FirefoxMarcadores_64.exe /REALTIME
ECHO.
%SystemRoot%/SysWOW32/OneDriveSetup.exe /uninstall
CLS 
ECHO Instalando...
ECHO.
ECHO  ****** 60%% ( Adobe Reader )
ECHO --------------------------------------------
AdbeRdr.exe /sPB
CLS
ECHO Instalando...
ECHO.
ECHO  ******* 70%% ( Adobe Pack )
ECHO --------------------------------------------
AdbeRdr_FontPack.msi /passive
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( Adobe Pack )
ECHO --------------------------------------------
REGEDIT /S "AdobeConfig.reg"
GOTO FIR_DELSIN


:MZ_64
COLOR 07
ECHO.
ECHO Instalando...
ECHO.
ECHO  *** 30%% ( Instalado JAVA 64bit)
ECHO --------------------------------------------
Java_64.exe /s
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  **** 40%% ( Instalado JAVA 64bit)
ECHO --------------------------------------------
Java_Conf.exe
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
Firefox_64.msi -ms
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
START FirefoxMarcadores_64 FirefoxMarcadores_64.exe /REALTIME
ECHO.
%SystemRoot%/SysWOW32/OneDriveSetup.exe /uninstall
CLS  
ECHO Instalando...
ECHO.
ECHO  ****** 60%% ( Adobe Reader )
ECHO --------------------------------------------
AdbeRdr.exe /sPB
CLS
ECHO Instalando...
ECHO.
ECHO  ******* 70%% ( Adobe Reader )
ECHO --------------------------------------------
AdbeRdr_FontPack.msi /passive
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( Adobe Pack )
ECHO --------------------------------------------
REGEDIT /S "AdobeConfig.reg"
GOTO FIR_DELSIN

ECHO           [--------------------(SIN OFFICE)-----------------------]
ECHO           [--------------------(CON OFFICE CAJA )-----------------]

:UPDCAJ
CLS
Color 1B
MODE CON cols=50 lines=9
TASKKILL /F /IM explorer.exe
ECHO.
ECHO  [************************************]
ECHO              - IMPORTANTE -
ECHO.
ECHO      CUANDO TERMINE POR COMPLETO EL 
ECHO       INSTALADOR SE AUTO REINICIARA 
ECHO              EL COMPUTADOR 
ECHO  [************************************] 
>nul ping -n 10 localhost  
CLS   
MODE CON cols=50 lines=5 
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  * 10%% ( Instalado )
ECHO --------------------------------------------
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\security\exception.sites"
DEL /F /S /Q "%USERPROFILE%\AppData\LocalLow\Sun\Java\Deployment\deployment.properties"
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  ** 20%% ( WinRAR. )
ECHO --------------------------------------------
WinRAR.exe
GOTO MZ_RUN

:MZ_RUN
if %PROCESSOR_ARCHITECTURE%==x86 (goto MZ_32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto MZ_64)

:MZ_32
COLOR 07
ECHO.
ECHO Instalando...
ECHO.
ECHO  *** 30%% ( Instalado JAVA 32bit)
ECHO --------------------------------------------
Java_32.exe /s
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  **** 40%% ( Instalado JAVA 32bit)
ECHO --------------------------------------------
Java_Conf.exe
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
Firefox_32.msi -ms
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
START FirefoxMarcadores_64 FirefoxMarcadores_64.exe /REALTIME
ECHO.
%SystemRoot%/SysWOW32/OneDriveSetup.exe /uninstall
CLS 
ECHO Instalando...
ECHO.
ECHO  ****** 60%% ( Adobe Reader )
ECHO --------------------------------------------
AdbeRdr.exe /sPB
CLS
ECHO Instalando...
ECHO.
ECHO  ******* 70%% ( Adobe Reader )
ECHO --------------------------------------------
AdbeRdr_FontPack.msi /passive
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( Adobe Pack )
ECHO --------------------------------------------
REGEDIT /S "AdobeConfig.reg"
CLS
ECHO Instalando...
ECHO.
ECHO  ********* 85%% ( Mozilla Thunderbird )
ECHO --------------------------------------------
RD /S /Q "C:\Program Files\Mozilla Thunderbird"
CLS
ECHO Instalando...
ECHO.
ECHO  ********* 85%% ( Mozilla Thunderbird )
ECHO --------------------------------------------
Thunderbird_32bit.exe -ms
ECHO.
"%PROGRAMFILES(X86)%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
ECHO.
GOTO FIR_DELCON



:MZ_64
COLOR 07
ECHO.
ECHO Instalando...
ECHO.
ECHO  *** 30%% ( Instalado JAVA 64bit)
ECHO --------------------------------------------
Java_64.exe /s
CLS
ECHO.
ECHO Instalando...
ECHO.
ECHO  **** 40%% ( Instalado JAVA 64bit)
ECHO --------------------------------------------
Java_Conf.exe
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
Firefox_64.msi -ms
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%APPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
RD /S /Q "%LOCALAPPDATA%\Mozilla\Firefox"
CLS
ECHO Instalando...
ECHO.
ECHO  ***** 50%% ( Mozilla )
ECHO --------------------------------------------
START FirefoxMarcadores_64 FirefoxMarcadores_64.exe /REALTIME
ECHO.
%SystemRoot%/SysWOW32/OneDriveSetup.exe /uninstall
CLS  
ECHO Instalando...
ECHO.
ECHO  ****** 60%% ( Adobe Reader )
ECHO --------------------------------------------
AdbeRdr.exe /sPB
CLS
ECHO Instalando...
ECHO.
ECHO  ******* 70%% ( Adobe Reader )
ECHO --------------------------------------------
AdbeRdr_FontPack.msi /passive
CLS
ECHO Instalando...
ECHO.
ECHO  ******** 80%% ( Adobe Pack )
ECHO --------------------------------------------
REGEDIT /S "AdobeConfig.reg"
CLS
ECHO Instalando...
ECHO.
ECHO  ********* 85%% ( Mozilla Thunderbird )
ECHO --------------------------------------------
RD /S /Q "C:\Program Files\Mozilla Thunderbird"
CLS
ECHO Instalando...
ECHO.
ECHO  ********* 85%% ( Mozilla Thunderbird )
ECHO --------------------------------------------
Thunderbird_64bit.exe -ms
ECHO.
"%PROGRAMFILES(X86)%\Mozilla Maintenance Service\Uninstall.exe" /S /NCRC
ECHO.
GOTO FIR_DELCON

ECHO           [--------------------(CON OFFICE CAJA )-----------------]
ECHO           [--------------------(SIN OFFICE)-----------------------]



ECHO           [----------------------------------------------------(LISTO)



:DESINSTALAR
CLS
ECHO.
if %PROCESSOR_ARCHITECTURE%==x86 (goto BORRAR32) else if %PROCESSOR_ARCHITECTURE%==AMD64 (goto BORRAR64)
ECHO.

:BORRAR32
DEL /F /S /Q "%userprofile%\Desktop\JAHER.lnk"
DEL /F /S /Q "%Public%\Desktop\JAHER.lnk"
RD /S /Q "C:\BACKUSPARK"
RD /S /Q "C:\BACKUTHUND"
taskkill /f /t /im "EditV32.exe"
taskkill /f /t /im "EditV64.exe"
RD /S /Q "Link"
start "unins000.exe" "%programfiles%\JAHER\unins000.exe" /SILENT
Exit

:BORRAR64
DEL /F /S /Q "%userprofile%\Desktop\JAHER.lnk"
DEL /F /S /Q "%Public%\Desktop\JAHER.lnk"
RD /S /Q "C:\BACKUSPARK"
RD /S /Q "C:\BACKUTHUND"
taskkill /f /t /im "EditV32.exe"
taskkill /f /t /im "EditV64.exe"
RD /S /Q "Link"
start "unins000.exe" "%ProgramFiles(x86)%\JAHER\unins000.exe" /SILENT
Exit

