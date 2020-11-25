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
ms.openlocfilehash: 4f488741f4233f06c128e0a262ce798ef27af3ff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699623"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="e5042-102">ICorDebugClass, interface</span><span class="sxs-lookup"><span data-stu-id="e5042-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="e5042-103">Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur).</span><span class="sxs-lookup"><span data-stu-id="e5042-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="e5042-104">Si le type est générique, `ICorDebugClass` représente le type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="e5042-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5042-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e5042-105">Methods</span></span>  
  
|<span data-ttu-id="e5042-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="e5042-106">Method</span></span>|<span data-ttu-id="e5042-107">Description</span><span class="sxs-lookup"><span data-stu-id="e5042-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5042-108">GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="e5042-108">GetModule Method</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="e5042-109">Obtient le module qui définit cette classe.</span><span class="sxs-lookup"><span data-stu-id="e5042-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="e5042-110">GetStaticFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="e5042-110">GetStaticFieldValue Method</span></span>](icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="e5042-111">Obtient la valeur du champ statique spécifié.</span><span class="sxs-lookup"><span data-stu-id="e5042-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="e5042-112">GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="e5042-112">GetToken Method</span></span>](icordebugclass-gettoken-method.md)|<span data-ttu-id="e5042-113">Obtient le `TypeDef` jeton de métadonnées pour cette classe.</span><span class="sxs-lookup"><span data-stu-id="e5042-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5042-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="e5042-114">Remarks</span></span>  

 <span data-ttu-id="e5042-115">L' `ICorDebugClass` interface représente un type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="e5042-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="e5042-116">L’interface ICorDebugType représente un type générique instancié.</span><span class="sxs-lookup"><span data-stu-id="e5042-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="e5042-117">Par exemple, `Hashtable<K, V>` serait représenté par `ICorDebugClass` , tandis que `Hashtable<Int32, String>` serait représenté par `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="e5042-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="e5042-118">Les types non génériques sont représentés par `ICorDebugClass` et `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="e5042-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="e5042-119">La dernière interface a été introduite dans la version 2,0 de .NET Framework pour gérer l’instanciation de type.</span><span class="sxs-lookup"><span data-stu-id="e5042-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5042-120">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="e5042-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5042-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e5042-121">Requirements</span></span>  

 <span data-ttu-id="e5042-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5042-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5042-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5042-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5042-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5042-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5042-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5042-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5042-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5042-126">See also</span></span>

- [<span data-ttu-id="e5042-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e5042-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
