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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57520b4a67eb164c8f8631dc4d63d32c655dafa2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753821"
---
# <a name="corprffunction-structure"></a><span data-ttu-id="b7d32-102">COR_PRF_FUNCTION, structure</span><span class="sxs-lookup"><span data-stu-id="b7d32-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="b7d32-103">Fournit une représentation unique d'une fonction en combinant son ID avec l'ID de sa version recompilée.</span><span class="sxs-lookup"><span data-stu-id="b7d32-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7d32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7d32-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="b7d32-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b7d32-105">Members</span></span>  
  
|<span data-ttu-id="b7d32-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b7d32-106">Member</span></span>|<span data-ttu-id="b7d32-107">Description</span><span class="sxs-lookup"><span data-stu-id="b7d32-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="b7d32-108">L’ID de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b7d32-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="b7d32-109">L’ID de la fonction recompilée.</span><span class="sxs-lookup"><span data-stu-id="b7d32-109">The ID of the recompiled function.</span></span> <span data-ttu-id="b7d32-110">La valeur 0 (zéro) représente la version d’origine de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b7d32-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7d32-111">Notes</span><span class="sxs-lookup"><span data-stu-id="b7d32-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7d32-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b7d32-112">Requirements</span></span>  
 <span data-ttu-id="b7d32-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7d32-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7d32-114">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b7d32-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b7d32-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7d32-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7d32-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7d32-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d32-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7d32-117">See also</span></span>

- [<span data-ttu-id="b7d32-118">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="b7d32-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
