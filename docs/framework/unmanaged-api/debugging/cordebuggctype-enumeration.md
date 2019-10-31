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
ms.openlocfilehash: b954aa0e4db10fd4b3bde951c7f27d18b8634f5a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132182"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="acb28-102">CorDebugGCType, énumération</span><span class="sxs-lookup"><span data-stu-id="acb28-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="acb28-103">Indique si le récupérateur de mémoire s'exécute sur une station de travail ou sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="acb28-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acb28-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="acb28-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="acb28-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="acb28-106">Membres</span><span class="sxs-lookup"><span data-stu-id="acb28-106">Members</span></span>  
  
|<span data-ttu-id="acb28-107">Nom de membre</span><span class="sxs-lookup"><span data-stu-id="acb28-107">Member name</span></span>|<span data-ttu-id="acb28-108">Description</span><span class="sxs-lookup"><span data-stu-id="acb28-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="acb28-109">Le garbage collector est en cours d’exécution sur une station de travail.</span><span class="sxs-lookup"><span data-stu-id="acb28-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="acb28-110">Le garbage collector est en cours d’exécution sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="acb28-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acb28-111">Notes</span><span class="sxs-lookup"><span data-stu-id="acb28-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acb28-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="acb28-112">Requirements</span></span>  
 <span data-ttu-id="acb28-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acb28-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acb28-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acb28-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acb28-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acb28-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acb28-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acb28-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb28-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acb28-117">See also</span></span>

- [<span data-ttu-id="acb28-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="acb28-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
