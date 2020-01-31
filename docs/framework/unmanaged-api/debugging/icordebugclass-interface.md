---
title: ICorDebugClass, interface
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
ms.openlocfilehash: 7ac588591222a1abbc7b99ec7e973284c055f95e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784171"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="56d7d-102">ICorDebugClass, interface</span><span class="sxs-lookup"><span data-stu-id="56d7d-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="56d7d-103">Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur).</span><span class="sxs-lookup"><span data-stu-id="56d7d-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="56d7d-104">Si le type est générique, `ICorDebugClass` représente le type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="56d7d-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56d7d-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="56d7d-105">Methods</span></span>  
  
|<span data-ttu-id="56d7d-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="56d7d-106">Method</span></span>|<span data-ttu-id="56d7d-107">Description</span><span class="sxs-lookup"><span data-stu-id="56d7d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56d7d-108">GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="56d7d-108">GetModule Method</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="56d7d-109">Obtient le module qui définit cette classe.</span><span class="sxs-lookup"><span data-stu-id="56d7d-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="56d7d-110">GetStaticFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="56d7d-110">GetStaticFieldValue Method</span></span>](icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="56d7d-111">Obtient la valeur du champ statique spécifié.</span><span class="sxs-lookup"><span data-stu-id="56d7d-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="56d7d-112">GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="56d7d-112">GetToken Method</span></span>](icordebugclass-gettoken-method.md)|<span data-ttu-id="56d7d-113">Obtient le `TypeDef` jeton de métadonnées pour cette classe.</span><span class="sxs-lookup"><span data-stu-id="56d7d-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56d7d-114">Notes</span><span class="sxs-lookup"><span data-stu-id="56d7d-114">Remarks</span></span>  
 <span data-ttu-id="56d7d-115">L’interface `ICorDebugClass` représente un type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="56d7d-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="56d7d-116">L’interface ICorDebugType représente un type générique instancié.</span><span class="sxs-lookup"><span data-stu-id="56d7d-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="56d7d-117">Par exemple, `Hashtable<K, V>` serait représenté par `ICorDebugClass`, tandis que `Hashtable<Int32, String>` serait représenté par `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="56d7d-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="56d7d-118">Les types non génériques sont représentés par les `ICorDebugClass` et `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="56d7d-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="56d7d-119">La dernière interface a été introduite dans la version 2,0 de .NET Framework pour gérer l’instanciation de type.</span><span class="sxs-lookup"><span data-stu-id="56d7d-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56d7d-120">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="56d7d-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56d7d-121">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="56d7d-121">Requirements</span></span>  
 <span data-ttu-id="56d7d-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56d7d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56d7d-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56d7d-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56d7d-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56d7d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56d7d-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56d7d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d7d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56d7d-126">See also</span></span>

- [<span data-ttu-id="56d7d-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="56d7d-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
