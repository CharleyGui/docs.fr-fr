---
title: ICorDebugCode2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9cb7be64089a55e7b653fcd6272219abba311af8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960808"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="69c08-102">ICorDebugCode2, interface</span><span class="sxs-lookup"><span data-stu-id="69c08-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="69c08-103">Fournit des méthodes qui étendent les fonctionnalités de «ICorDebugCode».</span><span class="sxs-lookup"><span data-stu-id="69c08-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69c08-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="69c08-104">Methods</span></span>  
  
|<span data-ttu-id="69c08-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="69c08-105">Method</span></span>|<span data-ttu-id="69c08-106">Description</span><span class="sxs-lookup"><span data-stu-id="69c08-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69c08-107">GetCodeChunks, méthode</span><span class="sxs-lookup"><span data-stu-id="69c08-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="69c08-108">Obtient les blocs de code composés de cet objet de code.</span><span class="sxs-lookup"><span data-stu-id="69c08-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="69c08-109">GetCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="69c08-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="69c08-110">Obtient les indicateurs qui spécifient les conditions sous lesquelles cet objet de code a été compilé juste-à-temps (JIT) ou généré à l’aide du générateur d’images natives (Ngen. exe).</span><span class="sxs-lookup"><span data-stu-id="69c08-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69c08-111">Notes</span><span class="sxs-lookup"><span data-stu-id="69c08-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69c08-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="69c08-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69c08-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="69c08-113">Requirements</span></span>  
 <span data-ttu-id="69c08-114">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69c08-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69c08-115">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="69c08-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69c08-116">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69c08-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69c08-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69c08-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c08-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69c08-118">See also</span></span>

- [<span data-ttu-id="69c08-119">ICorDebugCode3, interface</span><span class="sxs-lookup"><span data-stu-id="69c08-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="69c08-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="69c08-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
