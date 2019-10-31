---
title: CorDebugDecodeEventFlagsWindows, énumération
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
ms.openlocfilehash: da3a100bd552eaa3233642b006e0265adbcac1ca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132212"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="889b2-102">CorDebugDecodeEventFlagsWindows, énumération</span><span class="sxs-lookup"><span data-stu-id="889b2-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="889b2-103">Fournit des informations supplémentaires sur les événements de débogage propres à la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="889b2-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="889b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="889b2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="889b2-105">Membres</span><span class="sxs-lookup"><span data-stu-id="889b2-105">Members</span></span>  
  
|<span data-ttu-id="889b2-106">Membre</span><span class="sxs-lookup"><span data-stu-id="889b2-106">Member</span></span>|<span data-ttu-id="889b2-107">Description</span><span class="sxs-lookup"><span data-stu-id="889b2-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="889b2-108">Indique que l'événement de débogage est une exception de première chance.</span><span class="sxs-lookup"><span data-stu-id="889b2-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="889b2-109">Notes</span><span class="sxs-lookup"><span data-stu-id="889b2-109">Remarks</span></span>  
 <span data-ttu-id="889b2-110">La méthode [ICorDebugProcess6 ::D ecodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) inclut un paramètre `dwFlags` qui fournit des informations supplémentaires sur un événement de débogage et dont la valeur dépend de l’architecture cible.</span><span class="sxs-lookup"><span data-stu-id="889b2-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="889b2-111">L'énumération `CorDebugDecodeEventFlagsWindows` peut être utilisée avec les événements de débogage sur la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="889b2-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="889b2-112">Cette énumération est destinée à une utilisation dans des scénarios de débogage .NET Native uniquement.</span><span class="sxs-lookup"><span data-stu-id="889b2-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="889b2-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="889b2-113">Requirements</span></span>  
 <span data-ttu-id="889b2-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="889b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="889b2-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="889b2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="889b2-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="889b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="889b2-117">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="889b2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="889b2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="889b2-118">See also</span></span>

- [<span data-ttu-id="889b2-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="889b2-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
