---
title: ICorDebugType::EnumerateTypeParameters, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
ms.openlocfilehash: dc6bf4f02c49788e640c6e230f864e3ca8e71b0d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380007"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="443a9-102">ICorDebugType::EnumerateTypeParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="443a9-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="443a9-103">Obtient un pointeur d’interface vers un ICorDebugTypeEnum qui contient les <xref:System.Type> paramètres de la classe référencée par ce ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="443a9-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="443a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="443a9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="443a9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="443a9-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="443a9-106">à Pointeur vers l’adresse d’un `ICorDebugTypeEnum` qui contient les paramètres du type.</span><span class="sxs-lookup"><span data-stu-id="443a9-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="443a9-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="443a9-107">Remarks</span></span>  
 <span data-ttu-id="443a9-108">Vous pouvez utiliser `EnumerateTypeParameters` si la valeur CorElementType retournée par [ICorDebugType :: GetType](icordebugtype-gettype-method.md) est ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR ou ELEMENT_TYPE_FNPTR.</span><span class="sxs-lookup"><span data-stu-id="443a9-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="443a9-109">Le nombre de paramètres et leur ordre dépendent du type :</span><span class="sxs-lookup"><span data-stu-id="443a9-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="443a9-110">ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE : le nombre de paramètres de type contenus dans le `ICorDebugTypeEnum` retourné par cette méthode dépend du nombre de paramètres de type formels pour la classe correspondante.</span><span class="sxs-lookup"><span data-stu-id="443a9-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="443a9-111">Par exemple, si le type est `class Dict<String,int32>` , `EnumerateTypeParameters` retourne un `ICorDebugTypeEnum` qui contient des objets représentant `String` et `int32` en séquence.</span><span class="sxs-lookup"><span data-stu-id="443a9-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="443a9-112">ELEMENT_TYPE_FNPTR : le nombre de paramètres de type contenus dans le `ICorDebugTypeEnum` sera supérieur au nombre d’arguments accepté par la fonction.</span><span class="sxs-lookup"><span data-stu-id="443a9-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="443a9-113">Le premier paramètre de type contenu dans `ICorDebugTypeEnum` est le type de retour pour la fonction, et les paramètres de type suivants sont les paramètres de la fonction.</span><span class="sxs-lookup"><span data-stu-id="443a9-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="443a9-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR : un paramètre de type est retourné.</span><span class="sxs-lookup"><span data-stu-id="443a9-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="443a9-115">Par exemple, si le type est un type tableau tel que `int32[]` , `EnumerateTypeParameters` retourne un `ICorDebugTypeEnum` qui contient un objet représentant `int32` .</span><span class="sxs-lookup"><span data-stu-id="443a9-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="443a9-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="443a9-116">Requirements</span></span>  
 <span data-ttu-id="443a9-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="443a9-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="443a9-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="443a9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="443a9-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="443a9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="443a9-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="443a9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
