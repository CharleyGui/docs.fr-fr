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
ms.openlocfilehash: cd17cbc808b7f8381ac320bb55999c6b0466c3d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723533"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="ba18c-102">ICLRDebuggingLibraryProvider, interface</span><span class="sxs-lookup"><span data-stu-id="ba18c-102">ICLRDebuggingLibraryProvider Interface</span></span>

<span data-ttu-id="ba18c-103">Comprend la méthode de [méthode ProvideLibrary,](iclrdebugginglibraryprovider-providelibrary-method.md) , qui obtient une interface de rappel de fournisseur de bibliothèque qui permet à Common Language Runtime bibliothèques de débogage spécifiques à la version d’être localisées et chargées à la demande.</span><span class="sxs-lookup"><span data-stu-id="ba18c-103">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba18c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ba18c-104">Methods</span></span>  
  
|<span data-ttu-id="ba18c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ba18c-105">Method</span></span>|<span data-ttu-id="ba18c-106">Description</span><span class="sxs-lookup"><span data-stu-id="ba18c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba18c-107">ProvideLibrary, méthode</span><span class="sxs-lookup"><span data-stu-id="ba18c-107">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="ba18c-108">Permet au débogueur de fournir un handle à un module qui peut être utilisé pour charger une bibliothèque de débogage.</span><span class="sxs-lookup"><span data-stu-id="ba18c-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ba18c-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ba18c-109">Requirements</span></span>  

 <span data-ttu-id="ba18c-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba18c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba18c-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba18c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba18c-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba18c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba18c-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba18c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba18c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba18c-114">See also</span></span>

- [<span data-ttu-id="ba18c-115">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ba18c-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ba18c-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="ba18c-116">Debugging</span></span>](index.md)
