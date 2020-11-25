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
ms.openlocfilehash: 189a276b4228038ab1d70620ce3a4a0f4342b245
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712519"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="2bf63-102">CorDebugGenerationTypes, énumération</span><span class="sxs-lookup"><span data-stu-id="2bf63-102">CorDebugGenerationTypes Enumeration</span></span>

<span data-ttu-id="2bf63-103">Spécifie la génération d’une région de la mémoire sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="2bf63-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bf63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bf63-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="2bf63-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2bf63-105">Members</span></span>  
  
|<span data-ttu-id="2bf63-106">Nom du membre</span><span class="sxs-lookup"><span data-stu-id="2bf63-106">Member name</span></span>|<span data-ttu-id="2bf63-107">Description</span><span class="sxs-lookup"><span data-stu-id="2bf63-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="2bf63-108">Génération 0.</span><span class="sxs-lookup"><span data-stu-id="2bf63-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="2bf63-109">Génération 1</span><span class="sxs-lookup"><span data-stu-id="2bf63-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="2bf63-110">Génération 2.</span><span class="sxs-lookup"><span data-stu-id="2bf63-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="2bf63-111">Tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="2bf63-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bf63-112">Notes</span><span class="sxs-lookup"><span data-stu-id="2bf63-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bf63-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2bf63-113">Requirements</span></span>  

 <span data-ttu-id="2bf63-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bf63-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bf63-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2bf63-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bf63-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bf63-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bf63-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bf63-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf63-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bf63-118">See also</span></span>

- [<span data-ttu-id="2bf63-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="2bf63-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
