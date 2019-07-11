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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94d8fbf4d93bbfbaaeb7c1268004aada22b9b7df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768914"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="e3dbf-102">ICorDebugValue::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="e3dbf-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="e3dbf-103">Obtient la taille, en octets, de cet objet « ICorDebugValue ».</span><span class="sxs-lookup"><span data-stu-id="e3dbf-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3dbf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3dbf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3dbf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e3dbf-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="e3dbf-106">[out] La taille, en octets, de cet objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="e3dbf-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3dbf-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e3dbf-107">Remarks</span></span>  
 <span data-ttu-id="e3dbf-108">Si le type de valeur est un type référence, cette méthode retourne la taille du pointeur plutôt que la taille de l’objet.</span><span class="sxs-lookup"><span data-stu-id="e3dbf-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="e3dbf-109">Le `ICorDebugValue::GetSize` retourne de la méthode `COR_E_OVERFLOW` pour les objets qui sont supérieurs à 4 Go sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e3dbf-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="e3dbf-110">Utilisez le [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) méthode à la place pour les objets qui sont supérieurs à 4 Go.</span><span class="sxs-lookup"><span data-stu-id="e3dbf-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3dbf-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e3dbf-111">Requirements</span></span>  
 <span data-ttu-id="e3dbf-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3dbf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3dbf-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3dbf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3dbf-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3dbf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3dbf-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3dbf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3dbf-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3dbf-116">See also</span></span>

- [<span data-ttu-id="e3dbf-117">GetSize64, méthode</span><span class="sxs-lookup"><span data-stu-id="e3dbf-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
