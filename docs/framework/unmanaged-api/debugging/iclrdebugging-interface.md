---
title: ICLRDebugging, interface
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 9a768535c3bf69b5127777de4cee27054943091d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793639"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="d78a6-102">ICLRDebugging, interface</span><span class="sxs-lookup"><span data-stu-id="d78a6-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="d78a6-103">Fournit des méthodes qui gèrent le chargement et le déchargement des modules pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="d78a6-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d78a6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d78a6-104">Methods</span></span>  
  
|<span data-ttu-id="d78a6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d78a6-105">Method</span></span>|<span data-ttu-id="d78a6-106">Description</span><span class="sxs-lookup"><span data-stu-id="d78a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d78a6-107">OpenVirtualProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="d78a6-107">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="d78a6-108">Obtient l’interface « ICorDebugProcess » qui correspond à un module common language runtime (CLR) chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d78a6-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="d78a6-109">CanUnloadNow, méthode</span><span class="sxs-lookup"><span data-stu-id="d78a6-109">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="d78a6-110">Détermine si une bibliothèque qui a été fournie par une interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) est toujours en cours d’utilisation ou si elle peut être déchargée.</span><span class="sxs-lookup"><span data-stu-id="d78a6-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d78a6-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d78a6-111">Remarks</span></span>  
 <span data-ttu-id="d78a6-112">Vous pouvez obtenir une instance de l’interface `ICLRDebugging` à l’aide de la fonction [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) .</span><span class="sxs-lookup"><span data-stu-id="d78a6-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d78a6-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d78a6-113">Requirements</span></span>  
 <span data-ttu-id="d78a6-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d78a6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d78a6-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d78a6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d78a6-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d78a6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d78a6-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d78a6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d78a6-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d78a6-118">See also</span></span>

- [<span data-ttu-id="d78a6-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d78a6-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d78a6-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="d78a6-120">Debugging</span></span>](index.md)
