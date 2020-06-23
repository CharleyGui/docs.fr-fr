---
title: Outil d'inscription ServiceModel (ServiceModelReg.exe)
description: Utilisez cet outil en ligne de commande pour gérer l’inscription des composants WCF et WF sur un ordinateur unique si vous rencontrez des problèmes avec l’activation du service.
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 347b1b8071abe7d8eb7e16ffd879c1fdb9825bc7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245893"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="ba4c2-103">Outil d'inscription ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="ba4c2-103">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="ba4c2-104">Cet outil en ligne de commande permet de gérer l'inscription des composants WCF et WF sur un ordinateur unique.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-104">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="ba4c2-105">Dans des circonstances normales vous n'avez pas à utiliser cet outil, car les composants WCF et WF sont configurés lors de l'installation.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-105">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="ba4c2-106">Mais si vous rencontrez des problèmes avec l'activation de service, vous pouvez essayer d'inscrire les composants à l'aide de cet outil.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-106">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba4c2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba4c2-107">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="ba4c2-108">Notes</span><span class="sxs-lookup"><span data-stu-id="ba4c2-108">Remarks</span></span>  
 <span data-ttu-id="ba4c2-109">Cet outil se trouve à l'emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="ba4c2-109">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="ba4c2-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ba4c2-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="ba4c2-111">Lorsque l’outil d’inscription ServiceModel est exécuté sur Windows Vista, la boîte de dialogue **fonctionnalités de Windows** peut ne pas refléter le fait que l’option d' **Activation Windows Communication Foundation http** sous **Microsoft .NET Framework 3,0** est activée.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-111">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="ba4c2-112">Vous pouvez accéder à la boîte de dialogue **fonctionnalités de Windows** en cliquant sur **Démarrer**, puis sur **exécuter** et en tapant **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-112">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="ba4c2-113">Les tableaux suivants décrivent les options qui peuvent être utilisées avec ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-113">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="ba4c2-114">Option</span><span class="sxs-lookup"><span data-stu-id="ba4c2-114">Option</span></span>|<span data-ttu-id="ba4c2-115">Description</span><span class="sxs-lookup"><span data-stu-id="ba4c2-115">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="ba4c2-116">Installe les composants WCF et WF.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-116">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="ba4c2-117">Désinstalle les composants WCF et WF.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-117">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="ba4c2-118">Répare les composants WCF et WF.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-118">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="ba4c2-119">Installe les composants WCF et WF spécifiés avec –c.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-119">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="ba4c2-120">Désinstalle les composants WCF et WF spécifiés avec –c.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-120">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="ba4c2-121">Installe ou désinstalle un composant :</span><span class="sxs-lookup"><span data-stu-id="ba4c2-121">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="ba4c2-122">-httpnamespace – réservation d’espace de noms HTTP</span><span class="sxs-lookup"><span data-stu-id="ba4c2-122">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="ba4c2-123">-tcpportsharing – service de partage de ports TCP</span><span class="sxs-lookup"><span data-stu-id="ba4c2-123">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="ba4c2-124">-tcpactivation – service d’activation TCP (non pris en charge sur .NET 4 Client Profile)</span><span class="sxs-lookup"><span data-stu-id="ba4c2-124">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="ba4c2-125">-namedpipeactivation – service d’activation de canal nommé (non pris en charge sur .NET 4 Client Profile</span><span class="sxs-lookup"><span data-stu-id="ba4c2-125">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="ba4c2-126">-MsmqActivation – service d’activation MSMQ (non pris en charge sur .NET 4 Client Profile</span><span class="sxs-lookup"><span data-stu-id="ba4c2-126">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="ba4c2-127">-ETW – manifestes de suivi d’événements ETW (Windows Vista ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="ba4c2-127">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="ba4c2-128">Mode silencieux (enregistrement des erreurs d'affichage uniquement)</span><span class="sxs-lookup"><span data-stu-id="ba4c2-128">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="ba4c2-129">Mode documenté.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-129">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="ba4c2-130">Supprime le message de copyright et de bannière.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-130">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="ba4c2-131">Affiche le texte de l'aide.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-131">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="ba4c2-132">Résolution de l'erreur FileLoadException</span><span class="sxs-lookup"><span data-stu-id="ba4c2-132">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="ba4c2-133">Si vous avez installé des versions précédentes de WCF sur votre ordinateur, vous risquez d’obtenir une `FileLoadFoundException` erreur quand vous exécutez l’outil ServiceModelReg pour inscrire une nouvelle installation.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-133">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="ba4c2-134">Cela peut se produire même si vous avez supprimé manuellement les fichiers de la précédente installation, mais que vous avez conservé les paramètres machine.config.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-134">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="ba4c2-135">Le message d'erreur est semblable au message suivant.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-135">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="ba4c2-136">Ce message d’erreur indique que l’assembly de la version 2.0.0.0 de System.ServiceModel a été installé par une mise en production antérieure de CTP (Customer Technology Preview).</span><span class="sxs-lookup"><span data-stu-id="ba4c2-136">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="ba4c2-137">La version actuelle de l’assembly System.ServiceModel est la version 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-137">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="ba4c2-138">Par conséquent, ce problème se produit lorsque vous souhaitez installer la version officielle de WCF sur un ordinateur sur lequel une version CTP préliminaire de WCF a été installée, mais qui n’a pas été complètement désinstallée.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-138">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="ba4c2-139">ServiceModelReg.exe ne peut pas nettoyer les entrées de versions antérieures ; il ne peut pas non plus enregistrer les entrées de la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-139">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="ba4c2-140">La seule solution consiste à modifier manuellement machine.config. Vous pouvez localiser ce fichier à l’emplacement suivant.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-140">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="ba4c2-141">Si vous exécutez WCF sur un ordinateur 64 bits, vous devez également modifier le même fichier à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-141">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="ba4c2-142">Recherchez dans ce fichier tous les nœuds XML qui font référence à « System. ServiceModel, version = 2.0.0.0 », supprimez-les et tous les nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-142">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="ba4c2-143">Enregistrez le fichier et réexécutez ServiceModelReg.exe afin de résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-143">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ba4c2-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="ba4c2-144">Examples</span></span>  
 <span data-ttu-id="ba4c2-145">Les exemples suivants indiquent comment utiliser les options les plus courantes de l'outil ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="ba4c2-145">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
