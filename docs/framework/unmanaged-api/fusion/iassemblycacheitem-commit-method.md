---
title: IAssemblyCacheItem::Commit, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.Commit
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type:
- apiref
ms.openlocfilehash: 2b7c10e82aca2b2ece7ea4d7209c1f3c9a456434
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670405"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="fbbd9-102">IAssemblyCacheItem::Commit, méthode</span><span class="sxs-lookup"><span data-stu-id="fbbd9-102">IAssemblyCacheItem::Commit Method</span></span>

<span data-ttu-id="fbbd9-103">Valide la référence de l’assembly mis en cache dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="fbbd9-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbbd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbbd9-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbbd9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fbbd9-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="fbbd9-106">dans Indicateurs définis dans fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="fbbd9-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="fbbd9-107">[out, optional] Valeur qui indique le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="fbbd9-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbbd9-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fbbd9-108">Requirements</span></span>  

 <span data-ttu-id="fbbd9-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbbd9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbbd9-110">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="fbbd9-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fbbd9-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbbd9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbbd9-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbbd9-112">See also</span></span>

- [<span data-ttu-id="fbbd9-113">IAssemblyCacheItem, interface</span><span class="sxs-lookup"><span data-stu-id="fbbd9-113">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
