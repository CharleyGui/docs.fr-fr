---
title: ICorDebugModule::IsInMemory, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
ms.openlocfilehash: 637cac67e73d38aca0fdc5eaeae5405c4a859aa3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709815"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="98e51-102">ICorDebugModule::IsInMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="98e51-102">ICorDebugModule::IsInMemory Method</span></span>

<span data-ttu-id="98e51-103">Obtient une valeur qui indique si ce module existe uniquement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="98e51-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98e51-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98e51-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="98e51-105">Parameters</span></span>  

 `pInMemory`  
 <span data-ttu-id="98e51-106">[out] `true` Si ce module existe uniquement en mémoire ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="98e51-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98e51-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="98e51-107">Remarks</span></span>  

 <span data-ttu-id="98e51-108">Le common language runtime (CLR) prend en charge le chargement de modules à partir de flux bruts d’octets.</span><span class="sxs-lookup"><span data-stu-id="98e51-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="98e51-109">Ces modules sont appelés *modules en mémoire* et n’existent pas sur le disque.</span><span class="sxs-lookup"><span data-stu-id="98e51-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98e51-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="98e51-110">Requirements</span></span>  

 <span data-ttu-id="98e51-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98e51-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98e51-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98e51-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98e51-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98e51-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98e51-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98e51-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e51-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98e51-115">See also</span></span>
