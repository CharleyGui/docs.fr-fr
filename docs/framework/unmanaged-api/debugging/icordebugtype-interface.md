---
title: ICorDebugType, interface
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
ms.openlocfilehash: 9407dda7aab337f667cd5043b562d0eac94f0f04
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711921"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="69ce8-102">ICorDebugType, interface</span><span class="sxs-lookup"><span data-stu-id="69ce8-102">ICorDebugType Interface</span></span>

<span data-ttu-id="69ce8-103">Représente un type, de base ou complexe (autrement dit, défini par l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="69ce8-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="69ce8-104">Si le type est générique, `ICorDebugType` représente le type générique instancié.</span><span class="sxs-lookup"><span data-stu-id="69ce8-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69ce8-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="69ce8-105">Methods</span></span>  
  
|<span data-ttu-id="69ce8-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="69ce8-106">Method</span></span>|<span data-ttu-id="69ce8-107">Description</span><span class="sxs-lookup"><span data-stu-id="69ce8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69ce8-108">EnumerateTypeParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="69ce8-108">EnumerateTypeParameters Method</span></span>](icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="69ce8-109">Obtient un pointeur d’interface vers un ICorDebugTypeEnum qui référence les <xref:System.Type> paramètres génériques de la classe référencée par ce `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="69ce8-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="69ce8-110">GetBase, méthode</span><span class="sxs-lookup"><span data-stu-id="69ce8-110">GetBase Method</span></span>](icordebugtype-getbase-method.md)|<span data-ttu-id="69ce8-111">Obtient un pointeur d’interface vers un `ICorDebugType` qui référence la classe de base de la classe référencée par ce `ICorDebugType` , le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="69ce8-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="69ce8-112">GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="69ce8-112">GetClass Method</span></span>](icordebugtype-getclass-method.md)|<span data-ttu-id="69ce8-113">Obtient un pointeur d’interface vers une ICorDebugClass qui référence le constructeur typé de ce `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="69ce8-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="69ce8-114">GetFirstTypeParameter, méthode</span><span class="sxs-lookup"><span data-stu-id="69ce8-114">GetFirstTypeParameter Method</span></span>](icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="69ce8-115">Obtient un pointeur d’interface vers un `ICorDebugType` qui référence le premier <xref:System.Type> paramètre générique pour le constructeur de la classe référencée par ce `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="69ce8-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="69ce8-116">GetRank, méthode</span><span class="sxs-lookup"><span data-stu-id="69ce8-116">GetRank Method</span></span>](icordebugtype-getrank-method.md)|<span data-ttu-id="69ce8-117">Obtient le nombre de dimensions dans un type de tableau.</span><span class="sxs-lookup"><span data-stu-id="69ce8-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="69ce8-118">GetStaticFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="69ce8-118">GetStaticFieldValue Method</span></span>](icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="69ce8-119">Obtient un pointeur d’interface vers un ICorDebugValue qui contient la valeur du champ statique référencé par le jeton de champ spécifié dans le frame de pile spécifié.</span><span class="sxs-lookup"><span data-stu-id="69ce8-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="69ce8-120">GetType, méthode</span><span class="sxs-lookup"><span data-stu-id="69ce8-120">GetType Method</span></span>](icordebugtype-gettype-method.md)|<span data-ttu-id="69ce8-121">Obtient une valeur CorElementType qui décrit le type natif de la common language runtime <xref:System.Type> référencée par ce `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="69ce8-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69ce8-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="69ce8-122">Remarks</span></span>  

 <span data-ttu-id="69ce8-123">Si le type est générique, `ICorDebugClass` représente le type non instancié.</span><span class="sxs-lookup"><span data-stu-id="69ce8-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="69ce8-124">L' `ICorDebugType` interface représente un type générique instancié.</span><span class="sxs-lookup"><span data-stu-id="69ce8-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="69ce8-125">Par exemple, Hashtable \<K, V> serait représenté par `ICorDebugClass` , alors que Hashtable \<Int32, String> serait représenté par `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="69ce8-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="69ce8-126">Les types non génériques sont représentés par `ICorDebugClass` et `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="69ce8-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="69ce8-127">La dernière interface a été introduite dans la version 2,0 de .NET Framework pour gérer l’instanciation de type.</span><span class="sxs-lookup"><span data-stu-id="69ce8-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69ce8-128">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="69ce8-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69ce8-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="69ce8-129">Requirements</span></span>  

 <span data-ttu-id="69ce8-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69ce8-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69ce8-131">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69ce8-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69ce8-132">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69ce8-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69ce8-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69ce8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69ce8-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69ce8-134">See also</span></span>

- [<span data-ttu-id="69ce8-135">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="69ce8-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
