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
ms.openlocfilehash: 1cd3c34fc292e4a050fa8a75078283e34425fc8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139127"
---
# <a name="stacktrace_simplecontext-structure"></a><span data-ttu-id="84283-102">StackTrace_SimpleContext</span><span class="sxs-lookup"><span data-stu-id="84283-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="84283-103">Fournit un contexte simple qui peut être utilisé à la place d'une structure `CONTEXT` complète.</span><span class="sxs-lookup"><span data-stu-id="84283-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84283-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84283-104">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="84283-105">Membres</span><span class="sxs-lookup"><span data-stu-id="84283-105">Members</span></span>  
  
|<span data-ttu-id="84283-106">Membre</span><span class="sxs-lookup"><span data-stu-id="84283-106">Member</span></span>|<span data-ttu-id="84283-107">Description</span><span class="sxs-lookup"><span data-stu-id="84283-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="84283-108">Pointeur de pile, ou le pointeur de pile Enter (ESP) sur les plateformes x86.</span><span class="sxs-lookup"><span data-stu-id="84283-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="84283-109">Décalage de frame ou registre EBP sur les plateformes x86.</span><span class="sxs-lookup"><span data-stu-id="84283-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="84283-110">Le pointeur d’instruction, ou le pointeur d’instruction Enter (EIP) sur les plateformes x86.</span><span class="sxs-lookup"><span data-stu-id="84283-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84283-111">Notes</span><span class="sxs-lookup"><span data-stu-id="84283-111">Remarks</span></span>  
 <span data-ttu-id="84283-112">Étant donné que les fonctions de trace de pile ne doivent généralement retourner que l’adresse, le décalage de frame et l’adresse de pile, vous pouvez éventuellement utiliser la structure `SimpleContext` au lieu d’une grande structure de `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="84283-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84283-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="84283-113">Requirements</span></span>  
 <span data-ttu-id="84283-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84283-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84283-115">**En-tête :** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="84283-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="84283-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84283-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84283-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84283-117">See also</span></span>

- [<span data-ttu-id="84283-118">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="84283-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="84283-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="84283-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
