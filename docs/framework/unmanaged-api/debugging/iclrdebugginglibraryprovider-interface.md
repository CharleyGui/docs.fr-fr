---
title: ICLRDebuggingLibraryProvider, interface
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
ms.openlocfilehash: a8d9348572ec0cf67c5facebb2053a7091661724
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793601"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="48e85-102">ICLRDebuggingLibraryProvider, interface</span><span class="sxs-lookup"><span data-stu-id="48e85-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="48e85-103">Comprend la méthode de [méthode ProvideLibrary,](iclrdebugginglibraryprovider-providelibrary-method.md) , qui obtient une interface de rappel de fournisseur de bibliothèque qui permet à Common Language Runtime bibliothèques de débogage spécifiques à la version d’être localisées et chargées à la demande.</span><span class="sxs-lookup"><span data-stu-id="48e85-103">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48e85-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="48e85-104">Methods</span></span>  
  
|<span data-ttu-id="48e85-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="48e85-105">Method</span></span>|<span data-ttu-id="48e85-106">Description</span><span class="sxs-lookup"><span data-stu-id="48e85-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48e85-107">ProvideLibrary, méthode</span><span class="sxs-lookup"><span data-stu-id="48e85-107">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="48e85-108">Permet au débogueur de fournir un handle à un module qui peut être utilisé pour charger une bibliothèque de débogage.</span><span class="sxs-lookup"><span data-stu-id="48e85-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="48e85-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="48e85-109">Requirements</span></span>  
 <span data-ttu-id="48e85-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48e85-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48e85-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48e85-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48e85-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48e85-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48e85-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48e85-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e85-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48e85-114">See also</span></span>

- [<span data-ttu-id="48e85-115">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="48e85-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="48e85-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="48e85-116">Debugging</span></span>](index.md)
