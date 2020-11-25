---
title: ICorDebugEval::CreateValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
ms.openlocfilehash: 41db6ac00d8646651d0e8433d076c37af6020071
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696152"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="be1c7-102">ICorDebugEval::CreateValue, méthode</span><span class="sxs-lookup"><span data-stu-id="be1c7-102">ICorDebugEval::CreateValue Method</span></span>

<span data-ttu-id="be1c7-103">Crée une valeur du type spécifié, avec une valeur initiale de zéro ou null.</span><span class="sxs-lookup"><span data-stu-id="be1c7-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="be1c7-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be1c7-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="be1c7-105">Utilisez [ICorDebugEval2 :: CreateValueForType,](icordebugeval2-createvaluefortype-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="be1c7-105">Use [ICorDebugEval2::CreateValueForType](icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be1c7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be1c7-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be1c7-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be1c7-107">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="be1c7-108">dans Valeur de l’énumération [CorElementType](../metadata/corelementtype-enumeration.md) qui spécifie le type de la valeur.</span><span class="sxs-lookup"><span data-stu-id="be1c7-108">[in] A value of the [CorElementType](../metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="be1c7-109">dans Pointeur vers un objet [ICorDebugClass](icordebugclass-interface.md) qui spécifie la classe de la valeur, si le type n’est pas un type primitif.</span><span class="sxs-lookup"><span data-stu-id="be1c7-109">[in] Pointer to an [ICorDebugClass](icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="be1c7-110">à Pointeur vers l’adresse d’un objet « ICorDebugValue » qui représente la valeur.</span><span class="sxs-lookup"><span data-stu-id="be1c7-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be1c7-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="be1c7-111">Remarks</span></span>  

 <span data-ttu-id="be1c7-112">`CreateValue` crée un `ICorDebugValue` objet du type donné dans le seul but de l’utiliser dans une évaluation de fonction.</span><span class="sxs-lookup"><span data-stu-id="be1c7-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="be1c7-113">Cet objet de valeur peut être utilisé pour passer des constantes utilisateur en tant que paramètres.</span><span class="sxs-lookup"><span data-stu-id="be1c7-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="be1c7-114">Si le type de la valeur est un type primitif, sa valeur initiale est zéro ou null.</span><span class="sxs-lookup"><span data-stu-id="be1c7-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="be1c7-115">Utilisez [ICorDebugGenericValue :: SetValue](icordebuggenericvalue-setvalue-method.md) pour définir la valeur d’un type primitif.</span><span class="sxs-lookup"><span data-stu-id="be1c7-115">Use [ICorDebugGenericValue::SetValue](icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="be1c7-116">Si la valeur de `elementType` est ELEMENT_TYPE_CLASS, vous recevez un « ICorDebugReferenceValue » (retourné dans `ppValue` ) représentant la référence d’objet null.</span><span class="sxs-lookup"><span data-stu-id="be1c7-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="be1c7-117">Vous pouvez utiliser cet objet pour passer NULL à une évaluation de fonction qui a des paramètres de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="be1c7-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="be1c7-118">Vous ne pouvez pas définir la valeur sur quoi que ce soit `ICorDebugValue` ; elle reste toujours null.</span><span class="sxs-lookup"><span data-stu-id="be1c7-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be1c7-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="be1c7-119">Requirements</span></span>  

 <span data-ttu-id="be1c7-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be1c7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be1c7-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be1c7-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be1c7-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be1c7-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be1c7-123">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="be1c7-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be1c7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be1c7-124">See also</span></span>

- [<span data-ttu-id="be1c7-125">CreateValueForType, méthode</span><span class="sxs-lookup"><span data-stu-id="be1c7-125">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="be1c7-126">ICorDebugEval, interface</span><span class="sxs-lookup"><span data-stu-id="be1c7-126">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
