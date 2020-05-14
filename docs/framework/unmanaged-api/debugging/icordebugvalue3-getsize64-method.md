---
title: ICorDebugValue3::GetSize64, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
ms.openlocfilehash: 6eb26de83a6cdce47477e6cb3dffd6a94d889975
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397023"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="0bd77-102">ICorDebugValue3::GetSize64, méthode</span><span class="sxs-lookup"><span data-stu-id="0bd77-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="0bd77-103">Obtient la taille, en octets, de cet objet [icordebugvalue3,](icordebugvalue3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0bd77-103">Gets the size, in bytes, of this [ICorDebugValue3](icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd77-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bd77-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bd77-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0bd77-105">Parameters</span></span>  
 <span data-ttu-id="0bd77-106">pSize</span><span class="sxs-lookup"><span data-stu-id="0bd77-106">pSize</span></span>  
 <span data-ttu-id="0bd77-107">à Pointeur vers la taille, en octets, de cet objet.</span><span class="sxs-lookup"><span data-stu-id="0bd77-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bd77-108">Notes</span><span class="sxs-lookup"><span data-stu-id="0bd77-108">Remarks</span></span>  
 <span data-ttu-id="0bd77-109">Si le type de cette valeur est un type référence, cette méthode retourne la taille du pointeur plutôt que la taille de l’objet.</span><span class="sxs-lookup"><span data-stu-id="0bd77-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="0bd77-110">La `ICorDebugValue3::GetSize` méthode diffère de la méthode [ICorDebugValue ::](icordebugvalue-getsize-method.md) Quantity dans le type de son paramètre de sortie.</span><span class="sxs-lookup"><span data-stu-id="0bd77-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="0bd77-111">Dans [ICorDebugValue ::](icordebugvalue-getsize-method.md)dela, le paramètre de sortie est un `ULONG32` ; dans `ICorDebugValue3::GetSize` , il s’agit d’un `ULONG64` .</span><span class="sxs-lookup"><span data-stu-id="0bd77-111">In [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="0bd77-112">Cela permet à l’interface [icordebugvalue3,](icordebugvalue3-interface.md) de signaler la taille des tableaux qui dépassent 2 Go.</span><span class="sxs-lookup"><span data-stu-id="0bd77-112">This enables the [ICorDebugValue3](icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd77-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0bd77-113">Requirements</span></span>  
 <span data-ttu-id="0bd77-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bd77-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bd77-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bd77-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bd77-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bd77-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bd77-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bd77-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd77-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bd77-118">See also</span></span>

- [<span data-ttu-id="0bd77-119">ICorDebugValue3, interface</span><span class="sxs-lookup"><span data-stu-id="0bd77-119">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="0bd77-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0bd77-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
