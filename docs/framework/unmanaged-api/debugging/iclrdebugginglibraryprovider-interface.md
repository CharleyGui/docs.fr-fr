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
ms.openlocfilehash: 81b9ffe5979ad553a5bdfbc27111469b2ff4db6f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111377"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="ac8ea-102">ICLRDebuggingLibraryProvider, interface</span><span class="sxs-lookup"><span data-stu-id="ac8ea-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="ac8ea-103">Comprend la méthode de [méthode ProvideLibrary,](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) , qui obtient une interface de rappel de fournisseur de bibliothèque qui permet à Common Language Runtime bibliothèques de débogage spécifiques à la version d’être localisées et chargées à la demande.</span><span class="sxs-lookup"><span data-stu-id="ac8ea-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ac8ea-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ac8ea-104">Methods</span></span>  
  
|<span data-ttu-id="ac8ea-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ac8ea-105">Method</span></span>|<span data-ttu-id="ac8ea-106">Description</span><span class="sxs-lookup"><span data-stu-id="ac8ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ac8ea-107">ProvideLibrary, méthode</span><span class="sxs-lookup"><span data-stu-id="ac8ea-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="ac8ea-108">Permet au débogueur de fournir un handle à un module qui peut être utilisé pour charger une bibliothèque de débogage.</span><span class="sxs-lookup"><span data-stu-id="ac8ea-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac8ea-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="ac8ea-109">Requirements</span></span>  
 <span data-ttu-id="ac8ea-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac8ea-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac8ea-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac8ea-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac8ea-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac8ea-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac8ea-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac8ea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac8ea-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac8ea-114">See also</span></span>

- [<span data-ttu-id="ac8ea-115">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ac8ea-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ac8ea-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="ac8ea-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
