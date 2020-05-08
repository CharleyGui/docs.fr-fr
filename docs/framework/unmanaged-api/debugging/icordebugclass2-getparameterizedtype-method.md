---
title: ICorDebugClass2::GetParameterizedType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
ms.openlocfilehash: 329bcee441b395982a8a8b539c0a938fa8170b14
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894055"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="a5ad7-102">ICorDebugClass2::GetParameterizedType, méthode</span><span class="sxs-lookup"><span data-stu-id="a5ad7-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="a5ad7-103">Obtient la déclaration de type pour cette classe.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ad7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5ad7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5ad7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a5ad7-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="a5ad7-106">dans Valeur de l’énumération CorElementType qui spécifie le type d’élément de cette classe : définissez cette valeur sur ELEMENT_TYPE_VALUETYPE si ce ICorDebugClass2 représente un type valeur.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="a5ad7-107">Définissez cette valeur sur ELEMENT_TYPE_CLASS si ce `ICorDebugClass2` représente un type complexe.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="a5ad7-108">dans Nombre de paramètres de type, si le type est générique.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="a5ad7-109">Le nombre de paramètres de type (le cas échéant) doit correspondre au nombre requis par la classe.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="a5ad7-110">dans Tableau de pointeurs, chacun pointant vers un objet ICorDebugType qui représente un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="a5ad7-111">Si la classe n’est pas générique, cette valeur est null.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="a5ad7-112">à Pointeur vers l’adresse d’un `ICorDebugType` objet qui représente la déclaration de type.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="a5ad7-113">Cet objet est équivalent à un <xref:System.Type> objet dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5ad7-114">Notes </span><span class="sxs-lookup"><span data-stu-id="a5ad7-114">Remarks</span></span>  
 <span data-ttu-id="a5ad7-115">Si la classe n’est pas générique, autrement dit, si elle n’a pas de paramètres `GetParameterizedType` de type, obtient simplement l’objet de type au moment de l’exécution correspondant à la classe.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="a5ad7-116">Le `elementType` paramètre doit être défini sur le type d’élément correct pour la classe : ELEMENT_TYPE_VALUETYPE si la classe est un type valeur ; Sinon, ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="a5ad7-117">Si la classe accepte des paramètres de type (par `ArrayList<T>`exemple,), vous `GetParameterizedType` pouvez utiliser pour construire un objet de type pour un type instancié `ArrayList<int>`tel que.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="a5ad7-118">Informations générales</span><span class="sxs-lookup"><span data-stu-id="a5ad7-118">Background Information</span></span>  
 <span data-ttu-id="a5ad7-119">Dans les versions 1,0 et 1,1 de .NET Framework, chaque type dans les métadonnées peut être mappé directement à un type dans le processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="a5ad7-120">Ainsi, un type de métadonnées et un type de Runtime ont une représentation unique dans le processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="a5ad7-121">Toutefois, un type générique dans les métadonnées peut être mappé à de nombreuses instanciations différentes du type dans le processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="a5ad7-122">Par exemple `SortedList<K,V>` , le type de métadonnées peut `SortedList<String, EmployeeRecord>`être `SortedList<Int32, String>`mappé `SortedList<String,Array<Int32>>`à,,, etc.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="a5ad7-123">Par conséquent, vous avez besoin d’un moyen de gérer l’instanciation de type.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="a5ad7-124">La version de .NET Framework 2,0 introduit `ICorDebugType` l’interface.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="a5ad7-125">Pour un type générique, un `ICorDebugClass` objet `ICorDebugClass2` ou représente le type non instancié (`SortedList<K,V>`) et un `ICorDebugType` objet représente les différents types instanciés.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="a5ad7-126">À partir `ICorDebugClass` d' `ICorDebugClass2` un objet ou, vous pouvez `ICorDebugType` créer un objet pour toute instanciation `ICorDebugClass2::GetParameterizedType` en appelant la méthode.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="a5ad7-127">Vous pouvez également créer un `ICorDebugType` objet pour un type simple, tel que Int32, ou pour un type non générique.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="a5ad7-128">L’introduction de l' `ICorDebugType` objet pour représenter la notion d’exécution d’un type a un effet ondulation sur l’ensemble de l’API.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="a5ad7-129">Les fonctions qui prenaient précédemment `ICorDebugClass` un `ICorDebugClass2` objet ou, ou `CorElementType` même une valeur, sont généralisées `ICorDebugType` pour prendre un objet.</span><span class="sxs-lookup"><span data-stu-id="a5ad7-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5ad7-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a5ad7-130">Requirements</span></span>  
 <span data-ttu-id="a5ad7-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5ad7-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5ad7-132">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5ad7-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5ad7-133">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5ad7-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5ad7-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5ad7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
