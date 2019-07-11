---
title: LogSwitchCallReason, énumération
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 894f74f12de7ed0754dcca34eacb815efc33c766
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752572"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="ae3d4-102">LogSwitchCallReason, énumération</span><span class="sxs-lookup"><span data-stu-id="ae3d4-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="ae3d4-103">Indique l'opération qui a été effectuée sur un commutateur de débogage/suivi.</span><span class="sxs-lookup"><span data-stu-id="ae3d4-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae3d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae3d4-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="ae3d4-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ae3d4-105">Members</span></span>  
  
|<span data-ttu-id="ae3d4-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ae3d4-106">Member</span></span>|<span data-ttu-id="ae3d4-107">Description</span><span class="sxs-lookup"><span data-stu-id="ae3d4-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="ae3d4-108">Un commutateur de débogage/suivi a été créé.</span><span class="sxs-lookup"><span data-stu-id="ae3d4-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="ae3d4-109">Un commutateur de débogage/suivi a été modifié.</span><span class="sxs-lookup"><span data-stu-id="ae3d4-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="ae3d4-110">Un commutateur de débogage/suivi a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="ae3d4-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae3d4-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ae3d4-111">Requirements</span></span>  
 <span data-ttu-id="ae3d4-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae3d4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae3d4-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae3d4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae3d4-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae3d4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae3d4-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae3d4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae3d4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae3d4-116">See also</span></span>

- [<span data-ttu-id="ae3d4-117">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="ae3d4-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
