---
title: Outil WorkFlow Service Registration (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 182bef75bff1785905d77d3bc497e0701e297912
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346591"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="c68e5-102">Outil WorkFlow Service Registration (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="c68e5-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="c68e5-103">Workflow Services Registration (WFServicesReg.exe) est un outil autonome qui peut être utilisé pour ajouter, supprimer ou réparer les éléments de configuration correspondant aux services Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="c68e5-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c68e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c68e5-104">Syntax</span></span>  
  
```console  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="c68e5-105">Notes</span><span class="sxs-lookup"><span data-stu-id="c68e5-105">Remarks</span></span>  
 <span data-ttu-id="c68e5-106">L’outil se trouve à l’emplacement d’installation .NET Framework 3,5, en particulier%windir%\Microsoft.NET\Framework\v3.5 ou sur%windir%\Microsoft.NET\Framework64\v3.5 sur les ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c68e5-106">The tool can be found at the .NET Framework 3.5 installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="c68e5-107">Les tableaux suivants décrivent les options pouvant être utilisées avec l'outil Workflow Services Registration (WFServicesReg.exe).</span><span class="sxs-lookup"><span data-stu-id="c68e5-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="c68e5-108">Option</span><span class="sxs-lookup"><span data-stu-id="c68e5-108">Option</span></span>|<span data-ttu-id="c68e5-109">Description</span><span class="sxs-lookup"><span data-stu-id="c68e5-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="c68e5-110">Configure les services de workflow Windows.</span><span class="sxs-lookup"><span data-stu-id="c68e5-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="c68e5-111">Utilisé dans les scénarios d'installation et de réparation.</span><span class="sxs-lookup"><span data-stu-id="c68e5-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="c68e5-112">Supprime la configuration des services de workflow Windows.</span><span class="sxs-lookup"><span data-stu-id="c68e5-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="c68e5-113">Imprimez des informations détaillées (pour la configuration ou la suppression).</span><span class="sxs-lookup"><span data-stu-id="c68e5-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="c68e5-114">Active le format d'enregistrement MSI.</span><span class="sxs-lookup"><span data-stu-id="c68e5-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="c68e5-115">Réduit la fenêtre lorsque l'application est exécutée.</span><span class="sxs-lookup"><span data-stu-id="c68e5-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="c68e5-116">Inscription</span><span class="sxs-lookup"><span data-stu-id="c68e5-116">Registration</span></span>  
 <span data-ttu-id="c68e5-117">L'outil vérifie le fichier Web.config et enregistre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c68e5-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- <span data-ttu-id="c68e5-118">.NET Framework des assemblys de référence 3,5.</span><span class="sxs-lookup"><span data-stu-id="c68e5-118">.NET Framework 3.5 reference assemblies.</span></span>  
  
- <span data-ttu-id="c68e5-119">Fournisseur de version pour fichiers .xoml.</span><span class="sxs-lookup"><span data-stu-id="c68e5-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="c68e5-120">Gestionnaires HTTP pour fichiers .xoml et .rules.</span><span class="sxs-lookup"><span data-stu-id="c68e5-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="c68e5-121">L'outil vérifie le fichier Machine.config et enregistre les extensions suivantes :</span><span class="sxs-lookup"><span data-stu-id="c68e5-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="c68e5-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="c68e5-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="c68e5-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="c68e5-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="c68e5-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="c68e5-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="c68e5-125">L'outil enregistre également les importateurs de métadonnées clients suivants :</span><span class="sxs-lookup"><span data-stu-id="c68e5-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="c68e5-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="c68e5-126">policyImporters</span></span>  
  
- <span data-ttu-id="c68e5-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="c68e5-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="c68e5-128">L'outil enregistre également des mappages de scripts .xoml et .rules ainsi que des gestionnaires dans la métabase IIS.</span><span class="sxs-lookup"><span data-stu-id="c68e5-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="c68e5-129">Sur les ordinateurs Windows Server 2003 et [!INCLUDE[wxp](../../../includes/wxp-md.md)] (IIS 5,1 et IIS 6,0), un ensemble de scriptmaps. xoml et. Rules est inscrit.</span><span class="sxs-lookup"><span data-stu-id="c68e5-129">On Windows Server 2003 and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="c68e5-130">Sur les ordinateurs 64 bits, l'outil enregistre les mappages de scripts en mode WOW si le commutateur `Enable32BitAppOnWin64` est activé, ou les mappages de scripts 64 bits natifs si le commutateur `Enable32BitAppOnWin64` est désactivé.</span><span class="sxs-lookup"><span data-stu-id="c68e5-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="c68e5-131">Sur les ordinateurs Windows Vista et Windows Server 2008 (IIS 7,0 et versions ultérieures), deux ensembles de gestionnaires. xoml et. Rules sont inscrits : un pour le mode intégré et un pour le mode classique.</span><span class="sxs-lookup"><span data-stu-id="c68e5-131">On Windows Vista and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="c68e5-132">Sur les ordinateurs 64 bits, trois jeux de gestionnaires sont enregistrés (indépendamment de l'état du commutateur `Enable32BitAppOnWin64`) : un pour le mode intégré, un pour le mode classique WOW et le dernier pour le mode classique 64 bits natif.</span><span class="sxs-lookup"><span data-stu-id="c68e5-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c68e5-133">Contrairement à ServiceModelReg.exe, WFServicesReg.exe n'autorise pas l'ajout, la suppression ou la réparation des mappages de scripts ou des gestionnaires correspondant à un site Web particulier.</span><span class="sxs-lookup"><span data-stu-id="c68e5-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="c68e5-134">Pour contourner ce problème, consultez la section « Réparation des mappages de scripts ».</span><span class="sxs-lookup"><span data-stu-id="c68e5-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="c68e5-135">Scénarios d’utilisation</span><span class="sxs-lookup"><span data-stu-id="c68e5-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="c68e5-136">Installation des services IIS après l'installation de .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="c68e5-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="c68e5-137">Sur un ordinateur Windows Server 2003, .NET Framework 3,5 est installé avant l’installation d’IIS.</span><span class="sxs-lookup"><span data-stu-id="c68e5-137">On a Windows Server 2003 machine, .NET Framework 3.5 is installed prior to IIS installation.</span></span> <span data-ttu-id="c68e5-138">En raison de l’indisponibilité de la métabase IIS, l’installation de .NET Framework 3,5 s’effectue correctement sans installer les scriptmaps. xoml et. Rules.</span><span class="sxs-lookup"><span data-stu-id="c68e5-138">Due to the unavailability of the IIS metabase, installation of .NET Framework 3.5 succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="c68e5-139">Après avoir installé les services IIS, vous pouvez utiliser l'outil WFServicesReg.exe avec le commutateur `/c` pour installer ces mappages de scripts spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c68e5-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="c68e5-140">Réparation des mappages de scripts</span><span class="sxs-lookup"><span data-stu-id="c68e5-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="c68e5-141">Mappage de scripts supprimé sous le nœud Sites Web</span><span class="sxs-lookup"><span data-stu-id="c68e5-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="c68e5-142">Sur un ordinateur Windows Server 2003, les règles. xoml ou. Rules sont accidentellement supprimées du nœud sites Web.</span><span class="sxs-lookup"><span data-stu-id="c68e5-142">On a Windows Server 2003 machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="c68e5-143">Ce problème peut être résolu en exécutant l'outil WFServicesReg.exe avec le commutateur `/c`.</span><span class="sxs-lookup"><span data-stu-id="c68e5-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="c68e5-144">Mappage de scripts supprimé sous un site web particulier</span><span class="sxs-lookup"><span data-stu-id="c68e5-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="c68e5-145">Sur un ordinateur Windows Server 2003, les règles. xoml ou. Rules sont accidentellement supprimées d’un site Web particulier (par exemple, le site Web par défaut) plutôt que du nœud sites Web.</span><span class="sxs-lookup"><span data-stu-id="c68e5-145">On a Windows Server 2003 machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="c68e5-146">Pour réparer des gestionnaires supprimés pour un site Web particulier, exécutez « WFServicesReg. exe/r » pour supprimer les gestionnaires de tous les sites Web, puis exécutez « WFServicesReg. exe/c » pour créer les gestionnaires appropriés pour tous les sites Web.</span><span class="sxs-lookup"><span data-stu-id="c68e5-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="c68e5-147">Configuration de gestionnaires après activation du mode IIS</span><span class="sxs-lookup"><span data-stu-id="c68e5-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="c68e5-148">Quand IIS est en mode de configuration partagée et .NET Framework 3,5 est installé, la métabase IIS est configurée sous un emplacement partagé.</span><span class="sxs-lookup"><span data-stu-id="c68e5-148">When IIS is in shared configuration mode and .NET Framework 3.5 is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="c68e5-149">Si vous basculez IIS en mode de configuration non partagé, la métabase locale ne contiendra pas les gestionnaires requis.</span><span class="sxs-lookup"><span data-stu-id="c68e5-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="c68e5-150">Pour configurer correctement la métabase locale, vous pouvez soit importer la métabase partagée vers la métabase locale, soit exécuter « WFServicesReg. exe/c », ce qui configure la métabase locale.</span><span class="sxs-lookup"><span data-stu-id="c68e5-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
