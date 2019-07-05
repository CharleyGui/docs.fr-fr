---
title: ICLRMetaHost::GetRuntime, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 004122e9bb52dfe2e51ca00cd5362b2b7a06f30e
ms.sourcegitcommit: 4a3c95e91289d16c38979575a245a4f76b0da147
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67569571"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="28449-102">ICLRMetaHost::GetRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="28449-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="28449-103">Obtient le [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface qui correspond à une version particulière du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="28449-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="28449-104">Cette méthode remplace la [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) fonction utilisée avec le [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) indicateur.</span><span class="sxs-lookup"><span data-stu-id="28449-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28449-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28449-105">Syntax</span></span>  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28449-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="28449-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="28449-107">[in] La version de compilation .NET Framework stockée dans les métadonnées, au format « v*A*. *B*[. *X*] ».</span><span class="sxs-lookup"><span data-stu-id="28449-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="28449-108">*Un*, *B*, et *X* sont des nombres décimaux qui correspondent à la version principale, la version secondaire et le numéro de build.</span><span class="sxs-lookup"><span data-stu-id="28449-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28449-109">Ce paramètre doit correspondre au nom de répertoire pour la version de .NET Framework, tel qu’il apparaît sous C:\Windows\Microsoft.NET\Framework ou C:\Windows\Microsoft.NET\Framework64.</span><span class="sxs-lookup"><span data-stu-id="28449-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="28449-110">Exemples de valeurs : « v1.0.3705 », « v1.1.4322 », « v2.0.50727 » et « v4.0. *X*», où *X* varie selon le numéro de build installé.</span><span class="sxs-lookup"><span data-stu-id="28449-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="28449-111">Le préfixe « v » est requis.</span><span class="sxs-lookup"><span data-stu-id="28449-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="28449-112">[in] L’identificateur de l’interface souhaitée.</span><span class="sxs-lookup"><span data-stu-id="28449-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="28449-113">Actuellement, la seule valeur valide pour ce paramètre est IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="28449-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="28449-114">[out] Un pointeur vers le [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface qui correspond au runtime demandé.</span><span class="sxs-lookup"><span data-stu-id="28449-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28449-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="28449-115">Return Value</span></span>  
 <span data-ttu-id="28449-116">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="28449-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="28449-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28449-117">HRESULT</span></span>|<span data-ttu-id="28449-118">Description</span><span class="sxs-lookup"><span data-stu-id="28449-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28449-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="28449-119">S_OK</span></span>|<span data-ttu-id="28449-120">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="28449-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="28449-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="28449-121">E_POINTER</span></span>|<span data-ttu-id="28449-122">`pwzVersion` ou `ppRuntime` est null.</span><span class="sxs-lookup"><span data-stu-id="28449-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28449-123">Notes</span><span class="sxs-lookup"><span data-stu-id="28449-123">Remarks</span></span>  
 <span data-ttu-id="28449-124">Cette méthode interagit régulièrement avec les interfaces héritées telles que la [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface et les fonctions héritées comme déconseillées `CorBindTo*` fonctions (voir [déconseillée hébergeant des fonctions CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) dans l’API d’hébergement .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="28449-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="28449-125">Autrement dit, les runtimes chargés avec l’API héritée sont visibles à la nouvelle API, et les runtimes chargés avec la nouvelle API sont visibles à l’API héritée.</span><span class="sxs-lookup"><span data-stu-id="28449-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28449-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="28449-126">Requirements</span></span>  
 <span data-ttu-id="28449-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28449-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28449-128">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="28449-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="28449-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28449-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28449-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28449-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28449-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28449-131">See also</span></span>

- [<span data-ttu-id="28449-132">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="28449-132">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="28449-133">Coclasses et interfaces d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="28449-133">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="28449-134">Interfaces d’hébergement CLR</span><span class="sxs-lookup"><span data-stu-id="28449-134">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="28449-135">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="28449-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="28449-136">Hébergement</span><span class="sxs-lookup"><span data-stu-id="28449-136">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
