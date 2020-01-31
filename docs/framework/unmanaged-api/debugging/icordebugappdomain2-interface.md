---
title: ICorDebugAppDomain2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
ms.openlocfilehash: 6f9bcec66ff613d19c1198ac9849ca28c978f537
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788940"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="78193-102">ICorDebugAppDomain2, interface</span><span class="sxs-lookup"><span data-stu-id="78193-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="78193-103">Fournit des méthodes pour utiliser des tableaux, des pointeurs, des pointeurs de fonction et des types référence.</span><span class="sxs-lookup"><span data-stu-id="78193-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="78193-104">Cette interface est une extension de l’interface ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="78193-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78193-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="78193-105">Methods</span></span>  
  
|<span data-ttu-id="78193-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="78193-106">Method</span></span>|<span data-ttu-id="78193-107">Description</span><span class="sxs-lookup"><span data-stu-id="78193-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78193-108">GetArrayOrPointerType, méthode</span><span class="sxs-lookup"><span data-stu-id="78193-108">GetArrayOrPointerType Method</span></span>](icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="78193-109">Obtient un tableau du type spécifié, ou un pointeur ou une référence au type spécifié.</span><span class="sxs-lookup"><span data-stu-id="78193-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="78193-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="78193-110">GetFunctionPointerType</span></span>](icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="78193-111">Obtient un pointeur vers une fonction qui a une signature donnée.</span><span class="sxs-lookup"><span data-stu-id="78193-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78193-112">Notes</span><span class="sxs-lookup"><span data-stu-id="78193-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78193-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="78193-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78193-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="78193-114">Requirements</span></span>  
 <span data-ttu-id="78193-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78193-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78193-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78193-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78193-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78193-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78193-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78193-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78193-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78193-119">See also</span></span>

- [<span data-ttu-id="78193-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="78193-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
