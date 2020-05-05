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
ms.openlocfilehash: 7eccaf984b187e463195bb3804f87bbb2c7ad47b
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795922"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="ab2a1-102">CorDebugExceptionObjectStackFrame, structure</span><span class="sxs-lookup"><span data-stu-id="ab2a1-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="ab2a1-103">Représente les informations de frame de pile provenant d'un objet Exception.</span><span class="sxs-lookup"><span data-stu-id="ab2a1-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab2a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab2a1-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="ab2a1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ab2a1-105">Members</span></span>  
  
|<span data-ttu-id="ab2a1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ab2a1-106">Member</span></span>|<span data-ttu-id="ab2a1-107">Description</span><span class="sxs-lookup"><span data-stu-id="ab2a1-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="ab2a1-108">Pointeur vers l’objet ICorDebugModule pour le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="ab2a1-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="ab2a1-109">Valeur du pointeur d’instruction (EIP/RIP) du frame actuel.</span><span class="sxs-lookup"><span data-stu-id="ab2a1-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="ab2a1-110">Jeton de méthode pour le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="ab2a1-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="ab2a1-111">Valeur qui indique si le frame est le dernier frame dans une exception étrangère.</span><span class="sxs-lookup"><span data-stu-id="ab2a1-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab2a1-112">Notes </span><span class="sxs-lookup"><span data-stu-id="ab2a1-112">Remarks</span></span>  
 <span data-ttu-id="ab2a1-113">L’appelant doit libérer le pointeur vers l’objet ICorDebugModule une fois qu’il n’est plus utilisé.</span><span class="sxs-lookup"><span data-stu-id="ab2a1-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab2a1-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ab2a1-114">Requirements</span></span>  
 <span data-ttu-id="ab2a1-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab2a1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab2a1-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab2a1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab2a1-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab2a1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab2a1-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab2a1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab2a1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab2a1-119">See also</span></span>

- [<span data-ttu-id="ab2a1-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="ab2a1-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ab2a1-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="ab2a1-121">Debugging</span></span>](index.md)
