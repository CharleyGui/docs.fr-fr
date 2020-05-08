---
title: ICorDebugClass2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: ff15297eb479f7474c9f07123a29263fb4da3205
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893974"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="d5c84-102">ICorDebugClass2, interface</span><span class="sxs-lookup"><span data-stu-id="d5c84-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="d5c84-103">Représente une classe générique ou une classe avec un paramètre de méthode de type <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="d5c84-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="d5c84-104">Cette interface étend [ICorDebugClass](icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d5c84-104">This interface extends [ICorDebugClass](icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5c84-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d5c84-105">Methods</span></span>  
  
|<span data-ttu-id="d5c84-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="d5c84-106">Method</span></span>|<span data-ttu-id="d5c84-107">Description</span><span class="sxs-lookup"><span data-stu-id="d5c84-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5c84-108">GetParameterizedType, méthode</span><span class="sxs-lookup"><span data-stu-id="d5c84-108">GetParameterizedType Method</span></span>](icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="d5c84-109">Obtient la déclaration de type pour cette classe.</span><span class="sxs-lookup"><span data-stu-id="d5c84-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="d5c84-110">SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="d5c84-110">SetJMCStatus Method</span></span>](icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="d5c84-111">Pour chaque méthode de cette classe, définit une valeur qui indique si la méthode est du code défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5c84-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5c84-112">Notes </span><span class="sxs-lookup"><span data-stu-id="d5c84-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5c84-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="d5c84-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c84-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d5c84-114">Requirements</span></span>  
 <span data-ttu-id="d5c84-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5c84-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5c84-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5c84-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5c84-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5c84-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5c84-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5c84-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c84-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5c84-119">See also</span></span>

- [<span data-ttu-id="d5c84-120">ICorDebugClass, interface</span><span class="sxs-lookup"><span data-stu-id="d5c84-120">ICorDebugClass Interface</span></span>](icordebugclass-interface.md)
- [<span data-ttu-id="d5c84-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d5c84-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
