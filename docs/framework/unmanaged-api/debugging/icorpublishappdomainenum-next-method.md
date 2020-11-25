---
title: ICorPublishAppDomainEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
ms.openlocfilehash: 00aff9ab4edbbebe4b924d335fa12f92e9840737
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693695"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="54312-102">ICorPublishAppDomainEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="54312-102">ICorPublishAppDomainEnum::Next Method</span></span>

<span data-ttu-id="54312-103">Obtient le nombre spécifié de domaines d’application qui existent actuellement dans le processus, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="54312-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54312-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54312-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54312-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="54312-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="54312-106">dans Nombre d’éléments à récupérer.</span><span class="sxs-lookup"><span data-stu-id="54312-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="54312-107">à Pointeur vers le tableau d’objets [ICorPublishAppDomain](icorpublishappdomain-interface.md) récupérés, chacun représentant un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="54312-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="54312-108">à Pointeur vers le nombre de domaines d’application réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="54312-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="54312-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="54312-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54312-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="54312-110">Requirements</span></span>  

 <span data-ttu-id="54312-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54312-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54312-112">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="54312-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="54312-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54312-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54312-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54312-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54312-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54312-115">See also</span></span>

- [<span data-ttu-id="54312-116">ICorPublishAppDomainEnum, interface</span><span class="sxs-lookup"><span data-stu-id="54312-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
