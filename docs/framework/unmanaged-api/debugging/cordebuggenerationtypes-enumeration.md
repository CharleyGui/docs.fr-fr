---
title: CorDebugGenerationTypes, énumération
ms.date: 03/30/2017
api_name:
- CorDebugGenerationTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGenerationTypes
helpviewer_keywords:
- CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 193f5ffe96e89a00bed8a3c88ee346ba3ea9f2b4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740020"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="fd8cc-102">CorDebugGenerationTypes, énumération</span><span class="sxs-lookup"><span data-stu-id="fd8cc-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="fd8cc-103">Spécifie la génération d’une région de la mémoire sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="fd8cc-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd8cc-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="fd8cc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="fd8cc-105">Members</span></span>  
  
|<span data-ttu-id="fd8cc-106">Nom de membre</span><span class="sxs-lookup"><span data-stu-id="fd8cc-106">Member name</span></span>|<span data-ttu-id="fd8cc-107">Description</span><span class="sxs-lookup"><span data-stu-id="fd8cc-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="fd8cc-108">Génération 0.</span><span class="sxs-lookup"><span data-stu-id="fd8cc-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="fd8cc-109">Génération 1.</span><span class="sxs-lookup"><span data-stu-id="fd8cc-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="fd8cc-110">Génération 2.</span><span class="sxs-lookup"><span data-stu-id="fd8cc-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="fd8cc-111">Le tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="fd8cc-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd8cc-112">Notes</span><span class="sxs-lookup"><span data-stu-id="fd8cc-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd8cc-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fd8cc-113">Requirements</span></span>  
 <span data-ttu-id="fd8cc-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd8cc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd8cc-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd8cc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd8cc-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd8cc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd8cc-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd8cc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd8cc-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd8cc-118">See also</span></span>

- [<span data-ttu-id="fd8cc-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="fd8cc-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
