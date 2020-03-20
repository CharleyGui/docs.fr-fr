---
title: Outil d'inscription ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183108"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="8545a-102">Outil d'inscription ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="8545a-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="8545a-103">Cet outil en ligne de commande permet de gérer l'inscription des composants WCF et WF sur un ordinateur unique.</span><span class="sxs-lookup"><span data-stu-id="8545a-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="8545a-104">Dans des circonstances normales vous n'avez pas à utiliser cet outil, car les composants WCF et WF sont configurés lors de l'installation.</span><span class="sxs-lookup"><span data-stu-id="8545a-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="8545a-105">Mais si vous rencontrez des problèmes avec l'activation de service, vous pouvez essayer d'inscrire les composants à l'aide de cet outil.</span><span class="sxs-lookup"><span data-stu-id="8545a-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8545a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8545a-106">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="8545a-107">Notes </span><span class="sxs-lookup"><span data-stu-id="8545a-107">Remarks</span></span>  
 <span data-ttu-id="8545a-108">Cet outil se trouve à l'emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="8545a-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="8545a-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="8545a-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="8545a-110">Lorsque l’outil d’enregistrement De ServiceModel est exécuté sur Windows Vista, le dialogue **Windows Features** peut ne pas refléter que l’option **d’activation HTTP de la Fondation De communication Windows** dans le cadre de Microsoft **.NET Framework 3.0** est activée.</span><span class="sxs-lookup"><span data-stu-id="8545a-110">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="8545a-111">Le dialogue **Windows Features** peut être consulté en cliquant sur **Démarrer,** puis cliquez **sur Run,** puis en tapant **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="8545a-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="8545a-112">Les tableaux suivants décrivent les options qui peuvent être utilisées avec ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="8545a-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="8545a-113">Option</span><span class="sxs-lookup"><span data-stu-id="8545a-113">Option</span></span>|<span data-ttu-id="8545a-114">Description</span><span class="sxs-lookup"><span data-stu-id="8545a-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="8545a-115">Installe les composants WCF et WF.</span><span class="sxs-lookup"><span data-stu-id="8545a-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="8545a-116">Désinstalle les composants WCF et WF.</span><span class="sxs-lookup"><span data-stu-id="8545a-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="8545a-117">Répare les composants WCF et WF.</span><span class="sxs-lookup"><span data-stu-id="8545a-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="8545a-118">Installe les composants WCF et WF spécifiés avec –c.</span><span class="sxs-lookup"><span data-stu-id="8545a-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="8545a-119">Désinstalle les composants WCF et WF spécifiés avec –c.</span><span class="sxs-lookup"><span data-stu-id="8545a-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="8545a-120">Installe ou désinstalle un composant :</span><span class="sxs-lookup"><span data-stu-id="8545a-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="8545a-121">- httpnamespace - HTTP Namespace Reservation</span><span class="sxs-lookup"><span data-stu-id="8545a-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="8545a-122">- tcpportsharing - Service de partage de ports TCP</span><span class="sxs-lookup"><span data-stu-id="8545a-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="8545a-123">- tcpactivation - Service d’activation TCP (non pris en service sur .NET 4 Profil client)</span><span class="sxs-lookup"><span data-stu-id="8545a-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="8545a-124">- nommépipeactivation - Service d’activation de tuyaux nommés (non pris en service sur .NET 4 Profil client</span><span class="sxs-lookup"><span data-stu-id="8545a-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="8545a-125">- msmqactivation - Service d’activation MSMQ (non pris en service sur .NET 4 Profil client</span><span class="sxs-lookup"><span data-stu-id="8545a-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="8545a-126">- etw - ETW event tracing manifestes (Windows Vista ou plus tard)</span><span class="sxs-lookup"><span data-stu-id="8545a-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="8545a-127">Mode silencieux (enregistrement des erreurs d'affichage uniquement)</span><span class="sxs-lookup"><span data-stu-id="8545a-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="8545a-128">Mode documenté.</span><span class="sxs-lookup"><span data-stu-id="8545a-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="8545a-129">Supprime le message de copyright et de bannière.</span><span class="sxs-lookup"><span data-stu-id="8545a-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="8545a-130">Affiche le texte de l'aide.</span><span class="sxs-lookup"><span data-stu-id="8545a-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="8545a-131">Résolution de l'erreur FileLoadException</span><span class="sxs-lookup"><span data-stu-id="8545a-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="8545a-132">Si vous avez installé des versions précédentes de `FileLoadFoundException` WCF sur votre machine, vous pouvez obtenir une erreur lorsque vous exécutez l’outil ServiceModelReg pour enregistrer une nouvelle installation.</span><span class="sxs-lookup"><span data-stu-id="8545a-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="8545a-133">Cela peut se produire même si vous avez supprimé manuellement les fichiers de la précédente installation, mais que vous avez conservé les paramètres machine.config.</span><span class="sxs-lookup"><span data-stu-id="8545a-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="8545a-134">Le message d'erreur est semblable au message suivant.</span><span class="sxs-lookup"><span data-stu-id="8545a-134">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="8545a-135">Ce message d’erreur indique que l’assembly de la version 2.0.0.0 de System.ServiceModel a été installé par une mise en production antérieure de CTP (Customer Technology Preview).</span><span class="sxs-lookup"><span data-stu-id="8545a-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="8545a-136">La version actuelle de l’assembly System.ServiceModel est la version 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="8545a-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="8545a-137">Par conséquent, ce problème est rencontré lorsque vous voulez installer la version officielle WCF sur une machine où une version CTP précoce de WCF a été installé, mais pas complètement désinstallé.</span><span class="sxs-lookup"><span data-stu-id="8545a-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="8545a-138">ServiceModelReg.exe ne peut pas nettoyer les entrées de versions antérieures ; il ne peut pas non plus enregistrer les entrées de la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="8545a-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="8545a-139">La seule solution de contournement est d’éditer manuellement machine.config. Vous pouvez localiser ce fichier à l’endroit suivant.</span><span class="sxs-lookup"><span data-stu-id="8545a-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="8545a-140">Si vous exécutez WCF sur une machine 64 bits, vous devez également modifier le même fichier à cet endroit.</span><span class="sxs-lookup"><span data-stu-id="8545a-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="8545a-141">Localisez tous les nœuds XML dans ce fichier qui se réfèrent à "System.ServiceModel, Version 2.0.0.0", supprimez-les et nœuds pour enfants.</span><span class="sxs-lookup"><span data-stu-id="8545a-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="8545a-142">Enregistrez le fichier et réexécutez ServiceModelReg.exe afin de résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="8545a-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8545a-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="8545a-143">Examples</span></span>  
 <span data-ttu-id="8545a-144">Les exemples suivants indiquent comment utiliser les options les plus courantes de l'outil ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="8545a-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
