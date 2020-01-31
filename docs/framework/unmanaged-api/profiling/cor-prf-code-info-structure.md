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
ms.openlocfilehash: eaab5b7faeac3dd0fb64f0a387f437af44e7bc12
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867306"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="248e0-102">COR_PRF_CODE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="248e0-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="248e0-103">Représente un bloc contigu de code natif stocké en mémoire.</span><span class="sxs-lookup"><span data-stu-id="248e0-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="248e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="248e0-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="248e0-105">Members</span><span class="sxs-lookup"><span data-stu-id="248e0-105">Members</span></span>  
  
|<span data-ttu-id="248e0-106">Member</span><span class="sxs-lookup"><span data-stu-id="248e0-106">Member</span></span>|<span data-ttu-id="248e0-107">Description</span><span class="sxs-lookup"><span data-stu-id="248e0-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="248e0-108">Adresse de début du bloc de code contigu.</span><span class="sxs-lookup"><span data-stu-id="248e0-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="248e0-109">Taille du bloc.</span><span class="sxs-lookup"><span data-stu-id="248e0-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="248e0-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="248e0-110">Requirements</span></span>  
 <span data-ttu-id="248e0-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="248e0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="248e0-112">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="248e0-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="248e0-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="248e0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="248e0-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="248e0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="248e0-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="248e0-115">See also</span></span>

- [<span data-ttu-id="248e0-116">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="248e0-116">Profiling Structures</span></span>](profiling-structures.md)
