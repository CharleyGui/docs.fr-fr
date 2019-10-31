---
title: ICorDebugFunction::GetClass, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
ms.openlocfilehash: 887d207aea3de9296107c041816606b2f5947406
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124028"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="9781c-102">ICorDebugFunction::GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="9781c-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="9781c-103">Obtient un objet ICorDebugClass qui représente la classe dont cette fonction est membre.</span><span class="sxs-lookup"><span data-stu-id="9781c-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9781c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9781c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9781c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9781c-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="9781c-106">à Pointeur vers l’adresse de l’objet `ICorDebugClass` qui représente la classe, ou null, si cette fonction n’est pas membre d’une classe.</span><span class="sxs-lookup"><span data-stu-id="9781c-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9781c-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="9781c-107">Requirements</span></span>  
 <span data-ttu-id="9781c-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9781c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9781c-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9781c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9781c-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9781c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9781c-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9781c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
