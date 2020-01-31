---
title: ICorDebugValue2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
ms.openlocfilehash: c6f20b0f7927d79ee56b5b6962137d668dc048d1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791117"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="dfcfa-102">ICorDebugValue2, interface</span><span class="sxs-lookup"><span data-stu-id="dfcfa-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="dfcfa-103">Étend l’interface « ICorDebugValue » pour assurer la prise en charge des objets « ICorDebugType ».</span><span class="sxs-lookup"><span data-stu-id="dfcfa-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dfcfa-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="dfcfa-104">Methods</span></span>  
  
|<span data-ttu-id="dfcfa-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="dfcfa-105">Method</span></span>|<span data-ttu-id="dfcfa-106">Description</span><span class="sxs-lookup"><span data-stu-id="dfcfa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dfcfa-107">GetExactType, méthode</span><span class="sxs-lookup"><span data-stu-id="dfcfa-107">GetExactType Method</span></span>](icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="dfcfa-108">Obtient un pointeur d’interface vers un objet `ICorDebugType` qui représente la <xref:System.Type> de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="dfcfa-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfcfa-109">Notes</span><span class="sxs-lookup"><span data-stu-id="dfcfa-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dfcfa-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="dfcfa-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfcfa-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="dfcfa-111">Requirements</span></span>  
 <span data-ttu-id="dfcfa-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfcfa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfcfa-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfcfa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfcfa-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfcfa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfcfa-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfcfa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfcfa-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfcfa-116">See also</span></span>

- [<span data-ttu-id="dfcfa-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="dfcfa-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

- [<span data-ttu-id="dfcfa-118">ICorDebugValue3, interface</span><span class="sxs-lookup"><span data-stu-id="dfcfa-118">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
