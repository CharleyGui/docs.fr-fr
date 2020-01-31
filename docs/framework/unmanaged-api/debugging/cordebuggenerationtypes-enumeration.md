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
ms.openlocfilehash: 6133b34a60fd06c1b75d69783760741b8de62071
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789342"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="73aa9-102">CorDebugGenerationTypes, énumération</span><span class="sxs-lookup"><span data-stu-id="73aa9-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="73aa9-103">Spécifie la génération d’une région de la mémoire sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="73aa9-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73aa9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73aa9-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="73aa9-105">Members</span><span class="sxs-lookup"><span data-stu-id="73aa9-105">Members</span></span>  
  
|<span data-ttu-id="73aa9-106">Nom du membre</span><span class="sxs-lookup"><span data-stu-id="73aa9-106">Member name</span></span>|<span data-ttu-id="73aa9-107">Description</span><span class="sxs-lookup"><span data-stu-id="73aa9-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="73aa9-108">Génération 0.</span><span class="sxs-lookup"><span data-stu-id="73aa9-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="73aa9-109">Génération 1.</span><span class="sxs-lookup"><span data-stu-id="73aa9-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="73aa9-110">Génération 2.</span><span class="sxs-lookup"><span data-stu-id="73aa9-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="73aa9-111">Tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="73aa9-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73aa9-112">Notes</span><span class="sxs-lookup"><span data-stu-id="73aa9-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73aa9-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="73aa9-113">Requirements</span></span>  
 <span data-ttu-id="73aa9-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73aa9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73aa9-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73aa9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73aa9-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73aa9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73aa9-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73aa9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73aa9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73aa9-118">See also</span></span>

- [<span data-ttu-id="73aa9-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="73aa9-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
