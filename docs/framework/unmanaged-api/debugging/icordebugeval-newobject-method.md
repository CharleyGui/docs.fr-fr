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
ms.openlocfilehash: 38cc98f1bfd966d1f764e43b30003a2bae66297d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793469"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="5a5b3-102">ICorDebugEval::NewObject, méthode</span><span class="sxs-lookup"><span data-stu-id="5a5b3-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="5a5b3-103">Alloue une nouvelle instance d’objet et appelle la méthode de constructeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5a5b3-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="5a5b3-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a5b3-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="5a5b3-105">Utilisez [ICorDebugEval2 :: NewParameterizedObject,](icordebugeval2-newparameterizedobject-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="5a5b3-105">Use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a5b3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a5b3-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a5b3-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="5a5b3-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="5a5b3-108">dans Constructeur à appeler.</span><span class="sxs-lookup"><span data-stu-id="5a5b3-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="5a5b3-109">[in] Taille du tableau `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="5a5b3-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="5a5b3-110">dans Tableau d’objets ICorDebugValue, chacun représentant un argument à passer au constructeur.</span><span class="sxs-lookup"><span data-stu-id="5a5b3-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a5b3-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="5a5b3-111">Requirements</span></span>  
 <span data-ttu-id="5a5b3-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a5b3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a5b3-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a5b3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a5b3-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a5b3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a5b3-115">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="5a5b3-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a5b3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a5b3-116">See also</span></span>

- [<span data-ttu-id="5a5b3-117">NewParameterizedObject, méthode</span><span class="sxs-lookup"><span data-stu-id="5a5b3-117">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)
