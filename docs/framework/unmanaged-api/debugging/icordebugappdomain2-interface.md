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
ms.openlocfilehash: f20ae6977504f958b7bfa8e2f073b7db6e8b822b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731473"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="66e41-102">ICorDebugAppDomain2, interface</span><span class="sxs-lookup"><span data-stu-id="66e41-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="66e41-103">Fournit des méthodes pour utiliser des tableaux, des pointeurs, des pointeurs de fonction et des types référence.</span><span class="sxs-lookup"><span data-stu-id="66e41-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="66e41-104">Cette interface est une extension de l’interface ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="66e41-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66e41-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="66e41-105">Methods</span></span>  
  
|<span data-ttu-id="66e41-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="66e41-106">Method</span></span>|<span data-ttu-id="66e41-107">Description</span><span class="sxs-lookup"><span data-stu-id="66e41-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66e41-108">GetArrayOrPointerType, méthode</span><span class="sxs-lookup"><span data-stu-id="66e41-108">GetArrayOrPointerType Method</span></span>](icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="66e41-109">Obtient un tableau du type spécifié, ou un pointeur ou une référence au type spécifié.</span><span class="sxs-lookup"><span data-stu-id="66e41-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="66e41-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="66e41-110">GetFunctionPointerType</span></span>](icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="66e41-111">Obtient un pointeur vers une fonction qui a une signature donnée.</span><span class="sxs-lookup"><span data-stu-id="66e41-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66e41-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="66e41-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66e41-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="66e41-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e41-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="66e41-114">Requirements</span></span>  

 <span data-ttu-id="66e41-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66e41-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66e41-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66e41-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66e41-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66e41-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66e41-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66e41-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e41-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66e41-119">See also</span></span>

- [<span data-ttu-id="66e41-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="66e41-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
