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
ms.openlocfilehash: 6f7f400c51ded0b98c0c2286cb6f90bbd77e47d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178398"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="b866f-102">ICorPublishAppDomainEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="b866f-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="b866f-103">Obtient le nombre spécifié de domaines d’application qui existent actuellement dans le processus, à partir de la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="b866f-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b866f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b866f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b866f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b866f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b866f-106">[dans] Nombre d’éléments à récupérer.</span><span class="sxs-lookup"><span data-stu-id="b866f-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="b866f-107">[out] Un pointeur à la gamme d’objets [ICorPublishAppDomain](icorpublishappdomain-interface.md) récupérés, dont chacun représente un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="b866f-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b866f-108">[out] Pointeur sur le nombre de domaines d’application effectivement retourné.</span><span class="sxs-lookup"><span data-stu-id="b866f-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="b866f-109">Cette valeur peut `celt` être nulle si elle en est une.</span><span class="sxs-lookup"><span data-stu-id="b866f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b866f-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b866f-110">Requirements</span></span>  
 <span data-ttu-id="b866f-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b866f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b866f-112">**En-tête:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b866f-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b866f-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b866f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b866f-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b866f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b866f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b866f-115">See also</span></span>

- [<span data-ttu-id="b866f-116">ICorPublishAppDomainEnum, interface</span><span class="sxs-lookup"><span data-stu-id="b866f-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
