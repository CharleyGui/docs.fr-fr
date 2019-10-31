---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
ms.openlocfilehash: 37919be2d0ebd7d243615bc5845b0781ac13e574
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129313"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="a3560-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="a3560-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="a3560-103">Définit les propriétés qui seront utilisées pour initialiser le domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="a3560-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3560-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3560-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3560-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a3560-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="a3560-106">dans Nombre d’entrées dans `pwszPropertyNames` et `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="a3560-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="a3560-107">dans Tableau de noms de propriété, ou null s’il n’y a pas de propriétés.</span><span class="sxs-lookup"><span data-stu-id="a3560-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="a3560-108">Actuellement, le seul nom de propriété reconnu par cette méthode est « PARTIAL_TRUST_VISIBLE_ASSEMBLIES ».</span><span class="sxs-lookup"><span data-stu-id="a3560-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="a3560-109">dans Tableau de valeurs de propriété, ou null s’il n’existe aucune propriété.</span><span class="sxs-lookup"><span data-stu-id="a3560-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3560-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a3560-110">Return Value</span></span>  
 <span data-ttu-id="a3560-111">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a3560-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a3560-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3560-112">HRESULT</span></span>|<span data-ttu-id="a3560-113">Description</span><span class="sxs-lookup"><span data-stu-id="a3560-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3560-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3560-114">S_OK</span></span>|<span data-ttu-id="a3560-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="a3560-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="a3560-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="a3560-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="a3560-117">`pwszPropertyNames` comprend un nom de propriété qui n’est pas reconnu par cette méthode.</span><span class="sxs-lookup"><span data-stu-id="a3560-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3560-118">Notes</span><span class="sxs-lookup"><span data-stu-id="a3560-118">Remarks</span></span>  
 <span data-ttu-id="a3560-119">La valeur de propriété pour « PARTIAL_TRUST_VISIBLE_ASSEMBLIES » est une liste d’assemblys qui ont l’attribut conditionnel <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) avec l’indicateur <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType>, qui doivent être rendus visibles aux appelants d’un niveau de confiance partiel dans le domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="a3560-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3560-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="a3560-120">Requirements</span></span>  
 <span data-ttu-id="a3560-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3560-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3560-122">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="a3560-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a3560-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a3560-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3560-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3560-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3560-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3560-125">See also</span></span>

- [<span data-ttu-id="a3560-126">Hébergement</span><span class="sxs-lookup"><span data-stu-id="a3560-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="a3560-127">ICLRDomainManager, interface</span><span class="sxs-lookup"><span data-stu-id="a3560-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
