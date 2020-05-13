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
ms.openlocfilehash: 7b7b7a42edea775d1aaa850ccfc532ef86749991
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210022"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="0a3b6-102">ICorDebugMetaDataLocator, interface</span><span class="sxs-lookup"><span data-stu-id="0a3b6-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="0a3b6-103">Fournit des informations de métadonnées au débogueur.</span><span class="sxs-lookup"><span data-stu-id="0a3b6-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a3b6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0a3b6-104">Methods</span></span>  
  
|<span data-ttu-id="0a3b6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0a3b6-105">Method</span></span>|<span data-ttu-id="0a3b6-106">Description</span><span class="sxs-lookup"><span data-stu-id="0a3b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a3b6-107">GetMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="0a3b6-107">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="0a3b6-108">Indique au débogueur de retourner le chemin d’accès complet à un module dont les métadonnées sont nécessaires pour effectuer une opération demandée par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="0a3b6-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a3b6-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="0a3b6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a3b6-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="0a3b6-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a3b6-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0a3b6-111">Requirements</span></span>  
 <span data-ttu-id="0a3b6-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a3b6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a3b6-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a3b6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a3b6-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a3b6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a3b6-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a3b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3b6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a3b6-116">See also</span></span>

- [<span data-ttu-id="0a3b6-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0a3b6-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0a3b6-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="0a3b6-118">Debugging</span></span>](index.md)
