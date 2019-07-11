---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4434f5d0eaa45c9cfcbadb20b29564f0643a2dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754437"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="13a0d-102">ICorDebugEval2::NewParameterizedObjectNoConstructor, méthode</span><span class="sxs-lookup"><span data-stu-id="13a0d-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="13a0d-103">Instancie un nouvel objet de type paramétrable de la classe spécifiée sans essayer d’appeler une méthode de constructeur.</span><span class="sxs-lookup"><span data-stu-id="13a0d-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13a0d-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13a0d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="13a0d-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="13a0d-106">[in] Pointeur vers un objet ICorDebugClass qui représente la classe de l’objet à instancier.</span><span class="sxs-lookup"><span data-stu-id="13a0d-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="13a0d-107">[in] Nombre d’arguments de type passés.</span><span class="sxs-lookup"><span data-stu-id="13a0d-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="13a0d-108">[in] Tableau de pointeurs, chacun pointant vers un objet de ICorDebugType qui représente un argument de type pour l’objet qui est en cours d’instanciation.</span><span class="sxs-lookup"><span data-stu-id="13a0d-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13a0d-109">Notes</span><span class="sxs-lookup"><span data-stu-id="13a0d-109">Remarks</span></span>  
 <span data-ttu-id="13a0d-110">Le `NewParameterizedObjectNoConstructor` méthode échouera si un nombre incorrect d’arguments de type ou de types d’arguments de type incorrects sont passés.</span><span class="sxs-lookup"><span data-stu-id="13a0d-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13a0d-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="13a0d-111">Requirements</span></span>  
 <span data-ttu-id="13a0d-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a0d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a0d-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13a0d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13a0d-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13a0d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13a0d-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13a0d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
