---
title: ICorDebugHandleValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: e695a93036e00e651ecababb0e1407661bcc48d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729081"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="f6d78-102">ICorDebugHandleValue, interface</span><span class="sxs-lookup"><span data-stu-id="f6d78-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="f6d78-103">Sous-classe de ICorDebugReferenceValue qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f6d78-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6d78-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f6d78-104">Methods</span></span>  
  
|<span data-ttu-id="f6d78-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f6d78-105">Method</span></span>|<span data-ttu-id="f6d78-106">Description</span><span class="sxs-lookup"><span data-stu-id="f6d78-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6d78-107">Dispose, méthode</span><span class="sxs-lookup"><span data-stu-id="f6d78-107">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="f6d78-108">Libère le handle référencé par cet `ICorDebugHandleValue` objet sans libérer explicitement le pointeur d’interface.</span><span class="sxs-lookup"><span data-stu-id="f6d78-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="f6d78-109">GetHandleType, méthode</span><span class="sxs-lookup"><span data-stu-id="f6d78-109">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="f6d78-110">Obtient une valeur CorDebugHandleType, qui décrit le genre de handle référencé par ce `ICorDebugHandleValue` .</span><span class="sxs-lookup"><span data-stu-id="f6d78-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6d78-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="f6d78-111">Remarks</span></span>  

 <span data-ttu-id="f6d78-112">Un `ICorDebugReferenceValue` objet est invalidé par un arrêt dans l’exécution du code débogué.</span><span class="sxs-lookup"><span data-stu-id="f6d78-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="f6d78-113">Un `ICorDebugHandleValue` maintient sa référence via des arrêts et des continuations, jusqu’à ce qu’il soit explicitement libéré.</span><span class="sxs-lookup"><span data-stu-id="f6d78-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6d78-114">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="f6d78-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6d78-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f6d78-115">Requirements</span></span>  

 <span data-ttu-id="f6d78-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6d78-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6d78-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6d78-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6d78-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6d78-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6d78-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6d78-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d78-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6d78-120">See also</span></span>

- [<span data-ttu-id="f6d78-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f6d78-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
