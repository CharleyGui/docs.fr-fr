---
title: ICorDebugArrayValue::HasBaseIndicies, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c488ca3a77f2c2b2a40c6143989cd86adf071787
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737434"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="9b6e8-102">ICorDebugArrayValue::HasBaseIndicies, méthode</span><span class="sxs-lookup"><span data-stu-id="9b6e8-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="9b6e8-103">Obtient une valeur qui indique si toutes les dimensions de ce tableau ont un index de base de zéro.</span><span class="sxs-lookup"><span data-stu-id="9b6e8-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b6e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b6e8-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b6e8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9b6e8-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="9b6e8-106">[out] Un pointeur vers une valeur booléenne qui est `true` si une ou plusieurs dimensions de ce `ICorDebugArrayValue` objet a un index de base de zéro ; sinon, la valeur booléenne est `false`.</span><span class="sxs-lookup"><span data-stu-id="9b6e8-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b6e8-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9b6e8-107">Requirements</span></span>  
 <span data-ttu-id="9b6e8-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b6e8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b6e8-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b6e8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b6e8-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b6e8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b6e8-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b6e8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
