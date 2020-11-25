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
ms.openlocfilehash: bb27ec755fb83dc71af7dd48b5ed6e7699436335
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729727"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="67758-102">ICorDebugEval::NewObjectNoConstructor, méthode</span><span class="sxs-lookup"><span data-stu-id="67758-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>

<span data-ttu-id="67758-103">Alloue une nouvelle instance d’objet du type spécifié, sans tenter d’appeler une méthode de constructeur.</span><span class="sxs-lookup"><span data-stu-id="67758-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="67758-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67758-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="67758-105">Utilisez [ICorDebugEval2 :: NewParameterizedObjectNoConstructor,](icordebugeval2-newparameterizedobjectnoconstructor-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="67758-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67758-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67758-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67758-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="67758-107">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="67758-108">dans Pointeur vers un objet ICorDebugClass qui représente le type d’objet à instancier.</span><span class="sxs-lookup"><span data-stu-id="67758-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67758-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="67758-109">Requirements</span></span>  

 <span data-ttu-id="67758-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67758-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67758-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67758-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67758-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67758-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67758-113">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="67758-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67758-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67758-114">See also</span></span>

- [<span data-ttu-id="67758-115">NewParameterizedObjectNoConstructor, méthode</span><span class="sxs-lookup"><span data-stu-id="67758-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
