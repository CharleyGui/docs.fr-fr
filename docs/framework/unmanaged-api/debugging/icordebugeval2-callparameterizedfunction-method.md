---
title: ICorDebugEval2::CallParameterizedFunction, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2779cfaecfdd241b5317ac8b467222e045d48049
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753320"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="82c07-102">ICorDebugEval2::CallParameterizedFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="82c07-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="82c07-103">Définit un appel à ICorDebugFunction spécifié, qui peut être imbriquée dans une classe dont le constructeur prend <xref:System.Type> paramètres, ou peut lui-même prendre <xref:System.Type> paramètres.</span><span class="sxs-lookup"><span data-stu-id="82c07-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82c07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82c07-104">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82c07-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82c07-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="82c07-106">[in] Un pointeur vers un `ICorDebugFunction` objet qui représente la fonction à appeler.</span><span class="sxs-lookup"><span data-stu-id="82c07-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="82c07-107">[in] Le nombre d’arguments qui prend la fonction.</span><span class="sxs-lookup"><span data-stu-id="82c07-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="82c07-108">[in] Tableau de pointeurs, chacun pointant vers un objet de ICorDebugType qui représente un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="82c07-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="82c07-109">[in] Le nombre de valeurs passées dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="82c07-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="82c07-110">[in] Un tableau de pointeurs, chacun pointant vers un objet ICorDebugValue qui représente une valeur passée dans un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="82c07-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82c07-111">Notes</span><span class="sxs-lookup"><span data-stu-id="82c07-111">Remarks</span></span>  
 <span data-ttu-id="82c07-112">`CallParameterizedFunction` est semblable à [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) , à ceci près que la fonction peut être à l’intérieur d’une classe avec des paramètres de type, peut prendre elle-même les paramètres de type, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="82c07-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="82c07-113">Les arguments de type convient tout d’abord pour la classe, puis pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="82c07-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="82c07-114">Si la fonction est dans un domaine d’application différent, une transition se produit.</span><span class="sxs-lookup"><span data-stu-id="82c07-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="82c07-115">Toutefois, tous les arguments de type et la valeur doivent être dans le domaine d’application cible.</span><span class="sxs-lookup"><span data-stu-id="82c07-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="82c07-116">Évaluation de fonction peut être effectuée uniquement dans des scénarios limités.</span><span class="sxs-lookup"><span data-stu-id="82c07-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="82c07-117">Si `CallParameterizedFunction` ou `ICorDebugEval::CallFunction` échoue, le HRESULT retourné indiquera la raison possible la plus générale de l’échec.</span><span class="sxs-lookup"><span data-stu-id="82c07-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82c07-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="82c07-118">Requirements</span></span>  
 <span data-ttu-id="82c07-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82c07-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82c07-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82c07-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82c07-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82c07-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82c07-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82c07-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
