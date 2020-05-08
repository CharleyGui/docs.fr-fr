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
ms.openlocfilehash: e6e8eb91bbc41faf0dcea010da9aa54995058653
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894981"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="1f040-102">ICorDebugArrayValue::HasBaseIndicies, méthode</span><span class="sxs-lookup"><span data-stu-id="1f040-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="1f040-103">Obtient une valeur qui indique si les dimensions de ce tableau ont un index de base différent de zéro.</span><span class="sxs-lookup"><span data-stu-id="1f040-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f040-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f040-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f040-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1f040-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="1f040-106">à Pointeur vers une valeur booléenne qui est `true` si une ou plusieurs dimensions de cet `ICorDebugArrayValue` objet ont un index de base différent de zéro ; Sinon, la valeur booléenne est `false`.</span><span class="sxs-lookup"><span data-stu-id="1f040-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f040-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1f040-107">Requirements</span></span>  
 <span data-ttu-id="1f040-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f040-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f040-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f040-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f040-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f040-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f040-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f040-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
