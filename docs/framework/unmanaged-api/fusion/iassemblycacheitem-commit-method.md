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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d1f5988266fcbfc18ee937b6e7fdb1829646fa9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778678"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="08f63-102">IAssemblyCacheItem::Commit, méthode</span><span class="sxs-lookup"><span data-stu-id="08f63-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="08f63-103">Valide la référence d’assembly mis en cache dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="08f63-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08f63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08f63-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08f63-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08f63-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="08f63-106">[in] Indicateurs définis dans Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="08f63-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="08f63-107">[out, optional] Une valeur qui indique le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="08f63-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08f63-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="08f63-108">Requirements</span></span>  
 <span data-ttu-id="08f63-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08f63-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08f63-110">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="08f63-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="08f63-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08f63-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f63-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08f63-112">See also</span></span>

- [<span data-ttu-id="08f63-113">IAssemblyCacheItem, interface</span><span class="sxs-lookup"><span data-stu-id="08f63-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
