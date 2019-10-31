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
ms.openlocfilehash: c7af194351290ad937e40a2fc8b960c2c242629c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132794"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="23dab-102">CorDebugMDAFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="23dab-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="23dab-103">Spécifie l'état du thread sur lequel l'Assistant Débogage managé est déclenché.</span><span class="sxs-lookup"><span data-stu-id="23dab-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23dab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23dab-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="23dab-105">Membres</span><span class="sxs-lookup"><span data-stu-id="23dab-105">Members</span></span>  
  
|<span data-ttu-id="23dab-106">Membre</span><span class="sxs-lookup"><span data-stu-id="23dab-106">Member</span></span>|<span data-ttu-id="23dab-107">Description</span><span class="sxs-lookup"><span data-stu-id="23dab-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="23dab-108">Le thread sur lequel l’Assistant Débogage managé a été déclenché a glissé depuis le déclenchement de l’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="23dab-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23dab-109">Notes</span><span class="sxs-lookup"><span data-stu-id="23dab-109">Remarks</span></span>  
 <span data-ttu-id="23dab-110">Lorsque la pile des appels ne décrit plus où l’Assistant Débogage managé a été déclenché à l’origine, le thread est considéré comme ayant *glissé*.</span><span class="sxs-lookup"><span data-stu-id="23dab-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="23dab-111">Il s’agit d’une circonstance inhabituelle résultant de l’exécution par le thread d’une opération non valide lors de la sortie.</span><span class="sxs-lookup"><span data-stu-id="23dab-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23dab-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="23dab-112">Requirements</span></span>  
 <span data-ttu-id="23dab-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23dab-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23dab-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23dab-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23dab-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23dab-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23dab-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23dab-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23dab-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23dab-117">See also</span></span>

- [<span data-ttu-id="23dab-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="23dab-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
