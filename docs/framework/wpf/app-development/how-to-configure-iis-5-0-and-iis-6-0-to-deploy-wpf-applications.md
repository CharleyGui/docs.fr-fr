---
title: 'Procédure : Configurer IIS 5.0 et IIS 6.0 pour déployer des applications WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
ms.openlocfilehash: a1e58aef6d02b6cf05a126b6afd25ab2a6004002
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972294"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>Procédure : Configurer IIS 5.0 et IIS 6.0 pour déployer des applications WPF

Vous pouvez déployer une [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application à partir de la plupart des serveurs Web, à condition qu’ils soient configurés avec les types MIME (Multipurpose Internet Mail Extensions) appropriés. Par défaut, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] est configuré avec ces types MIME, mais [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] et [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] ne le sont pas.

Cette rubrique décrit comment configurer [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] et [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] pour déployer des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

> [!NOTE]
> Vous pouvez vérifier la chaîne *UserAgent* dans le registre pour déterminer si un système a .NET Framework installé. Pour plus d’informations et pour obtenir un script qui examine la chaîne *UserAgent* afin de déterminer si .NET Framework est installé sur un système, consultez [détecter si la .NET Framework 3,0 est installée](how-to-detect-whether-the-net-framework-3-0-is-installed.md).

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a>Régler le paramètre d’expiration du contenu

Vous devez régler le paramètre d’expiration du contenu sur 1 minute. La procédure suivante décrit comment faire avec [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].

1. Cliquez sur le menu **Démarrer**, pointez sur **Outils d’administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)** . Vous pouvez également lancer cette application à partir de la ligne de commande avec « %SystemRoot%\system32\inetsrv\iis.msc ».

2. Développez l’arborescence [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] jusqu’à trouver le nœud **Site Web par défaut**.

3. Cliquez avec le bouton droit sur **Site Web par défaut** et sélectionnez **Propriétés** dans le menu contextuel.

4. Sélectionnez l’onglet **En-têtes HTTP** et cliquez sur « Activer l’expiration de contenu ».

5. Paramétrez le contenu pour qu’il expire après une minute.

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a>Inscrire des types MIME et des extensions de fichiers

Vous devez inscrire plusieurs types MIME et extensions de fichier afin que le navigateur sur le système du client puisse charger le gestionnaire approprié. Vous devez ajouter les types suivants :

|Extension|Type MIME|
|---------------|---------------|
|.manifest|application/manifest|
|.xaml|application/xaml+xml|
|.application|application/x-ms-application|
|.xbap|application/x-ms-xbap|
|.deploy|application/octet-stream|
|.xps|application/vnd.ms-xpsdocument|

> [!NOTE]
> Vous n’avez pas besoin d’enregistrer les types MIME ou les extensions de fichier sur les systèmes clients. Ils sont inscrits automatiquement lorsque vous installez Microsoft .NET Framework.

L’exemple Microsoft Visual Basic Scripting Edition (VBScript) suivant ajoute automatiquement les types MIME nécessaires à [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]. Pour utiliser le script, copiez le code dans un fichier .vbs sur votre serveur. Ensuite, exécutez le script en exécutant le fichier à partir de la ligne de commande ou en double-cliquant sur le fichier dans [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].

```vb
' This script adds the necessary Windows Presentation Foundation MIME types
' to an IIS Server.
' To use this script, just double-click or execute it from a command line.
' Running this script multiple times results in multiple entries in the IIS MimeMap.

Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec
Const ADS_PROPERTY_UPDATE = 2

' Set the MIME types to be added
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _
    "application/xaml+xml", ".application", "application/x-ms-application", _
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _
    ".xps", "application/vnd.ms-xpsdocument")

' Get the MimeMap object
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")

' Call AddMimeType for every pair of extension/MIME type
For counter = 0 to UBound(MimeTypesToAddArray) Step 2
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)
Next

' Create a Shell object
Set WshShell = CreateObject("WScript.Shell")

' Stop and Start the IIS Service
Set oExec = WshShell.Exec("net stop w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = WshShell.Exec("net start w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = Nothing

' Report status to user
WScript.Echo "Windows Presentation Foundation MIME types have been registered."

' AddMimeType Sub
Sub AddMimeType (Ext, MType)

    ' Get the mappings from the MimeMap property.
    MimeMapArray = MimeMapObj.GetEx("MimeMap")

    ' Add a new mapping.
    i = UBound(MimeMapArray) + 1
    ReDim Preserve MimeMapArray(i)
    Set MimeMapArray(i) = CreateObject("MimeMap")
    MimeMapArray(i).Extension = Ext
    MimeMapArray(i).MimeType = MType
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray
    MimeMapObj.SetInfo

End Sub
```

> [!NOTE]
> L’exécution de ce script plusieurs fois crée plusieurs entrées de mappage [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] MIME [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] dans la métabase ou.

Après avoir exécuté ce script, vous ne verrez peut-être pas de types [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] MIME [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] supplémentaires à partir du ou [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)]de. Toutefois, ces types MIME ont été ajoutés à la [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] métabase [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] ou. Le script suivant affiche tous les types MIME dans la [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] métabase ou. [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)]

```vb
' This script lists the MIME types for an IIS Server.
' To use this script, just double-click or execute it from a command line
' by calling cscript.exe

dim mimeMapEntry, allMimeMaps

' Get the MimeMap object.
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")
allMimeMaps = mimeMapEntry.GetEx("MimeMap")

' Display the mappings in the table.
For Each mimeMap In allMimeMaps
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")
Next
```

Enregistrez le script en tant que fichier `.vbs` (par exemple, `DiscoverIISMimeTypes.vbs`) et exécutez-le à partir de l’invite de commandes à l’aide de la commande suivante :

```console
cscript DiscoverIISMimeTypes.vbs
```
