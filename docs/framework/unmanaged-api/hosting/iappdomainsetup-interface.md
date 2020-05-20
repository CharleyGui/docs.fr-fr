---
title: IAppDomainSetup, interface
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 1726f8929404e0dde979972d7830a6951dd71891
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617059"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="ead6e-102">IAppDomainSetup, interface</span><span class="sxs-lookup"><span data-stu-id="ead6e-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="ead6e-103">Fournit des propriétés qui permettent à l’hôte de configurer un <xref:System.AppDomain?displayProperty=nameWithType> type avant d’appeler la méthode [ICorRuntimeHost :: CreateDomainEx](icorruntimehost-createdomainex-method.md) pour le créer.</span><span class="sxs-lookup"><span data-stu-id="ead6e-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ead6e-104">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ead6e-104">Properties</span></span>  
  
|<span data-ttu-id="ead6e-105">Propriété</span><span class="sxs-lookup"><span data-stu-id="ead6e-105">Property</span></span>|<span data-ttu-id="ead6e-106">Description</span><span class="sxs-lookup"><span data-stu-id="ead6e-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="ead6e-107">Obtient ou définit le nom du répertoire qui contient l’application.</span><span class="sxs-lookup"><span data-stu-id="ead6e-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="ead6e-108">Obtient ou définit le nom de l'application.</span><span class="sxs-lookup"><span data-stu-id="ead6e-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="ead6e-109">Obtient ou définit le nom d’une zone spécifique à l’application dans laquelle les fichiers sont des clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="ead6e-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="ead6e-110">Obtient ou définit le nom du fichier de configuration pour une application.</span><span class="sxs-lookup"><span data-stu-id="ead6e-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="ead6e-111">Obtient ou définit le nom du répertoire dans lequel les fichiers générés dynamiquement sont stockés et accessibles.</span><span class="sxs-lookup"><span data-stu-id="ead6e-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="ead6e-112">Obtient ou définit le chemin d’accès au fichier de licence associé à ce domaine.</span><span class="sxs-lookup"><span data-stu-id="ead6e-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="ead6e-113">Obtient ou définit la liste des répertoires combinés avec le <xref:System.AppDomainSetup.ApplicationBase%2A> répertoire pour détecter les assemblys privés.</span><span class="sxs-lookup"><span data-stu-id="ead6e-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="ead6e-114">Obtient ou définit une valeur de chaîne qui inclut ou exclut du <xref:System.AppDomainSetup.ApplicationBase%2A> chemin de recherche de l’application.</span><span class="sxs-lookup"><span data-stu-id="ead6e-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="ead6e-115">Obtient ou définit les noms des répertoires qui contiennent des assemblys pour lesquels des clichés instantanés doivent être définis.</span><span class="sxs-lookup"><span data-stu-id="ead6e-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="ead6e-116">Obtient ou définit une chaîne qui indique si la copie fictive est activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="ead6e-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="ead6e-117">Les valeurs valides sont « true » ou « false ».</span><span class="sxs-lookup"><span data-stu-id="ead6e-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ead6e-118">Notes</span><span class="sxs-lookup"><span data-stu-id="ead6e-118">Remarks</span></span>  
 <span data-ttu-id="ead6e-119">L' `IAppDomainSetup` interface correspond à l’interface managée <xref:System.IAppDomainSetup> , que le <xref:System.AppDomainSetup> type implémente.</span><span class="sxs-lookup"><span data-stu-id="ead6e-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="ead6e-120">Pour obtenir une <xref:System.IAppDomainSetup?displayProperty=nameWithType> Description détaillée de ses propriétés, consultez.</span><span class="sxs-lookup"><span data-stu-id="ead6e-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="ead6e-121">`IAppDomainSetup`représente les informations de liaison d’assembly qui peuvent être ajoutées à une <xref:System.AppDomain> instance avant sa création.</span><span class="sxs-lookup"><span data-stu-id="ead6e-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="ead6e-122">Par exemple, un hôte peut définir la <xref:System.AppDomainSetup.ApplicationBase%2A> propriété pour établir un répertoire racine, que le Common Language Runtime (CLR) sonde pour les assemblys managés.</span><span class="sxs-lookup"><span data-stu-id="ead6e-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ead6e-123">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="ead6e-123">Requirements</span></span>  
 <span data-ttu-id="ead6e-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ead6e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ead6e-125">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ead6e-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ead6e-126">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ead6e-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ead6e-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ead6e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ead6e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ead6e-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="ead6e-129">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="ead6e-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
