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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 362c01e0b08145919793cec011a856f0090e5c47
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752989"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="96f58-102">ICorDebugEval::NewObject, méthode</span><span class="sxs-lookup"><span data-stu-id="96f58-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="96f58-103">Alloue une nouvelle instance d’objet et appelle la méthode de constructeur spécifié.</span><span class="sxs-lookup"><span data-stu-id="96f58-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="96f58-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="96f58-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="96f58-105">Utilisez [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="96f58-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96f58-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96f58-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96f58-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="96f58-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="96f58-108">[in] Le constructeur à appeler.</span><span class="sxs-lookup"><span data-stu-id="96f58-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="96f58-109">[in] Taille du tableau `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="96f58-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="96f58-110">[in] Tableau d’objets ICorDebugValue, chacun d’eux représente un argument à passer au constructeur.</span><span class="sxs-lookup"><span data-stu-id="96f58-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96f58-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="96f58-111">Requirements</span></span>  
 <span data-ttu-id="96f58-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96f58-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96f58-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96f58-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96f58-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96f58-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96f58-115">**Versions du .NET framework :** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="96f58-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f58-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96f58-116">See also</span></span>

- [<span data-ttu-id="96f58-117">NewParameterizedObject, méthode</span><span class="sxs-lookup"><span data-stu-id="96f58-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
