---
title: ICorDebugThread4, interface
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: a0d6f3e109f92ad44eeeb1b1dec05e53015992a6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378365"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="a3454-102">ICorDebugThread4, interface</span><span class="sxs-lookup"><span data-stu-id="a3454-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="a3454-103">Fournit des informations sur le blocage des threads.</span><span class="sxs-lookup"><span data-stu-id="a3454-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3454-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a3454-104">Methods</span></span>  
  
|<span data-ttu-id="a3454-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="a3454-105">Method</span></span>|<span data-ttu-id="a3454-106">Description</span><span class="sxs-lookup"><span data-stu-id="a3454-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3454-107">GetBlockingObjects, méthode</span><span class="sxs-lookup"><span data-stu-id="a3454-107">GetBlockingObjects Method</span></span>](icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="a3454-108">Fournit une énumération ordonnée des structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) qui fournissent des informations sur le blocage des threads.</span><span class="sxs-lookup"><span data-stu-id="a3454-108">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="a3454-109">HadUnhandledException, méthode</span><span class="sxs-lookup"><span data-stu-id="a3454-109">HadUnhandledException Method</span></span>](icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="a3454-110">Indique si le thread a déjà eu une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="a3454-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="a3454-111">GetCurrentCustomDebuggerNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="a3454-111">GetCurrentCustomDebuggerNotification Method</span></span>](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="a3454-112">Obtient l’objet [ICorDebugManagedCallback3 :: CustomNotification,](icordebugmanagedcallback3-customnotification-method.md) actuel sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="a3454-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3454-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="a3454-113">Remarks</span></span>  
 <span data-ttu-id="a3454-114">Cette interface est une extension logique des interfaces ICorDebugThread, ICorDebugThread2 et [ICorDebugThread3](icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a3454-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3454-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="a3454-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3454-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a3454-116">Requirements</span></span>  
 <span data-ttu-id="a3454-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3454-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3454-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3454-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3454-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3454-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3454-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3454-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3454-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3454-121">See also</span></span>

- [<span data-ttu-id="a3454-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a3454-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a3454-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="a3454-123">Debugging</span></span>](index.md)
