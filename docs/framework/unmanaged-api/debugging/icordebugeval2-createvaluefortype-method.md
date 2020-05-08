---
title: ICorDebugEval2::CreateValueForType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: fd7acaa8bcb4d53893855bcd25ff68cf26e30354
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976159"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="b3144-102">ICorDebugEval2::CreateValueForType, méthode</span><span class="sxs-lookup"><span data-stu-id="b3144-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="b3144-103">Obtient un pointeur vers un nouveau ICorDebugValue du type spécifié, avec une valeur initiale de zéro ou null.</span><span class="sxs-lookup"><span data-stu-id="b3144-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3144-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3144-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3144-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b3144-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="b3144-106">dans Pointeur vers un objet ICorDebugType qui représente le type.</span><span class="sxs-lookup"><span data-stu-id="b3144-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b3144-107">à Pointeur vers l’adresse d’un `ICorDebugValue` objet qui représente la valeur.</span><span class="sxs-lookup"><span data-stu-id="b3144-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3144-108">Notes </span><span class="sxs-lookup"><span data-stu-id="b3144-108">Remarks</span></span>  
 <span data-ttu-id="b3144-109">`CreateValueForType`généralise [ICorDebugEval :: CreateValue](icordebugeval-createvalue-method.md) en vous permettant de spécifier un type d’objet arbitraire, y compris des types `List<int>`construits tels que.</span><span class="sxs-lookup"><span data-stu-id="b3144-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="b3144-110">Le seul objectif de cette méthode est de générer une valeur qui peut être passée à une évaluation de fonction.</span><span class="sxs-lookup"><span data-stu-id="b3144-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="b3144-111">Le type doit être une classe ou un type valeur.</span><span class="sxs-lookup"><span data-stu-id="b3144-111">The type must be a class or a value type.</span></span> <span data-ttu-id="b3144-112">Vous ne pouvez pas utiliser cette méthode pour créer des valeurs de tableau ou des valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="b3144-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3144-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b3144-113">Requirements</span></span>  
 <span data-ttu-id="b3144-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3144-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3144-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3144-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3144-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3144-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3144-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3144-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
