---
title: COR_PRF_FUNCTION, structure
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
ms.openlocfilehash: 40698a49ac7012c4f67eb88b1ead04c80f3dea77
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428325"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="1892c-102">COR_PRF_FUNCTION, structure</span><span class="sxs-lookup"><span data-stu-id="1892c-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="1892c-103">Fournit une représentation unique d'une fonction en combinant son ID avec l'ID de sa version recompilée.</span><span class="sxs-lookup"><span data-stu-id="1892c-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1892c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1892c-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="1892c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1892c-105">Members</span></span>  
  
|<span data-ttu-id="1892c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1892c-106">Member</span></span>|<span data-ttu-id="1892c-107">Description</span><span class="sxs-lookup"><span data-stu-id="1892c-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="1892c-108">ID de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1892c-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="1892c-109">ID de la fonction recompilée.</span><span class="sxs-lookup"><span data-stu-id="1892c-109">The ID of the recompiled function.</span></span> <span data-ttu-id="1892c-110">La valeur 0 (zéro) représente la version d’origine de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1892c-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1892c-111">Notes</span><span class="sxs-lookup"><span data-stu-id="1892c-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1892c-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1892c-112">Requirements</span></span>  
 <span data-ttu-id="1892c-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1892c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1892c-114">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="1892c-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1892c-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1892c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1892c-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1892c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1892c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1892c-117">See also</span></span>

- [<span data-ttu-id="1892c-118">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="1892c-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
