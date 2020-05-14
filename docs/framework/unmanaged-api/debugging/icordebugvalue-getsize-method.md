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
ms.openlocfilehash: 9ff7128f55236ae4d0c3a9067a279c496cfb6798
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396749"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="9261a-102">ICorDebugValue::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="9261a-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="9261a-103">Obtient la taille, en octets, de cet objet « ICorDebugValue ».</span><span class="sxs-lookup"><span data-stu-id="9261a-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9261a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9261a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9261a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9261a-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="9261a-106">à Taille, en octets, de cet objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="9261a-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9261a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="9261a-107">Remarks</span></span>  
 <span data-ttu-id="9261a-108">Si le type de la valeur est un type référence, cette méthode retourne la taille du pointeur plutôt que la taille de l’objet.</span><span class="sxs-lookup"><span data-stu-id="9261a-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="9261a-109">La `ICorDebugValue::GetSize` méthode retourne `COR_E_OVERFLOW` pour les objets dont la taille est supérieure à 4 Go sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="9261a-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="9261a-110">Utilisez plutôt la méthode [icordebugvalue3, :: getsize64,](icordebugvalue3-getsize64-method.md) pour les objets dont la taille est supérieure à 4 Go.</span><span class="sxs-lookup"><span data-stu-id="9261a-110">Use the [ICorDebugValue3::GetSize64](icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9261a-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9261a-111">Requirements</span></span>  
 <span data-ttu-id="9261a-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9261a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9261a-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9261a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9261a-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9261a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9261a-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9261a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9261a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9261a-116">See also</span></span>

- [<span data-ttu-id="9261a-117">GetSize64, méthode</span><span class="sxs-lookup"><span data-stu-id="9261a-117">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)
