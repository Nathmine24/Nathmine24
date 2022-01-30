Quote: cls
@ECHO OFF
title Folder Private
if EXIST "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}" goto UNLOCK
if NOT EXIST Private goto MDLOCKER
:CONFIRM
echo voulez vous verrouiller le dossier private  (Y/N)
set/p "cho=>"
if %cho%==Y goto LOCK
if %cho%==y goto LOCK
if %cho%==n goto END
if %cho%==N goto END
echo Mauvais choix tapez Y pour oui et N pour non.
goto CONFIRM
:LOCK
ren Private "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
attrib +h +s "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
echo Dossier verrouillé
goto End
:UNLOCK
echo Entrez le mot de passe pour accèder au dossier verrouillé
set/p "pass=>"
if NOT %pass%== Mot_de_passe goto FAIL
attrib -h -s "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
ren "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}" Private
echo Dossier déverrouillé
goto End
:FAIL
echo Mot de passe invalide
goto end
:MDLOCKER
md Private
echo dossier Private créé 
goto End
:End
