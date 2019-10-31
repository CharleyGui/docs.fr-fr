---
title: ICorDebugEval::CallFunction, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
ms.openlocfilehash: 4ac26ef4449dc02230f26b1247616b4587d217b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085160"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="3d64a-102">ICorDebugEval::CallFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="3d64a-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="3d64a-103">Configure un appel à la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3d64a-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="3d64a-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3d64a-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3d64a-105">Utilisez [ICorDebugEval2 :: CallParameterizedFunction,](icordebugeval2-callparameterizedfunction-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="3d64a-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="3d64a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d64a-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="3d64a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d64a-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="3d64a-108">dans Pointeur vers un objet ICorDebugFunction qui spécifie la fonction à appeler.</span><span class="sxs-lookup"><span data-stu-id="3d64a-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="3d64a-109">dans Nombre d’arguments pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="3d64a-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="3d64a-110">dans Tableau de pointeurs, chacun pointant vers un objet ICorDebugValue qui spécifie un argument à passer à la fonction.</span><span class="sxs-lookup"><span data-stu-id="3d64a-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d64a-111">Notes</span><span class="sxs-lookup"><span data-stu-id="3d64a-111">Remarks</span></span>

<span data-ttu-id="3d64a-112">Si la fonction est virtuelle, `CallFunction` effectue une répartition virtuelle.</span><span class="sxs-lookup"><span data-stu-id="3d64a-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="3d64a-113">Si la fonction se trouve dans un domaine d’application différent, une transition est effectuée tant que tous les arguments sont également dans ce domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="3d64a-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="3d64a-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="3d64a-114">Requirements</span></span>

<span data-ttu-id="3d64a-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d64a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="3d64a-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d64a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="3d64a-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d64a-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3d64a-118">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="3d64a-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="3d64a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d64a-119">See also</span></span>

- [<span data-ttu-id="3d64a-120">CallParameterizedFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="3d64a-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)
