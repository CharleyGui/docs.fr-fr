---
title: ICorDebugEval::NewObject, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: e9570d3c916123093f69e7f26d3778f1c7184b1f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976185"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="b1861-102">ICorDebugEval::NewObject, méthode</span><span class="sxs-lookup"><span data-stu-id="b1861-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="b1861-103">Alloue une nouvelle instance d’objet et appelle la méthode de constructeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b1861-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="b1861-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1861-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="b1861-105">Utilisez [ICorDebugEval2 :: NewParameterizedObject,](icordebugeval2-newparameterizedobject-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="b1861-105">Use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1861-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1861-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1861-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b1861-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="b1861-108">dans Constructeur à appeler.</span><span class="sxs-lookup"><span data-stu-id="b1861-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="b1861-109">[in] Taille du tableau `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="b1861-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="b1861-110">dans Tableau d’objets ICorDebugValue, chacun représentant un argument à passer au constructeur.</span><span class="sxs-lookup"><span data-stu-id="b1861-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1861-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b1861-111">Requirements</span></span>  
 <span data-ttu-id="b1861-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1861-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1861-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1861-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1861-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1861-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1861-115">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="b1861-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1861-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1861-116">See also</span></span>

- [<span data-ttu-id="b1861-117">NewParameterizedObject, méthode</span><span class="sxs-lookup"><span data-stu-id="b1861-117">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)
