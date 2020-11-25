---
title: ICorDebugMetaDataLocator, interface
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator
helpviewer_keywords:
- ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type:
- apiref
ms.openlocfilehash: dbf5c751e84dfd9bf0549e8ce79d07a90fb4a3b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710387"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="ae916-102">ICorDebugMetaDataLocator, interface</span><span class="sxs-lookup"><span data-stu-id="ae916-102">ICorDebugMetaDataLocator Interface</span></span>

<span data-ttu-id="ae916-103">Fournit des informations de métadonnées au débogueur.</span><span class="sxs-lookup"><span data-stu-id="ae916-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae916-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ae916-104">Methods</span></span>  
  
|<span data-ttu-id="ae916-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ae916-105">Method</span></span>|<span data-ttu-id="ae916-106">Description</span><span class="sxs-lookup"><span data-stu-id="ae916-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae916-107">GetMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="ae916-107">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="ae916-108">Indique au débogueur de retourner le chemin d’accès complet à un module dont les métadonnées sont nécessaires pour effectuer une opération demandée par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="ae916-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae916-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="ae916-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae916-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="ae916-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae916-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ae916-111">Requirements</span></span>  

 <span data-ttu-id="ae916-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae916-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae916-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae916-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae916-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae916-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae916-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae916-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae916-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae916-116">See also</span></span>

- [<span data-ttu-id="ae916-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ae916-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ae916-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="ae916-118">Debugging</span></span>](index.md)
