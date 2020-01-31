---
title: COR_PRF_FUNCTION_ARGUMENT_RANGE, structure
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
ms.openlocfilehash: dae5ed7c25f85051d1a28681fb88b056617c4de0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867244"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="3f574-102">COR_PRF_FUNCTION_ARGUMENT_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="3f574-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="3f574-103">Représente un bloc d’arguments de fonction stockés de façon contiguë en mémoire selon un ordre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="3f574-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f574-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f574-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="3f574-105">Members</span><span class="sxs-lookup"><span data-stu-id="3f574-105">Members</span></span>  
  
|<span data-ttu-id="3f574-106">Members</span><span class="sxs-lookup"><span data-stu-id="3f574-106">Members</span></span>|<span data-ttu-id="3f574-107">Description</span><span class="sxs-lookup"><span data-stu-id="3f574-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="3f574-108">Adresse de début du bloc.</span><span class="sxs-lookup"><span data-stu-id="3f574-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="3f574-109">Longueur du bloc contigu.</span><span class="sxs-lookup"><span data-stu-id="3f574-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f574-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="3f574-110">Requirements</span></span>  
 <span data-ttu-id="3f574-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f574-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f574-112">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="3f574-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3f574-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f574-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f574-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f574-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f574-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f574-115">See also</span></span>

- [<span data-ttu-id="3f574-116">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="3f574-116">Profiling Structures</span></span>](profiling-structures.md)
