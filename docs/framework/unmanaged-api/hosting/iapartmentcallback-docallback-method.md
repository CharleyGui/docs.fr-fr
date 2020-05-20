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
ms.openlocfilehash: 1a56c3ebe4b1c528f9c6555bdfbf1270a438410d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617111"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="e1f0d-102">IApartmentCallback::DoCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="e1f0d-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="e1f0d-103">Exécute la fonction spécifiée dans un cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="e1f0d-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1f0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1f0d-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1f0d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e1f0d-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="e1f0d-106">dans Pointeur vers la fonction à exécuter au sein du cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="e1f0d-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="e1f0d-107">dans Pointeur vers l’argument de la fonction.</span><span class="sxs-lookup"><span data-stu-id="e1f0d-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1f0d-108">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="e1f0d-108">Requirements</span></span>  
 <span data-ttu-id="e1f0d-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1f0d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1f0d-110">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e1f0d-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1f0d-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e1f0d-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1f0d-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1f0d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f0d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1f0d-113">See also</span></span>

- [<span data-ttu-id="e1f0d-114">IApartmentCallback, interface</span><span class="sxs-lookup"><span data-stu-id="e1f0d-114">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)
