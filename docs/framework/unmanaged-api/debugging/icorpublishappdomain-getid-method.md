---
title: ICorPublishAppDomain::GetID, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
ms.openlocfilehash: ab331145a8147e8830cb9b158a1975bc748c7cce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716861"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="1d681-102">ICorPublishAppDomain::GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="1d681-102">ICorPublishAppDomain::GetID Method</span></span>

<span data-ttu-id="1d681-103">Obtient l’identificateur unique de ce [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="1d681-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d681-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d681-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d681-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1d681-105">Parameters</span></span>  

 `puId`  
 <span data-ttu-id="1d681-106">à Pointeur vers l’identificateur du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="1d681-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d681-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="1d681-107">Remarks</span></span>  

 <span data-ttu-id="1d681-108">L’identificateur est unique dans la portée du processus conteneur.</span><span class="sxs-lookup"><span data-stu-id="1d681-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d681-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1d681-109">Requirements</span></span>  

 <span data-ttu-id="1d681-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d681-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d681-111">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="1d681-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="1d681-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d681-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d681-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d681-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d681-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d681-114">See also</span></span>

- [<span data-ttu-id="1d681-115">ICorPublishAppDomain, interface</span><span class="sxs-lookup"><span data-stu-id="1d681-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
