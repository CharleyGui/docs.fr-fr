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
ms.openlocfilehash: 028cfd51a713d8598598566a5b1edcf3fc70ecfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732058"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="3714d-102">ICLRRuntimeInfo::GetProcAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="3714d-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>

<span data-ttu-id="3714d-103">Obtient l’adresse d’une fonction spécifiée qui a été exportée à partir du common language runtime (CLR) associé à cette interface.</span><span class="sxs-lookup"><span data-stu-id="3714d-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="3714d-104">Cette méthode remplace la fonction [GetRealProcAddress,](getrealprocaddress-function.md) .</span><span class="sxs-lookup"><span data-stu-id="3714d-104">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3714d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3714d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3714d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3714d-106">Parameters</span></span>  

 `pszProcName`  
 <span data-ttu-id="3714d-107">dans Nom de la fonction exportée.</span><span class="sxs-lookup"><span data-stu-id="3714d-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="3714d-108">à Adresse de la fonction exportée.</span><span class="sxs-lookup"><span data-stu-id="3714d-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3714d-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3714d-109">Return Value</span></span>  

 <span data-ttu-id="3714d-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3714d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3714d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3714d-111">HRESULT</span></span>|<span data-ttu-id="3714d-112">Description</span><span class="sxs-lookup"><span data-stu-id="3714d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3714d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3714d-113">S_OK</span></span>|<span data-ttu-id="3714d-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="3714d-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="3714d-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3714d-115">E_POINTER</span></span>|<span data-ttu-id="3714d-116">`pszProcName` ou `ppProc` est null.</span><span class="sxs-lookup"><span data-stu-id="3714d-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="3714d-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="3714d-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="3714d-118">La fonction spécifiée n’est pas une fonction exportée.</span><span class="sxs-lookup"><span data-stu-id="3714d-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3714d-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="3714d-119">Remarks</span></span>  

 <span data-ttu-id="3714d-120">Cette méthode provoque le chargement du CLR mais pas son initialisation.</span><span class="sxs-lookup"><span data-stu-id="3714d-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3714d-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3714d-121">Requirements</span></span>  

 <span data-ttu-id="3714d-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3714d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3714d-123">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="3714d-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3714d-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3714d-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3714d-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3714d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3714d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3714d-126">See also</span></span>

- [<span data-ttu-id="3714d-127">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="3714d-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="3714d-128">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="3714d-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="3714d-129">Hébergement</span><span class="sxs-lookup"><span data-stu-id="3714d-129">Hosting</span></span>](index.md)
