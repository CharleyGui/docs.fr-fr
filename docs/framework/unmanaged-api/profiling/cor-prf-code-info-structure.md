---
title: COR_PRF_CODE_INFO, structure
ms.date: 03/30/2017
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
ms.openlocfilehash: 9dbe0219f5932a9d212edaf5181b96335c47db0e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501012"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="3eec8-102">COR_PRF_CODE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="3eec8-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="3eec8-103">Représente un bloc contigu de code natif stocké en mémoire.</span><span class="sxs-lookup"><span data-stu-id="3eec8-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eec8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3eec8-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="3eec8-105">Membres</span><span class="sxs-lookup"><span data-stu-id="3eec8-105">Members</span></span>  
  
|<span data-ttu-id="3eec8-106">Membre</span><span class="sxs-lookup"><span data-stu-id="3eec8-106">Member</span></span>|<span data-ttu-id="3eec8-107">Description</span><span class="sxs-lookup"><span data-stu-id="3eec8-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="3eec8-108">Adresse de début du bloc de code contigu.</span><span class="sxs-lookup"><span data-stu-id="3eec8-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="3eec8-109">Taille du bloc.</span><span class="sxs-lookup"><span data-stu-id="3eec8-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3eec8-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3eec8-110">Requirements</span></span>  
 <span data-ttu-id="3eec8-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eec8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eec8-112">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="3eec8-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3eec8-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3eec8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3eec8-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eec8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eec8-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3eec8-115">See also</span></span>

- [<span data-ttu-id="3eec8-116">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="3eec8-116">Profiling Structures</span></span>](profiling-structures.md)
