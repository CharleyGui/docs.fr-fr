---
title: ICorDebugEval2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
ms.openlocfilehash: b597d95b5b25e5ebf04fac48e4f3fda312a9594c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976120"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="ceb74-102">ICorDebugEval2, interface</span><span class="sxs-lookup"><span data-stu-id="ceb74-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="ceb74-103">Étend « ICorDebugEval » pour assurer la prise en charge des types génériques.</span><span class="sxs-lookup"><span data-stu-id="ceb74-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ceb74-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ceb74-104">Methods</span></span>  
  
|<span data-ttu-id="ceb74-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ceb74-105">Method</span></span>|<span data-ttu-id="ceb74-106">Description</span><span class="sxs-lookup"><span data-stu-id="ceb74-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ceb74-107">CallParameterizedFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="ceb74-107">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="ceb74-108">Configure un appel au « ICorDebugFunction » spécifié, qui peut être imbriqué dans un type dont le constructeur prend des paramètres de type ou qui peut lui-même prendre des paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="ceb74-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="ceb74-109">CreateValueForType, méthode</span><span class="sxs-lookup"><span data-stu-id="ceb74-109">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="ceb74-110">Obtient un pointeur vers un nouveau « ICorDebugValue » du type spécifié, avec une valeur initiale de null ou zéro.</span><span class="sxs-lookup"><span data-stu-id="ceb74-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="ceb74-111">NewParameterizedArray, méthode</span><span class="sxs-lookup"><span data-stu-id="ceb74-111">NewParameterizedArray Method</span></span>](icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="ceb74-112">Alloue un nouveau tableau du type d’élément et des dimensions spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ceb74-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="ceb74-113">NewParameterizedObject, méthode</span><span class="sxs-lookup"><span data-stu-id="ceb74-113">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="ceb74-114">Instancie un nouvel objet de type paramétré et appelle la méthode de constructeur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="ceb74-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="ceb74-115">NewParameterizedObjectNoConstructor, méthode</span><span class="sxs-lookup"><span data-stu-id="ceb74-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="ceb74-116">Instancie un nouvel objet de type paramétrable de la classe spécifiée sans tenter d’appeler une méthode de constructeur</span><span class="sxs-lookup"><span data-stu-id="ceb74-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="ceb74-117">NewStringWithLength, méthode</span><span class="sxs-lookup"><span data-stu-id="ceb74-117">NewStringWithLength Method</span></span>](icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="ceb74-118">Crée une nouvelle chaîne de la longueur spécifiée avec le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="ceb74-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="ceb74-119">RudeAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="ceb74-119">RudeAbort Method</span></span>](icordebugeval2-rudeabort-method.md)|<span data-ttu-id="ceb74-120">Abandonne le calcul `ICorDebugEval2` en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ceb74-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ceb74-121">Notes </span><span class="sxs-lookup"><span data-stu-id="ceb74-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ceb74-122">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="ceb74-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceb74-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ceb74-123">Requirements</span></span>  
 <span data-ttu-id="ceb74-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceb74-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceb74-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ceb74-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ceb74-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ceb74-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ceb74-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceb74-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb74-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ceb74-128">See also</span></span>

- [<span data-ttu-id="ceb74-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ceb74-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
