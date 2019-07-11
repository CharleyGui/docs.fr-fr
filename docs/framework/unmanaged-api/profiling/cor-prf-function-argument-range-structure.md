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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0c0679dac84089577a2698ed8b0b5497a1a81e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753900"
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="4b29c-102">COR_PRF_FUNCTION_ARGUMENT_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="4b29c-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="4b29c-103">Représente un bloc d’arguments de fonction stockés de façon contiguë en mémoire selon un ordre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="4b29c-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b29c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b29c-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="4b29c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="4b29c-105">Members</span></span>  
  
|<span data-ttu-id="4b29c-106">Membres</span><span class="sxs-lookup"><span data-stu-id="4b29c-106">Members</span></span>|<span data-ttu-id="4b29c-107">Description</span><span class="sxs-lookup"><span data-stu-id="4b29c-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="4b29c-108">Adresse de départ du bloc.</span><span class="sxs-lookup"><span data-stu-id="4b29c-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="4b29c-109">La longueur du bloc contigu.</span><span class="sxs-lookup"><span data-stu-id="4b29c-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4b29c-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4b29c-110">Requirements</span></span>  
 <span data-ttu-id="4b29c-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b29c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b29c-112">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="4b29c-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4b29c-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b29c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b29c-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b29c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b29c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b29c-115">See also</span></span>

- [<span data-ttu-id="4b29c-116">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="4b29c-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
