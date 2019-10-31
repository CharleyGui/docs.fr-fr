---
title: ICLRRuntimeInfo::GetProcAddress, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: cedda39aeebc62c6bf43f42ae2daf6f6f515fd27
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120274"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="4222f-102">ICLRRuntimeInfo::GetProcAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="4222f-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="4222f-103">Obtient l’adresse d’une fonction spécifiée qui a été exportée à partir du common language runtime (CLR) associé à cette interface.</span><span class="sxs-lookup"><span data-stu-id="4222f-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="4222f-104">Cette méthode remplace la fonction [GetRealProcAddress,](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) .</span><span class="sxs-lookup"><span data-stu-id="4222f-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4222f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4222f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4222f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4222f-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="4222f-107">dans Nom de la fonction exportée.</span><span class="sxs-lookup"><span data-stu-id="4222f-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="4222f-108">à Adresse de la fonction exportée.</span><span class="sxs-lookup"><span data-stu-id="4222f-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4222f-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4222f-109">Return Value</span></span>  
 <span data-ttu-id="4222f-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4222f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4222f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4222f-111">HRESULT</span></span>|<span data-ttu-id="4222f-112">Description</span><span class="sxs-lookup"><span data-stu-id="4222f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4222f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="4222f-113">S_OK</span></span>|<span data-ttu-id="4222f-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="4222f-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="4222f-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4222f-115">E_POINTER</span></span>|<span data-ttu-id="4222f-116">`pszProcName` ou `ppProc` est null.</span><span class="sxs-lookup"><span data-stu-id="4222f-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="4222f-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="4222f-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="4222f-118">La fonction spécifiée n’est pas une fonction exportée.</span><span class="sxs-lookup"><span data-stu-id="4222f-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4222f-119">Notes</span><span class="sxs-lookup"><span data-stu-id="4222f-119">Remarks</span></span>  
 <span data-ttu-id="4222f-120">Cette méthode provoque le chargement du CLR mais pas son initialisation.</span><span class="sxs-lookup"><span data-stu-id="4222f-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4222f-121">spécifications</span><span class="sxs-lookup"><span data-stu-id="4222f-121">Requirements</span></span>  
 <span data-ttu-id="4222f-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4222f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4222f-123">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="4222f-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4222f-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4222f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4222f-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4222f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4222f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4222f-126">See also</span></span>

- [<span data-ttu-id="4222f-127">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="4222f-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="4222f-128">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="4222f-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4222f-129">Hébergement</span><span class="sxs-lookup"><span data-stu-id="4222f-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
