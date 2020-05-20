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
ms.openlocfilehash: 4d29bb3886ffb51e1dfb9654f4d70ef7c568fd43
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420706"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="9dc3f-102">LogSwitchCallReason, énumération</span><span class="sxs-lookup"><span data-stu-id="9dc3f-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="9dc3f-103">Indique l'opération qui a été effectuée sur un commutateur de débogage/suivi.</span><span class="sxs-lookup"><span data-stu-id="9dc3f-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dc3f-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="9dc3f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9dc3f-105">Members</span></span>  
  
|<span data-ttu-id="9dc3f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9dc3f-106">Member</span></span>|<span data-ttu-id="9dc3f-107">Description</span><span class="sxs-lookup"><span data-stu-id="9dc3f-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="9dc3f-108">Un commutateur de débogage/suivi a été créé.</span><span class="sxs-lookup"><span data-stu-id="9dc3f-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="9dc3f-109">Un commutateur de débogage/suivi a été modifié.</span><span class="sxs-lookup"><span data-stu-id="9dc3f-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="9dc3f-110">Un commutateur de débogage/suivi a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="9dc3f-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9dc3f-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="9dc3f-111">Requirements</span></span>  
 <span data-ttu-id="9dc3f-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dc3f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dc3f-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9dc3f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9dc3f-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dc3f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dc3f-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dc3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc3f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dc3f-116">See also</span></span>

- [<span data-ttu-id="9dc3f-117">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="9dc3f-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
