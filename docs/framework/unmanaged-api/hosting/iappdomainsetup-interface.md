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
ms.openlocfilehash: 0fab64c31d4a73995c16d21767f4569f21c7df9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126869"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="87785-102">IAppDomainSetup, interface</span><span class="sxs-lookup"><span data-stu-id="87785-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="87785-103">Fournit des propriétés qui permettent à l’hôte de configurer un type de <xref:System.AppDomain?displayProperty=nameWithType> avant d’appeler la méthode [ICorRuntimeHost :: CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) pour le créer.</span><span class="sxs-lookup"><span data-stu-id="87785-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="87785-104">Propriétés</span><span class="sxs-lookup"><span data-stu-id="87785-104">Properties</span></span>  
  
|<span data-ttu-id="87785-105">Property</span><span class="sxs-lookup"><span data-stu-id="87785-105">Property</span></span>|<span data-ttu-id="87785-106">Description</span><span class="sxs-lookup"><span data-stu-id="87785-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="87785-107">Obtient ou définit le nom du répertoire qui contient l’application.</span><span class="sxs-lookup"><span data-stu-id="87785-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="87785-108">Obtient ou définit le nom de l'application.</span><span class="sxs-lookup"><span data-stu-id="87785-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="87785-109">Obtient ou définit le nom d’une zone spécifique à l’application dans laquelle les fichiers sont des clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="87785-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="87785-110">Obtient ou définit le nom du fichier de configuration pour une application.</span><span class="sxs-lookup"><span data-stu-id="87785-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="87785-111">Obtient ou définit le nom du répertoire dans lequel les fichiers générés dynamiquement sont stockés et accessibles.</span><span class="sxs-lookup"><span data-stu-id="87785-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="87785-112">Obtient ou définit le chemin d’accès au fichier de licence associé à ce domaine.</span><span class="sxs-lookup"><span data-stu-id="87785-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="87785-113">Obtient ou définit la liste des répertoires combinés avec le répertoire <xref:System.AppDomainSetup.ApplicationBase%2A> pour détecter les assemblys privés.</span><span class="sxs-lookup"><span data-stu-id="87785-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="87785-114">Obtient ou définit une valeur de chaîne qui inclut ou exclut <xref:System.AppDomainSetup.ApplicationBase%2A> du chemin de recherche de l’application.</span><span class="sxs-lookup"><span data-stu-id="87785-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="87785-115">Obtient ou définit les noms des répertoires qui contiennent des assemblys pour lesquels des clichés instantanés doivent être définis.</span><span class="sxs-lookup"><span data-stu-id="87785-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="87785-116">Obtient ou définit une chaîne qui indique si la copie fictive est activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="87785-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="87785-117">Les valeurs valides sont « true » ou « false ».</span><span class="sxs-lookup"><span data-stu-id="87785-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87785-118">Notes</span><span class="sxs-lookup"><span data-stu-id="87785-118">Remarks</span></span>  
 <span data-ttu-id="87785-119">L’interface `IAppDomainSetup` correspond à l’interface <xref:System.IAppDomainSetup> managée, que le type de <xref:System.AppDomainSetup> implémente.</span><span class="sxs-lookup"><span data-stu-id="87785-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="87785-120">Pour obtenir une description détaillée de ses propriétés, consultez <xref:System.IAppDomainSetup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87785-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="87785-121">`IAppDomainSetup` représente des informations de liaison d’assembly qui peuvent être ajoutées à une instance de <xref:System.AppDomain> avant sa création.</span><span class="sxs-lookup"><span data-stu-id="87785-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="87785-122">Par exemple, un hôte peut définir la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> pour établir un répertoire racine, que le common language runtime (CLR) sonde pour les assemblys managés.</span><span class="sxs-lookup"><span data-stu-id="87785-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87785-123">spécifications</span><span class="sxs-lookup"><span data-stu-id="87785-123">Requirements</span></span>  
 <span data-ttu-id="87785-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87785-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87785-125">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="87785-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87785-126">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87785-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87785-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87785-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87785-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87785-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="87785-129">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="87785-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
