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
ms.openlocfilehash: 418ebb51df3f2d86011ee2e77022c3ee5c7ac0b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088234"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="322fd-102">ICorDebugArrayValue::HasBaseIndicies, méthode</span><span class="sxs-lookup"><span data-stu-id="322fd-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="322fd-103">Obtient une valeur qui indique si les dimensions de ce tableau ont un index de base différent de zéro.</span><span class="sxs-lookup"><span data-stu-id="322fd-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="322fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="322fd-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="322fd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="322fd-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="322fd-106">à Pointeur vers une valeur booléenne qui est `true` si une ou plusieurs dimensions de cet objet `ICorDebugArrayValue` ont un index de base différent de zéro ; dans le cas contraire, la valeur booléenne est `false`.</span><span class="sxs-lookup"><span data-stu-id="322fd-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="322fd-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="322fd-107">Requirements</span></span>  
 <span data-ttu-id="322fd-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="322fd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="322fd-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="322fd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="322fd-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="322fd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="322fd-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="322fd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
