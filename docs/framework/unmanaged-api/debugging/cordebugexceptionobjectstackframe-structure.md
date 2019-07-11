---
title: CorDebugExceptionObjectStackFrame, structure
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cd2add7e96a8edaff8509563ae1846e80132001
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740101"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="1aaed-102">CorDebugExceptionObjectStackFrame, structure</span><span class="sxs-lookup"><span data-stu-id="1aaed-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="1aaed-103">Représente les informations de frame de pile provenant d'un objet Exception.</span><span class="sxs-lookup"><span data-stu-id="1aaed-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aaed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1aaed-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="1aaed-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1aaed-105">Members</span></span>  
  
|<span data-ttu-id="1aaed-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1aaed-106">Member</span></span>|<span data-ttu-id="1aaed-107">Description</span><span class="sxs-lookup"><span data-stu-id="1aaed-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="1aaed-108">Pointeur vers l’objet ICorDebugModule pour le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="1aaed-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="1aaed-109">La valeur de pointeur d’instruction (EIP/RIP) pour le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="1aaed-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="1aaed-110">Le jeton de méthode pour le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="1aaed-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="1aaed-111">Une valeur qui indique si le frame est la dernière image étrangère d’une exception.</span><span class="sxs-lookup"><span data-stu-id="1aaed-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1aaed-112">Notes</span><span class="sxs-lookup"><span data-stu-id="1aaed-112">Remarks</span></span>  
 <span data-ttu-id="1aaed-113">L’appelant doit libérer le pointeur vers l’objet ICorDebugModule une fois qu’il n’est plus en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="1aaed-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aaed-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1aaed-114">Requirements</span></span>  
 <span data-ttu-id="1aaed-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aaed-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aaed-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1aaed-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1aaed-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1aaed-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aaed-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aaed-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aaed-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1aaed-119">See also</span></span>

- [<span data-ttu-id="1aaed-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="1aaed-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="1aaed-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="1aaed-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
