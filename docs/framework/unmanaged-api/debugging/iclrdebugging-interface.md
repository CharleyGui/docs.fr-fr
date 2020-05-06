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
ms.openlocfilehash: a3d4297e3b16dd1637e6293dbf7f04d4fbeda50f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860385"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="ce9e3-102">ICLRDebugging, interface</span><span class="sxs-lookup"><span data-stu-id="ce9e3-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="ce9e3-103">Fournit des méthodes qui gèrent le chargement et le déchargement des modules pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="ce9e3-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce9e3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ce9e3-104">Methods</span></span>  
  
|<span data-ttu-id="ce9e3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ce9e3-105">Method</span></span>|<span data-ttu-id="ce9e3-106">Description</span><span class="sxs-lookup"><span data-stu-id="ce9e3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce9e3-107">OpenVirtualProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="ce9e3-107">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="ce9e3-108">Obtient l’interface « ICorDebugProcess » qui correspond à un module common language runtime (CLR) chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ce9e3-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="ce9e3-109">CanUnloadNow, méthode</span><span class="sxs-lookup"><span data-stu-id="ce9e3-109">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="ce9e3-110">Détermine si une bibliothèque qui a été fournie par une interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) est toujours en cours d’utilisation ou si elle peut être déchargée.</span><span class="sxs-lookup"><span data-stu-id="ce9e3-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce9e3-111">Notes </span><span class="sxs-lookup"><span data-stu-id="ce9e3-111">Remarks</span></span>  
 <span data-ttu-id="ce9e3-112">Vous pouvez obtenir une instance de l' `ICLRDebugging` interface à l’aide de la fonction [CLRCreateInstance](../hosting/clrcreateinstance-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ce9e3-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce9e3-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ce9e3-113">Requirements</span></span>  
 <span data-ttu-id="ce9e3-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce9e3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce9e3-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce9e3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce9e3-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce9e3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce9e3-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce9e3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9e3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce9e3-118">See also</span></span>

- [<span data-ttu-id="ce9e3-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ce9e3-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ce9e3-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="ce9e3-120">Debugging</span></span>](index.md)
