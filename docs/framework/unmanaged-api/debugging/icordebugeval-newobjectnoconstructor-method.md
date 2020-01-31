---
title: ICorDebugEval::NewObjectNoConstructor, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
ms.openlocfilehash: 45efa1939813a319e996a72fef62ada167b877c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788701"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="24f2d-102">ICorDebugEval::NewObjectNoConstructor, méthode</span><span class="sxs-lookup"><span data-stu-id="24f2d-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="24f2d-103">Alloue une nouvelle instance d’objet du type spécifié, sans tenter d’appeler une méthode de constructeur.</span><span class="sxs-lookup"><span data-stu-id="24f2d-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="24f2d-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="24f2d-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="24f2d-105">Utilisez [ICorDebugEval2 :: NewParameterizedObjectNoConstructor,](icordebugeval2-newparameterizedobjectnoconstructor-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="24f2d-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24f2d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24f2d-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24f2d-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="24f2d-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="24f2d-108">dans Pointeur vers un objet ICorDebugClass qui représente le type d’objet à instancier.</span><span class="sxs-lookup"><span data-stu-id="24f2d-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24f2d-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="24f2d-109">Requirements</span></span>  
 <span data-ttu-id="24f2d-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24f2d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24f2d-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24f2d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24f2d-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24f2d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24f2d-113">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="24f2d-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f2d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24f2d-114">See also</span></span>

- [<span data-ttu-id="24f2d-115">NewParameterizedObjectNoConstructor, méthode</span><span class="sxs-lookup"><span data-stu-id="24f2d-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
