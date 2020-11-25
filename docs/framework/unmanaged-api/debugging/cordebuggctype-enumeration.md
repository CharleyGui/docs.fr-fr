---
title: CorDebugGCType, énumération
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
ms.openlocfilehash: 6b3075613af0403527ecf67d574c0f5733a5cd8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712610"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="67604-102">CorDebugGCType, énumération</span><span class="sxs-lookup"><span data-stu-id="67604-102">CorDebugGCType Enumeration</span></span>

<span data-ttu-id="67604-103">Indique si le récupérateur de mémoire s'exécute sur une station de travail ou sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="67604-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67604-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67604-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="67604-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="67604-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="67604-106">Membres</span><span class="sxs-lookup"><span data-stu-id="67604-106">Members</span></span>  
  
|<span data-ttu-id="67604-107">Nom du membre</span><span class="sxs-lookup"><span data-stu-id="67604-107">Member name</span></span>|<span data-ttu-id="67604-108">Description</span><span class="sxs-lookup"><span data-stu-id="67604-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="67604-109">Le garbage collector est en cours d’exécution sur une station de travail.</span><span class="sxs-lookup"><span data-stu-id="67604-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="67604-110">Le garbage collector est en cours d’exécution sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="67604-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67604-111">Notes</span><span class="sxs-lookup"><span data-stu-id="67604-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67604-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="67604-112">Requirements</span></span>  

 <span data-ttu-id="67604-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67604-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67604-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67604-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67604-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67604-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67604-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67604-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67604-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67604-117">See also</span></span>

- [<span data-ttu-id="67604-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="67604-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
