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
ms.openlocfilehash: e024500ea66dcb42e712e07e976a709401160a27
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795766"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="d50df-102">CorDebugMDAFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="d50df-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="d50df-103">Spécifie l'état du thread sur lequel l'Assistant Débogage managé est déclenché.</span><span class="sxs-lookup"><span data-stu-id="d50df-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d50df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d50df-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d50df-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d50df-105">Members</span></span>  
  
|<span data-ttu-id="d50df-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d50df-106">Member</span></span>|<span data-ttu-id="d50df-107">Description</span><span class="sxs-lookup"><span data-stu-id="d50df-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="d50df-108">Le thread sur lequel l’Assistant Débogage managé a été déclenché a glissé depuis le déclenchement de l’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="d50df-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d50df-109">Notes </span><span class="sxs-lookup"><span data-stu-id="d50df-109">Remarks</span></span>  
 <span data-ttu-id="d50df-110">Lorsque la pile des appels ne décrit plus où l’Assistant Débogage managé a été déclenché à l’origine, le thread est considéré comme ayant *glissé*.</span><span class="sxs-lookup"><span data-stu-id="d50df-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="d50df-111">Il s’agit d’une circonstance inhabituelle résultant de l’exécution par le thread d’une opération non valide lors de la sortie.</span><span class="sxs-lookup"><span data-stu-id="d50df-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d50df-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d50df-112">Requirements</span></span>  
 <span data-ttu-id="d50df-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d50df-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d50df-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d50df-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d50df-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d50df-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d50df-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d50df-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d50df-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d50df-117">See also</span></span>

- [<span data-ttu-id="d50df-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="d50df-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
