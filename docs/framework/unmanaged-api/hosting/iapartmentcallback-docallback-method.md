---
title: IApartmentCallback::DoCallback, méthode
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
ms.openlocfilehash: 9bb257a3d84d5022b9ae13c89a34572485d3033b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126943"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="20a5c-102">IApartmentCallback::DoCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="20a5c-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="20a5c-103">Exécute la fonction spécifiée dans un cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="20a5c-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20a5c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20a5c-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20a5c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20a5c-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="20a5c-106">dans Pointeur vers la fonction à exécuter au sein du cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="20a5c-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="20a5c-107">dans Pointeur vers l’argument de la fonction.</span><span class="sxs-lookup"><span data-stu-id="20a5c-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20a5c-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="20a5c-108">Requirements</span></span>  
 <span data-ttu-id="20a5c-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20a5c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20a5c-110">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="20a5c-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20a5c-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="20a5c-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20a5c-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20a5c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a5c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20a5c-113">See also</span></span>

- [<span data-ttu-id="20a5c-114">IApartmentCallback, interface</span><span class="sxs-lookup"><span data-stu-id="20a5c-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
