---
title: StackTrace_SimpleContext
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc0fc18e31b89b22ffd30d99a8b079ed7b87fa1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752501"
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="2b469-102">StackTrace_SimpleContext</span><span class="sxs-lookup"><span data-stu-id="2b469-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="2b469-103">Fournit un contexte simple qui peut être utilisé à la place d'une structure `CONTEXT` complète.</span><span class="sxs-lookup"><span data-stu-id="2b469-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b469-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b469-104">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="2b469-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2b469-105">Members</span></span>  
  
|<span data-ttu-id="2b469-106">Membre</span><span class="sxs-lookup"><span data-stu-id="2b469-106">Member</span></span>|<span data-ttu-id="2b469-107">Description</span><span class="sxs-lookup"><span data-stu-id="2b469-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="2b469-108">Le pointeur de pile ou le pointeur de pile d’entrée (ESP) sur x86 plateformes.</span><span class="sxs-lookup"><span data-stu-id="2b469-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="2b469-109">Le décalage de trame ou EBP sur x86 les plateformes.</span><span class="sxs-lookup"><span data-stu-id="2b469-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="2b469-110">Le pointeur d’instruction ou le pointeur d’instruction entrée (EIP) sur x86 plateformes.</span><span class="sxs-lookup"><span data-stu-id="2b469-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b469-111">Notes</span><span class="sxs-lookup"><span data-stu-id="2b469-111">Remarks</span></span>  
 <span data-ttu-id="2b469-112">Étant donné que les fonctions de trace de pile doivent généralement retourner uniquement l’adresse offset de frame et adresse de la pile, vous pouvez éventuellement utiliser le `SimpleContext` structure au lieu d’un grand `CONTEXT` structure.</span><span class="sxs-lookup"><span data-stu-id="2b469-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b469-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2b469-113">Requirements</span></span>  
 <span data-ttu-id="2b469-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b469-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b469-115">**En-tête :** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="2b469-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="2b469-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b469-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b469-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b469-117">See also</span></span>

- [<span data-ttu-id="2b469-118">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="2b469-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="2b469-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="2b469-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
