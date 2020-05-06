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
ms.openlocfilehash: 77c2011ce677d1bd2823d47740782f48151b408a
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860282"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="d40ef-102">ICLRDebuggingLibraryProvider, interface</span><span class="sxs-lookup"><span data-stu-id="d40ef-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="d40ef-103">Comprend la méthode de [méthode ProvideLibrary,](iclrdebugginglibraryprovider-providelibrary-method.md) , qui obtient une interface de rappel de fournisseur de bibliothèque qui permet à Common Language Runtime bibliothèques de débogage spécifiques à la version d’être localisées et chargées à la demande.</span><span class="sxs-lookup"><span data-stu-id="d40ef-103">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d40ef-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d40ef-104">Methods</span></span>  
  
|<span data-ttu-id="d40ef-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d40ef-105">Method</span></span>|<span data-ttu-id="d40ef-106">Description</span><span class="sxs-lookup"><span data-stu-id="d40ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d40ef-107">ProvideLibrary, méthode</span><span class="sxs-lookup"><span data-stu-id="d40ef-107">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="d40ef-108">Permet au débogueur de fournir un handle à un module qui peut être utilisé pour charger une bibliothèque de débogage.</span><span class="sxs-lookup"><span data-stu-id="d40ef-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d40ef-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d40ef-109">Requirements</span></span>  
 <span data-ttu-id="d40ef-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d40ef-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d40ef-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d40ef-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d40ef-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d40ef-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d40ef-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d40ef-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40ef-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d40ef-114">See also</span></span>

- [<span data-ttu-id="d40ef-115">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d40ef-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d40ef-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="d40ef-116">Debugging</span></span>](index.md)
