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
ms.openlocfilehash: 72bcc2479f7b6f41b384fc2517f0b04694663398
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976146"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="49629-102">ICorDebugEval2::CallParameterizedFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="49629-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="49629-103">Configure un appel au ICorDebugFunction spécifié, qui peut être imbriqué à l’intérieur d’une classe dont le <xref:System.Type> constructeur accepte des paramètres ou peut <xref:System.Type> prendre lui-même des paramètres.</span><span class="sxs-lookup"><span data-stu-id="49629-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49629-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49629-104">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49629-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49629-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="49629-106">dans Pointeur vers un `ICorDebugFunction` objet qui représente la fonction à appeler.</span><span class="sxs-lookup"><span data-stu-id="49629-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="49629-107">dans Nombre d’arguments que prend la fonction.</span><span class="sxs-lookup"><span data-stu-id="49629-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="49629-108">dans Tableau de pointeurs, chacun pointant vers un objet ICorDebugType qui représente un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="49629-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="49629-109">dans Nombre de valeurs passées dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="49629-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="49629-110">dans Tableau de pointeurs, chacun pointant vers un objet ICorDebugValue qui représente une valeur passée dans un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="49629-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49629-111">Notes </span><span class="sxs-lookup"><span data-stu-id="49629-111">Remarks</span></span>  
 <span data-ttu-id="49629-112">`CallParameterizedFunction`est semblable à [ICorDebugEval :: CallFunction](icordebugeval-callfunction-method.md) , sauf que la fonction peut être à l’intérieur d’une classe avec des paramètres de type, peut lui-même prendre des paramètres de type, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="49629-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="49629-113">Les arguments de type doivent être fournis en premier pour la classe, puis pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="49629-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="49629-114">Si la fonction se trouve dans un domaine d’application différent, une transition est effectuée.</span><span class="sxs-lookup"><span data-stu-id="49629-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="49629-115">Toutefois, tous les arguments de type et de valeur doivent être dans le domaine d’application cible.</span><span class="sxs-lookup"><span data-stu-id="49629-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="49629-116">L’évaluation de fonction ne peut être effectuée que dans des scénarios limités.</span><span class="sxs-lookup"><span data-stu-id="49629-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="49629-117">Si `CallParameterizedFunction` ou `ICorDebugEval::CallFunction` échoue, le HRESULT retourné indique la raison la plus générale possible de l’échec.</span><span class="sxs-lookup"><span data-stu-id="49629-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49629-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="49629-118">Requirements</span></span>  
 <span data-ttu-id="49629-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49629-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49629-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49629-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49629-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49629-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49629-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49629-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
