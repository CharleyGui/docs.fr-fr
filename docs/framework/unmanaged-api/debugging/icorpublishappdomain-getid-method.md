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
ms.openlocfilehash: 33a72d9aea09f808d42d1a17a7ec5640d20d7c79
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140374"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="a5312-102">ICorPublishAppDomain::GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="a5312-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="a5312-103">Obtient l’identificateur unique de ce [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a5312-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5312-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5312-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5312-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a5312-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="a5312-106">à Pointeur vers l’identificateur du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a5312-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5312-107">Notes</span><span class="sxs-lookup"><span data-stu-id="a5312-107">Remarks</span></span>  
 <span data-ttu-id="a5312-108">L’identificateur est unique dans la portée du processus conteneur.</span><span class="sxs-lookup"><span data-stu-id="a5312-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5312-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="a5312-109">Requirements</span></span>  
 <span data-ttu-id="a5312-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5312-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5312-111">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a5312-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a5312-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5312-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5312-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5312-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5312-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5312-114">See also</span></span>

- [<span data-ttu-id="a5312-115">ICorPublishAppDomain, interface</span><span class="sxs-lookup"><span data-stu-id="a5312-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
