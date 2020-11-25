---
title: CorDebugMDAFlags, énumération
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: 1bb99503481d917d41ae00a5ef73c8fa59e2a999
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696451"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="fa2ee-102">CorDebugMDAFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="fa2ee-102">CorDebugMDAFlags Enumeration</span></span>

<span data-ttu-id="fa2ee-103">Spécifie l'état du thread sur lequel l'Assistant Débogage managé est déclenché.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa2ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa2ee-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fa2ee-105">Membres</span><span class="sxs-lookup"><span data-stu-id="fa2ee-105">Members</span></span>  
  
|<span data-ttu-id="fa2ee-106">Membre</span><span class="sxs-lookup"><span data-stu-id="fa2ee-106">Member</span></span>|<span data-ttu-id="fa2ee-107">Description</span><span class="sxs-lookup"><span data-stu-id="fa2ee-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="fa2ee-108">Le thread sur lequel l’Assistant Débogage managé a été déclenché a glissé depuis le déclenchement de l’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa2ee-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="fa2ee-109">Remarks</span></span>  

 <span data-ttu-id="fa2ee-110">Lorsque la pile des appels ne décrit plus où l’Assistant Débogage managé a été déclenché à l’origine, le thread est considéré comme ayant *glissé*.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="fa2ee-111">Il s’agit d’une circonstance inhabituelle résultant de l’exécution par le thread d’une opération non valide lors de la sortie.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa2ee-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fa2ee-112">Requirements</span></span>  

 <span data-ttu-id="fa2ee-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa2ee-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa2ee-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa2ee-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa2ee-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa2ee-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa2ee-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa2ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa2ee-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa2ee-117">See also</span></span>

- [<span data-ttu-id="fa2ee-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="fa2ee-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
