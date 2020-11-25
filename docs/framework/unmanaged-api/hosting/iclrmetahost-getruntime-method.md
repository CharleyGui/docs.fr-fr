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
ms.openlocfilehash: 093fa64a7d51e0c2fdc304d2bb4f1c9f7b03e2ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730407"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="d59c1-102">ICLRMetaHost::GetRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="d59c1-102">ICLRMetaHost::GetRuntime Method</span></span>

<span data-ttu-id="d59c1-103">Obtient l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) qui correspond à une version particulière du Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d59c1-103">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="d59c1-104">Cette méthode remplace la fonction [CorBindToRuntimeEx](corbindtoruntimeex-function.md) utilisée avec l’indicateur [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="d59c1-104">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59c1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d59c1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d59c1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d59c1-106">Parameters</span></span>  

 `pwzVersion`  
 <span data-ttu-id="d59c1-107">dans Version de compilation .NET Framework stockée dans les métadonnées, au format «v *A*. *B*[.*X*]».</span><span class="sxs-lookup"><span data-stu-id="d59c1-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v *A*.*B*[.*X*]".</span></span> <span data-ttu-id="d59c1-108">*A*, *B* et *X* sont des nombres décimaux qui correspondent à la version principale, à la version mineure et au numéro de Build.</span><span class="sxs-lookup"><span data-stu-id="d59c1-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d59c1-109">Ce paramètre doit correspondre au nom de répertoire de la version .NET Framework, tel qu’il apparaît sous C:\Windows\Microsoft.NET\Framework ou C:\Windows\Microsoft.NET\Framework64.</span><span class="sxs-lookup"><span data-stu-id="d59c1-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="d59c1-110">Les exemples de valeurs sont « v 1.0.3705 », « v 1.1.4322 », « v 2.0.50727 » et « v 4.0 ». *X*», où *x* dépend du numéro de Build installé.</span><span class="sxs-lookup"><span data-stu-id="d59c1-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="d59c1-111">Le préfixe « v » est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d59c1-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="d59c1-112">dans Identificateur de l’interface souhaitée.</span><span class="sxs-lookup"><span data-stu-id="d59c1-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="d59c1-113">Actuellement, la seule valeur valide pour ce paramètre est IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="d59c1-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="d59c1-114">à Pointeur vers l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) qui correspond au runtime demandé.</span><span class="sxs-lookup"><span data-stu-id="d59c1-114">[out] A pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d59c1-115">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d59c1-115">Return Value</span></span>  

 <span data-ttu-id="d59c1-116">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d59c1-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d59c1-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d59c1-117">HRESULT</span></span>|<span data-ttu-id="d59c1-118">Description</span><span class="sxs-lookup"><span data-stu-id="d59c1-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d59c1-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="d59c1-119">S_OK</span></span>|<span data-ttu-id="d59c1-120">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="d59c1-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="d59c1-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d59c1-121">E_POINTER</span></span>|<span data-ttu-id="d59c1-122">`pwzVersion` ou `ppRuntime` est null.</span><span class="sxs-lookup"><span data-stu-id="d59c1-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d59c1-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="d59c1-123">Remarks</span></span>  

 <span data-ttu-id="d59c1-124">Cette méthode interagit de manière cohérente avec les interfaces héritées telles que l’interface [ICorRuntimeHost](icorruntimehost-interface.md) et les fonctions héritées telles que les fonctions déconseillées `CorBindTo*` (consultez [fonctions d’hébergement CLR dépréciées](deprecated-clr-hosting-functions.md) dans l’API d’hébergement .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="d59c1-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="d59c1-125">Autrement dit, les runtimes chargés avec l’API héritée sont visibles par la nouvelle API, et les runtimes chargés avec la nouvelle API sont visibles par l’API héritée.</span><span class="sxs-lookup"><span data-stu-id="d59c1-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d59c1-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d59c1-126">Requirements</span></span>  

 <span data-ttu-id="d59c1-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d59c1-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d59c1-128">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="d59c1-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d59c1-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d59c1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d59c1-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d59c1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59c1-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d59c1-131">See also</span></span>

- [<span data-ttu-id="d59c1-132">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="d59c1-132">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="d59c1-133">Interfaces d'hébergement du CLR et coclasses déconseillées</span><span class="sxs-lookup"><span data-stu-id="d59c1-133">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="d59c1-134">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="d59c1-134">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="d59c1-135">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="d59c1-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="d59c1-136">Hébergement</span><span class="sxs-lookup"><span data-stu-id="d59c1-136">Hosting</span></span>](index.md)
