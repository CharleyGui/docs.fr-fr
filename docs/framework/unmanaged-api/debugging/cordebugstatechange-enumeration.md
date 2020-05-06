---
title: CorDebugStateChange, énumération
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
ms.openlocfilehash: d94422d25da91cd2a6653a95cbd852c3930a151a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795688"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="0ea85-102">CorDebugStateChange, énumération</span><span class="sxs-lookup"><span data-stu-id="0ea85-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="0ea85-103">Représente la quantité de données mises en cache à ignorer sur la base des modifications apportées au processus.</span><span class="sxs-lookup"><span data-stu-id="0ea85-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ea85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ea85-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="0ea85-105">Membres</span><span class="sxs-lookup"><span data-stu-id="0ea85-105">Members</span></span>

| <span data-ttu-id="0ea85-106">Membre</span><span class="sxs-lookup"><span data-stu-id="0ea85-106">Member</span></span>            | <span data-ttu-id="0ea85-107">Description</span><span class="sxs-lookup"><span data-stu-id="0ea85-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="0ea85-108">Le processus a atteint un nouvel état de mémoire via l'exécution en avant.</span><span class="sxs-lookup"><span data-stu-id="0ea85-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="0ea85-109">La mémoire du processus peut être arbitrairement différente de ce qu'elle était précédemment.</span><span class="sxs-lookup"><span data-stu-id="0ea85-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="0ea85-110">Notes </span><span class="sxs-lookup"><span data-stu-id="0ea85-110">Remarks</span></span>

 <span data-ttu-id="0ea85-111">Un membre de l' `CorDebugStateChange` énumération est fourni en tant qu’argument lorsque le débogueur `ProcessStateChanged` appelle la méthode avec [ICorDebugProcess4 ::P rocessStateChanged](icordebugprocess4-processstatechanged-method.md) ou [ICorDebugProcess6 ::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="0ea85-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="0ea85-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0ea85-112">Requirements</span></span>

 <span data-ttu-id="0ea85-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ea85-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="0ea85-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ea85-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="0ea85-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ea85-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="0ea85-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ea85-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0ea85-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ea85-117">See also</span></span>

- [<span data-ttu-id="0ea85-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="0ea85-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="0ea85-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="0ea85-119">Debugging</span></span>](index.md)
