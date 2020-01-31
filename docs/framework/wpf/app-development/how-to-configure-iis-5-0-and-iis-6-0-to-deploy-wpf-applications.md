---
title: Guide pratique pour configurer IIS 5.0 et IIS 6.0 pour déployer des applications WPF
titleSuffix: ''
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
ms.openlocfilehash: d557ac6cd380edcbc93b5315f6356697817274bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740406"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="8f950-102">Guide pratique pour configurer IIS 5.0 et IIS 6.0 pour déployer des applications WPF</span><span class="sxs-lookup"><span data-stu-id="8f950-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>

<span data-ttu-id="8f950-103">Vous pouvez déployer une application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] à partir de la plupart des serveurs Web, à condition qu’ils soient configurés avec les types MIME (Multipurpose Internet Mail Extensions) appropriés.</span><span class="sxs-lookup"><span data-stu-id="8f950-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate Multipurpose Internet Mail Extensions (MIME) types.</span></span> <span data-ttu-id="8f950-104">Par défaut, Microsoft Internet Information Services (IIS) 7,0 est configuré avec ces types MIME, mais Microsoft Internet Information Services (IIS) 5,0 et Microsoft Internet Information Services (IIS) 6,0 ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="8f950-104">By default, Microsoft Internet Information Services (IIS) 7.0 is configured with these MIME types, but Microsoft Internet Information Services (IIS) 5.0 and Microsoft Internet Information Services (IIS) 6.0 are not.</span></span>

<span data-ttu-id="8f950-105">Cette rubrique explique comment configurer Microsoft Internet Information Services (IIS) 5,0 et Microsoft Internet Information Services (IIS) 6,0 pour déployer des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f950-105">This topic describes how to configure Microsoft Internet Information Services (IIS) 5.0 and Microsoft Internet Information Services (IIS) 6.0 to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>

> [!NOTE]
> <span data-ttu-id="8f950-106">Vous pouvez vérifier la chaîne *UserAgent* dans le registre pour déterminer si un système a .NET Framework installé.</span><span class="sxs-lookup"><span data-stu-id="8f950-106">You can check the *UserAgent* string in the registry to determine whether a system has .NET Framework installed.</span></span> <span data-ttu-id="8f950-107">Pour plus d’informations et pour obtenir un script qui examine la chaîne *UserAgent* afin de déterminer si .NET Framework est installé sur un système, consultez [détecter si la .NET Framework 3,0 est installée](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span><span class="sxs-lookup"><span data-stu-id="8f950-107">For details and a script that examines the *UserAgent* string to determine whether .NET Framework is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="8f950-108">Régler le paramètre d’expiration du contenu</span><span class="sxs-lookup"><span data-stu-id="8f950-108">Adjust the Content Expiration Setting</span></span>

<span data-ttu-id="8f950-109">Vous devez régler le paramètre d’expiration du contenu sur 1 minute.</span><span class="sxs-lookup"><span data-stu-id="8f950-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="8f950-110">La procédure suivante décrit comment faire avec IIS.</span><span class="sxs-lookup"><span data-stu-id="8f950-110">The following procedure outlines how to do this with IIS.</span></span>

1. <span data-ttu-id="8f950-111">Cliquez sur le menu **Démarrer**, pointez sur **Outils d’administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="8f950-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="8f950-112">Vous pouvez également lancer cette application à partir de la ligne de commande avec « %SystemRoot%\system32\inetsrv\iis.msc ».</span><span class="sxs-lookup"><span data-stu-id="8f950-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>

2. <span data-ttu-id="8f950-113">Développez l’arborescence IIS jusqu’à ce que vous trouviez le nœud **site Web par défaut** .</span><span class="sxs-lookup"><span data-stu-id="8f950-113">Expand the IIS tree until you find the **Default Web site** node.</span></span>

3. <span data-ttu-id="8f950-114">Cliquez avec le bouton droit sur **Site Web par défaut** et sélectionnez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="8f950-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>

4. <span data-ttu-id="8f950-115">Sélectionnez l’onglet **En-têtes HTTP** et cliquez sur « Activer l’expiration de contenu ».</span><span class="sxs-lookup"><span data-stu-id="8f950-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>

5. <span data-ttu-id="8f950-116">Paramétrez le contenu pour qu’il expire après une minute.</span><span class="sxs-lookup"><span data-stu-id="8f950-116">Set the content to expire after 1 minute.</span></span>

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="8f950-117">Inscrire des types MIME et des extensions de fichiers</span><span class="sxs-lookup"><span data-stu-id="8f950-117">Register MIME Types and File Extensions</span></span>

<span data-ttu-id="8f950-118">Vous devez inscrire plusieurs types MIME et extensions de fichier afin que le navigateur sur le système du client puisse charger le gestionnaire approprié.</span><span class="sxs-lookup"><span data-stu-id="8f950-118">You must register several MIME types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="8f950-119">Vous devez ajouter les types suivants :</span><span class="sxs-lookup"><span data-stu-id="8f950-119">You need to add the following types:</span></span>

|<span data-ttu-id="8f950-120">Extension</span><span class="sxs-lookup"><span data-stu-id="8f950-120">Extension</span></span>|<span data-ttu-id="8f950-121">Type MIME</span><span class="sxs-lookup"><span data-stu-id="8f950-121">MIME Type</span></span>|
|---------------|---------------|
|<span data-ttu-id="8f950-122">.manifest</span><span class="sxs-lookup"><span data-stu-id="8f950-122">.manifest</span></span>|<span data-ttu-id="8f950-123">application/manifest</span><span class="sxs-lookup"><span data-stu-id="8f950-123">application/manifest</span></span>|
|<span data-ttu-id="8f950-124">.xaml</span><span class="sxs-lookup"><span data-stu-id="8f950-124">.xaml</span></span>|<span data-ttu-id="8f950-125">application/xaml+xml</span><span class="sxs-lookup"><span data-stu-id="8f950-125">application/xaml+xml</span></span>|
|<span data-ttu-id="8f950-126">.application</span><span class="sxs-lookup"><span data-stu-id="8f950-126">.application</span></span>|<span data-ttu-id="8f950-127">application/x-ms-application</span><span class="sxs-lookup"><span data-stu-id="8f950-127">application/x-ms-application</span></span>|
|<span data-ttu-id="8f950-128">.xbap</span><span class="sxs-lookup"><span data-stu-id="8f950-128">.xbap</span></span>|<span data-ttu-id="8f950-129">application/x-ms-xbap</span><span class="sxs-lookup"><span data-stu-id="8f950-129">application/x-ms-xbap</span></span>|
|<span data-ttu-id="8f950-130">.deploy</span><span class="sxs-lookup"><span data-stu-id="8f950-130">.deploy</span></span>|<span data-ttu-id="8f950-131">application/octet-stream</span><span class="sxs-lookup"><span data-stu-id="8f950-131">application/octet-stream</span></span>|
|<span data-ttu-id="8f950-132">.xps</span><span class="sxs-lookup"><span data-stu-id="8f950-132">.xps</span></span>|<span data-ttu-id="8f950-133">application/vnd.ms-xpsdocument</span><span class="sxs-lookup"><span data-stu-id="8f950-133">application/vnd.ms-xpsdocument</span></span>|

> [!NOTE]
> <span data-ttu-id="8f950-134">Vous n’avez pas besoin d’enregistrer les types MIME ou les extensions de fichier sur les systèmes clients.</span><span class="sxs-lookup"><span data-stu-id="8f950-134">You do not need to register MIME types or file extensions on client systems.</span></span> <span data-ttu-id="8f950-135">Ils sont inscrits automatiquement lorsque vous installez Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f950-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>

<span data-ttu-id="8f950-136">L’exemple Microsoft Visual Basic Scripting Edition (VBScript) suivant ajoute automatiquement les types MIME nécessaires à IIS.</span><span class="sxs-lookup"><span data-stu-id="8f950-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary MIME types to IIS.</span></span> <span data-ttu-id="8f950-137">Pour utiliser le script, copiez le code dans un fichier .vbs sur votre serveur.</span><span class="sxs-lookup"><span data-stu-id="8f950-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="8f950-138">Ensuite, exécutez le script en exécutant le fichier à partir de la ligne de commande ou en double-cliquant sur le fichier dans l’Explorateur Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="8f950-138">Then, run the script by running the file from the command line or double-clicking the file in Microsoft Windows Explorer.</span></span>

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
> <span data-ttu-id="8f950-139">L’exécution de ce script plusieurs fois crée plusieurs entrées de mappage MIME dans la métabase Microsoft Internet Information Services (IIS) 5,0 ou Microsoft Internet Information Services (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="8f950-139">Running this script multiple times creates multiple MIME map entries in the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span>

<span data-ttu-id="8f950-140">Une fois que vous avez exécuté ce script, vous ne verrez peut-être pas de types MIME supplémentaires à partir de Microsoft Internet Information Services (IIS) 5,0 ou Microsoft Internet Information Services (IIS) 6,0 Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="8f950-140">After you have run this script, you may not see additional MIME types from the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 Microsoft Management Console (MMC).</span></span> <span data-ttu-id="8f950-141">Toutefois, ces types MIME ont été ajoutés à la métabase Microsoft Internet Information Services (IIS) 5,0 ou Microsoft Internet Information Services (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="8f950-141">However, these MIME types have been added to the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span> <span data-ttu-id="8f950-142">Le script suivant affiche tous les types MIME de la métabase Microsoft Internet Information Services (IIS) 5,0 ou Microsoft Internet Information Services (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="8f950-142">The following script will display all the MIME types in the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span>

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

<span data-ttu-id="8f950-143">Enregistrez le script en tant que fichier `.vbs` (par exemple, `DiscoverIISMimeTypes.vbs`) et exécutez-le à partir de l’invite de commandes à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8f950-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>

```console
cscript DiscoverIISMimeTypes.vbs
```
