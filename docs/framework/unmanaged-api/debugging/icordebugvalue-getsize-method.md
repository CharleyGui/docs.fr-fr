---
title: ICorDebugValue::GetSize, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 3d6caa02333229bcd49f4c6ccf8b93265181a0b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137082"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="110bb-102">ICorDebugValue::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="110bb-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="110bb-103">Obtient la taille, en octets, de cet objet « ICorDebugValue ».</span><span class="sxs-lookup"><span data-stu-id="110bb-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="110bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="110bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="110bb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="110bb-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="110bb-106">à Taille, en octets, de cet objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="110bb-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="110bb-107">Notes</span><span class="sxs-lookup"><span data-stu-id="110bb-107">Remarks</span></span>  
 <span data-ttu-id="110bb-108">Si le type de la valeur est un type référence, cette méthode retourne la taille du pointeur plutôt que la taille de l’objet.</span><span class="sxs-lookup"><span data-stu-id="110bb-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="110bb-109">La méthode `ICorDebugValue::GetSize` retourne `COR_E_OVERFLOW` pour les objets dont la taille est supérieure à 4 Go sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="110bb-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="110bb-110">Utilisez plutôt la méthode [icordebugvalue3, :: getsize64,](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) pour les objets dont la taille est supérieure à 4 Go.</span><span class="sxs-lookup"><span data-stu-id="110bb-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="110bb-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="110bb-111">Requirements</span></span>  
 <span data-ttu-id="110bb-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="110bb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="110bb-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="110bb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="110bb-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="110bb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="110bb-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="110bb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110bb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="110bb-116">See also</span></span>

- [<span data-ttu-id="110bb-117">GetSize64, méthode</span><span class="sxs-lookup"><span data-stu-id="110bb-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
