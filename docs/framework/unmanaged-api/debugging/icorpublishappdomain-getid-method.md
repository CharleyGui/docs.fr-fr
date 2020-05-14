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
ms.openlocfilehash: 36c5c674f3cdf867107b9ee85a5befadc9246d78
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396304"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="a61c4-102">ICorPublishAppDomain::GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="a61c4-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="a61c4-103">Obtient l’identificateur unique de ce [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a61c4-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a61c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a61c4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a61c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a61c4-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="a61c4-106">à Pointeur vers l’identificateur du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a61c4-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a61c4-107">Notes</span><span class="sxs-lookup"><span data-stu-id="a61c4-107">Remarks</span></span>  
 <span data-ttu-id="a61c4-108">L’identificateur est unique dans la portée du processus conteneur.</span><span class="sxs-lookup"><span data-stu-id="a61c4-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a61c4-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a61c4-109">Requirements</span></span>  
 <span data-ttu-id="a61c4-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a61c4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a61c4-111">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a61c4-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a61c4-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a61c4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a61c4-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a61c4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a61c4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a61c4-114">See also</span></span>

- [<span data-ttu-id="a61c4-115">ICorPublishAppDomain, interface</span><span class="sxs-lookup"><span data-stu-id="a61c4-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
