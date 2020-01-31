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
ms.openlocfilehash: 6f4c96517375df4cd249b72953bf37812a498c0c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789359"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="9551f-102">CorDebugGCType, énumération</span><span class="sxs-lookup"><span data-stu-id="9551f-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="9551f-103">Indique si le récupérateur de mémoire s'exécute sur une station de travail ou sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="9551f-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9551f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9551f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9551f-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="9551f-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="9551f-106">Members</span><span class="sxs-lookup"><span data-stu-id="9551f-106">Members</span></span>  
  
|<span data-ttu-id="9551f-107">Nom du membre</span><span class="sxs-lookup"><span data-stu-id="9551f-107">Member name</span></span>|<span data-ttu-id="9551f-108">Description</span><span class="sxs-lookup"><span data-stu-id="9551f-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="9551f-109">Le garbage collector est en cours d’exécution sur une station de travail.</span><span class="sxs-lookup"><span data-stu-id="9551f-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="9551f-110">Le garbage collector est en cours d’exécution sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="9551f-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9551f-111">Notes</span><span class="sxs-lookup"><span data-stu-id="9551f-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9551f-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="9551f-112">Requirements</span></span>  
 <span data-ttu-id="9551f-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9551f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9551f-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9551f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9551f-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9551f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9551f-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9551f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9551f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9551f-117">See also</span></span>

- [<span data-ttu-id="9551f-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="9551f-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
