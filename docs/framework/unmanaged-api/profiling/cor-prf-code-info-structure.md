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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f236a74da04dfddef852514eccb02215ad2d15a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752386"
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="de550-102">COR_PRF_CODE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="de550-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="de550-103">Représente un bloc contigu de code natif stocké en mémoire.</span><span class="sxs-lookup"><span data-stu-id="de550-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de550-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de550-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="de550-105">Membres</span><span class="sxs-lookup"><span data-stu-id="de550-105">Members</span></span>  
  
|<span data-ttu-id="de550-106">Membre</span><span class="sxs-lookup"><span data-stu-id="de550-106">Member</span></span>|<span data-ttu-id="de550-107">Description</span><span class="sxs-lookup"><span data-stu-id="de550-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="de550-108">Adresse de départ du bloc contigu de code.</span><span class="sxs-lookup"><span data-stu-id="de550-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="de550-109">La taille du bloc.</span><span class="sxs-lookup"><span data-stu-id="de550-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="de550-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="de550-110">Requirements</span></span>  
 <span data-ttu-id="de550-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de550-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de550-112">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="de550-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="de550-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de550-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de550-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de550-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de550-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de550-115">See also</span></span>

- [<span data-ttu-id="de550-116">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="de550-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
