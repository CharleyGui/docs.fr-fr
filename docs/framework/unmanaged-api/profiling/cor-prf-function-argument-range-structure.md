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
ms.openlocfilehash: 223ad57f0b317bf75778d4e5355ec129185f5a29
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449488"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="92373-102">COR_PRF_FUNCTION_ARGUMENT_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="92373-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="92373-103">Représente un bloc d’arguments de fonction stockés de façon contiguë en mémoire selon un ordre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="92373-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92373-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92373-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="92373-105">Membres</span><span class="sxs-lookup"><span data-stu-id="92373-105">Members</span></span>  
  
|<span data-ttu-id="92373-106">Membres</span><span class="sxs-lookup"><span data-stu-id="92373-106">Members</span></span>|<span data-ttu-id="92373-107">Description</span><span class="sxs-lookup"><span data-stu-id="92373-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="92373-108">Adresse de début du bloc.</span><span class="sxs-lookup"><span data-stu-id="92373-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="92373-109">Longueur du bloc contigu.</span><span class="sxs-lookup"><span data-stu-id="92373-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92373-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="92373-110">Requirements</span></span>  
 <span data-ttu-id="92373-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92373-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92373-112">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="92373-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="92373-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92373-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92373-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92373-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92373-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92373-115">See also</span></span>

- [<span data-ttu-id="92373-116">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="92373-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
