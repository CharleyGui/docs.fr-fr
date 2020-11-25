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
ms.openlocfilehash: e3031bf123ff9107b4cebc0723f1be0d423bdaec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721749"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="f0825-102">IApartmentCallback::DoCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="f0825-102">IApartmentCallback::DoCallback Method</span></span>

<span data-ttu-id="f0825-103">Exécute la fonction spécifiée dans un cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="f0825-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0825-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0825-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0825-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0825-105">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="f0825-106">dans Pointeur vers la fonction à exécuter au sein du cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="f0825-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="f0825-107">dans Pointeur vers l’argument de la fonction.</span><span class="sxs-lookup"><span data-stu-id="f0825-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0825-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f0825-108">Requirements</span></span>  

 <span data-ttu-id="f0825-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0825-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0825-110">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0825-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0825-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0825-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0825-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0825-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0825-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0825-113">See also</span></span>

- [<span data-ttu-id="f0825-114">IApartmentCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f0825-114">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)
