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
ms.openlocfilehash: 7aca5fcb5a55331756b4f98c08eb46fc4db1e289
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720332"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="28144-102">ICorDebugValue2, interface</span><span class="sxs-lookup"><span data-stu-id="28144-102">ICorDebugValue2 Interface</span></span>

<span data-ttu-id="28144-103">Étend l’interface « ICorDebugValue » pour assurer la prise en charge des objets « ICorDebugType ».</span><span class="sxs-lookup"><span data-stu-id="28144-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28144-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="28144-104">Methods</span></span>  
  
|<span data-ttu-id="28144-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="28144-105">Method</span></span>|<span data-ttu-id="28144-106">Description</span><span class="sxs-lookup"><span data-stu-id="28144-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28144-107">GetExactType, méthode</span><span class="sxs-lookup"><span data-stu-id="28144-107">GetExactType Method</span></span>](icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="28144-108">Obtient un pointeur d’interface vers un `ICorDebugType` objet qui représente le <xref:System.Type> de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="28144-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28144-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="28144-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28144-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="28144-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28144-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="28144-111">Requirements</span></span>  

 <span data-ttu-id="28144-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28144-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28144-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28144-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28144-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28144-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28144-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28144-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28144-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28144-116">See also</span></span>

- [<span data-ttu-id="28144-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="28144-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

- [<span data-ttu-id="28144-118">ICorDebugValue3, interface</span><span class="sxs-lookup"><span data-stu-id="28144-118">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
