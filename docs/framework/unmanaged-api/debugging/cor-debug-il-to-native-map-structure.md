---
title: COR_DEBUG_IL_TO_NATIVE_MAP, structure
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: babb1ace1385c241b782691f22bfb4fbb689e310
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274076"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="0f330-102">COR_DEBUG_IL_TO_NATIVE_MAP, structure</span><span class="sxs-lookup"><span data-stu-id="0f330-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="0f330-103">Contient les décalages qui sont utilisés pour mapper du code MSIL (Microsoft Intermediate Language) à du code natif.</span><span class="sxs-lookup"><span data-stu-id="0f330-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f330-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f330-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="0f330-105">Membres</span><span class="sxs-lookup"><span data-stu-id="0f330-105">Members</span></span>  
  
|<span data-ttu-id="0f330-106">Membre</span><span class="sxs-lookup"><span data-stu-id="0f330-106">Member</span></span>|<span data-ttu-id="0f330-107">Description</span><span class="sxs-lookup"><span data-stu-id="0f330-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="0f330-108">Offset du code MSIL.</span><span class="sxs-lookup"><span data-stu-id="0f330-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="0f330-109">Offset du début du code natif.</span><span class="sxs-lookup"><span data-stu-id="0f330-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="0f330-110">Offset de la fin du code natif.</span><span class="sxs-lookup"><span data-stu-id="0f330-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f330-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0f330-111">Requirements</span></span>  
 <span data-ttu-id="0f330-112">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f330-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f330-113">**En-tête :** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="0f330-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="0f330-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f330-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f330-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f330-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f330-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f330-116">See also</span></span>

- [<span data-ttu-id="0f330-117">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="0f330-117">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="0f330-118">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="0f330-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="0f330-119">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="0f330-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0f330-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="0f330-120">Debugging</span></span>](index.md)
