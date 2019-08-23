---
title: Outil WorkFlow Service Registration (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 0a9cd5039c085f82f5507c93ebe0855cc620825d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916826"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="9d6f6-102">Outil WorkFlow Service Registration (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="9d6f6-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="9d6f6-103">Workflow Services Registration (WFServicesReg.exe) est un outil autonome qui peut être utilisé pour ajouter, supprimer ou réparer les éléments de configuration correspondant aux services Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="9d6f6-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d6f6-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="9d6f6-105">Notes</span><span class="sxs-lookup"><span data-stu-id="9d6f6-105">Remarks</span></span>  
 <span data-ttu-id="9d6f6-106">Cet outil se trouve à l'emplacement d'installation de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], c'est-à-dire %windir%\Microsoft.NET\Framework\v3.5 ou %windir%\Microsoft.NET\Framework64\v3.5 pour les ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="9d6f6-107">Les tableaux suivants décrivent les options pouvant être utilisées avec l'outil Workflow Services Registration (WFServicesReg.exe).</span><span class="sxs-lookup"><span data-stu-id="9d6f6-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="9d6f6-108">Option</span><span class="sxs-lookup"><span data-stu-id="9d6f6-108">Option</span></span>|<span data-ttu-id="9d6f6-109">Description</span><span class="sxs-lookup"><span data-stu-id="9d6f6-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="9d6f6-110">Configure les services de workflow Windows.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="9d6f6-111">Utilisé dans les scénarios d'installation et de réparation.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="9d6f6-112">Supprime la configuration des services de workflow Windows.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="9d6f6-113">Imprimez des informations détaillées (pour la configuration ou la suppression).</span><span class="sxs-lookup"><span data-stu-id="9d6f6-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="9d6f6-114">Active le format d'enregistrement MSI.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="9d6f6-115">Réduit la fenêtre lorsque l'application est exécutée.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="9d6f6-116">Inscription</span><span class="sxs-lookup"><span data-stu-id="9d6f6-116">Registration</span></span>  
 <span data-ttu-id="9d6f6-117">L'outil vérifie le fichier Web.config et enregistre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9d6f6-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- <span data-ttu-id="9d6f6-118">Assemblys de référence de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d6f6-118">[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] reference assemblies.</span></span>  
  
- <span data-ttu-id="9d6f6-119">Fournisseur de version pour fichiers .xoml.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="9d6f6-120">Gestionnaires HTTP pour fichiers .xoml et .rules.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="9d6f6-121">L'outil vérifie le fichier Machine.config et enregistre les extensions suivantes :</span><span class="sxs-lookup"><span data-stu-id="9d6f6-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="9d6f6-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="9d6f6-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="9d6f6-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="9d6f6-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="9d6f6-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="9d6f6-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="9d6f6-125">L'outil enregistre également les importateurs de métadonnées clients suivants :</span><span class="sxs-lookup"><span data-stu-id="9d6f6-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="9d6f6-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="9d6f6-126">policyImporters</span></span>  
  
- <span data-ttu-id="9d6f6-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="9d6f6-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="9d6f6-128">L'outil enregistre également des mappages de scripts .xoml et .rules ainsi que des gestionnaires dans la métabase IIS.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="9d6f6-129">Sur [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] les [!INCLUDE[wxp](../../../includes/wxp-md.md)] ordinateurs et (IIS 5,1 et IIS 6,0), un ensemble de scriptmaps. xoml et. Rules sont inscrits.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="9d6f6-130">Sur les ordinateurs 64 bits, l'outil enregistre les mappages de scripts en mode WOW si le commutateur `Enable32BitAppOnWin64` est activé, ou les mappages de scripts 64 bits natifs si le commutateur `Enable32BitAppOnWin64` est désactivé.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="9d6f6-131">Sur [!INCLUDE[wv](../../../includes/wv-md.md)] et Windows Server 2008 (IIS 7,0 et versions ultérieures), deux ensembles de gestionnaires. xoml et. Rules sont inscrits: un pour le mode intégré et un pour le mode classique.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="9d6f6-132">Sur les ordinateurs 64 bits, trois jeux de gestionnaires sont enregistrés (indépendamment de l'état du commutateur `Enable32BitAppOnWin64`) : un pour le mode intégré, un pour le mode classique WOW et le dernier pour le mode classique 64 bits natif.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9d6f6-133">Contrairement à ServiceModelReg.exe, WFServicesReg.exe n'autorise pas l'ajout, la suppression ou la réparation des mappages de scripts ou des gestionnaires correspondant à un site Web particulier.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="9d6f6-134">Pour contourner ce problème, consultez la section « Réparation des mappages de scripts ».</span><span class="sxs-lookup"><span data-stu-id="9d6f6-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="9d6f6-135">Scénarios d'utilisation</span><span class="sxs-lookup"><span data-stu-id="9d6f6-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="9d6f6-136">Installation des services IIS après l'installation de .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="9d6f6-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="9d6f6-137">Sous [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] est installé avant les services IIS.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="9d6f6-138">En raison de l'indisponibilité de la métabase IIS, l'installation de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] aboutit sans installer les mappages de scripts .xoml et .rules.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="9d6f6-139">Après avoir installé les services IIS, vous pouvez utiliser l'outil WFServicesReg.exe avec le commutateur `/c` pour installer ces mappages de scripts spécifiques.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="9d6f6-140">Réparation des mappages de scripts</span><span class="sxs-lookup"><span data-stu-id="9d6f6-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="9d6f6-141">Mappage de scripts supprimé sous le nœud Sites Web</span><span class="sxs-lookup"><span data-stu-id="9d6f6-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="9d6f6-142">Sous [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], le mappage de scripts .xoml ou .rules est supprimé par erreur du nœud Sites Web.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="9d6f6-143">Ce problème peut être résolu en exécutant l'outil WFServicesReg.exe avec le commutateur `/c`.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="9d6f6-144">Mappage de scripts supprimé sous un site web particulier</span><span class="sxs-lookup"><span data-stu-id="9d6f6-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="9d6f6-145">Sous [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], un mappage de scripts .xoml ou .rules est supprimé par erreur d’un site web particulier (celui par défaut, par exemple) et non du nœud Sites Web.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="9d6f6-146">Pour réparer des gestionnaires supprimés pour un site Web particulier, exécutez «WFServicesReg. exe/r» pour supprimer les gestionnaires de tous les sites Web, puis exécutez «WFServicesReg. exe/c» pour créer les gestionnaires appropriés pour tous les sites Web.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="9d6f6-147">Configuration de gestionnaires après activation du mode IIS</span><span class="sxs-lookup"><span data-stu-id="9d6f6-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="9d6f6-148">Si les services IIS sont en mode de configuration partagé et si [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] est installé, la métabase IIS est configurée sous un emplacement partagé.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="9d6f6-149">Si vous basculez IIS en mode de configuration non partagé, la métabase locale ne contiendra pas les gestionnaires requis.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="9d6f6-150">Pour configurer correctement la métabase locale, vous pouvez soit importer la métabase partagée vers la métabase locale, soit exécuter «WFServicesReg. exe/c», ce qui configure la métabase locale.</span><span class="sxs-lookup"><span data-stu-id="9d6f6-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
