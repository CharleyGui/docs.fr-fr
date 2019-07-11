---
title: ICLRRuntimeInfo::LoadLibrary, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65ac05a524297029ca50970bdd231c6a9112e35c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748386"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="31c00-102">ICLRRuntimeInfo::LoadLibrary, méthode</span><span class="sxs-lookup"><span data-stu-id="31c00-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="31c00-103">Charge une bibliothèque .NET Framework à partir de représenté par le common language runtime (CLR) un [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="31c00-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="31c00-104">Cette méthode remplace la [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="31c00-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31c00-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31c00-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31c00-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31c00-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="31c00-107">[in] Le nom de l’assembly à charger.</span><span class="sxs-lookup"><span data-stu-id="31c00-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="31c00-108">[out] Handle vers l’assembly chargé.</span><span class="sxs-lookup"><span data-stu-id="31c00-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31c00-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="31c00-109">Return Value</span></span>  
 <span data-ttu-id="31c00-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="31c00-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="31c00-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31c00-111">HRESULT</span></span>|<span data-ttu-id="31c00-112">Description</span><span class="sxs-lookup"><span data-stu-id="31c00-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31c00-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="31c00-113">S_OK</span></span>|<span data-ttu-id="31c00-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="31c00-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="31c00-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="31c00-115">E_POINTER</span></span>|<span data-ttu-id="31c00-116">`pwzDllName` ou `phndModule` est null.</span><span class="sxs-lookup"><span data-stu-id="31c00-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="31c00-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="31c00-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="31c00-118">Pas assez de mémoire est disponible pour traiter la demande.</span><span class="sxs-lookup"><span data-stu-id="31c00-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31c00-119">Notes</span><span class="sxs-lookup"><span data-stu-id="31c00-119">Remarks</span></span>  
 <span data-ttu-id="31c00-120">Cette méthode charge uniquement les DLL incluses dans le package redistribuable .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="31c00-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="31c00-121">Il ne peut pas charger des assemblys générés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="31c00-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31c00-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="31c00-122">Requirements</span></span>  
 <span data-ttu-id="31c00-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31c00-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31c00-124">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="31c00-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="31c00-125">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31c00-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31c00-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31c00-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c00-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31c00-127">See also</span></span>

- [<span data-ttu-id="31c00-128">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="31c00-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="31c00-129">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="31c00-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="31c00-130">Hébergement</span><span class="sxs-lookup"><span data-stu-id="31c00-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
