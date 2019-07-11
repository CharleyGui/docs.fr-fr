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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96e63d121bb64fd1aa6433881f7806b5c4058115
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773997"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="6bdcf-102">ICorDebugValue3::GetSize64, méthode</span><span class="sxs-lookup"><span data-stu-id="6bdcf-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="6bdcf-103">Obtient la taille, en octets, de ce [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="6bdcf-103">Gets the size, in bytes, of this [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bdcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bdcf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bdcf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6bdcf-105">Parameters</span></span>  
 <span data-ttu-id="6bdcf-106">pSize</span><span class="sxs-lookup"><span data-stu-id="6bdcf-106">pSize</span></span>  
 <span data-ttu-id="6bdcf-107">[out] Pointeur vers la taille, en octets, de cet objet.</span><span class="sxs-lookup"><span data-stu-id="6bdcf-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bdcf-108">Notes</span><span class="sxs-lookup"><span data-stu-id="6bdcf-108">Remarks</span></span>  
 <span data-ttu-id="6bdcf-109">Si le type de cette valeur est un type référence, cette méthode retourne la taille du pointeur plutôt que la taille de l’objet.</span><span class="sxs-lookup"><span data-stu-id="6bdcf-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="6bdcf-110">Le `ICorDebugValue3::GetSize` méthode diffère de la [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) méthode dans le type de son paramètre de sortie.</span><span class="sxs-lookup"><span data-stu-id="6bdcf-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="6bdcf-111">Dans [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), le paramètre de sortie est un `ULONG32`; dans `ICorDebugValue3::GetSize`, il est un `ULONG64`.</span><span class="sxs-lookup"><span data-stu-id="6bdcf-111">In [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="6bdcf-112">Cela permet la [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface pour signaler la taille des tableaux qui dépassent 2 Go.</span><span class="sxs-lookup"><span data-stu-id="6bdcf-112">This enables the [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bdcf-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6bdcf-113">Requirements</span></span>  
 <span data-ttu-id="6bdcf-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bdcf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bdcf-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bdcf-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bdcf-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bdcf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bdcf-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bdcf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bdcf-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bdcf-118">See also</span></span>

- [<span data-ttu-id="6bdcf-119">ICorDebugValue3, interface</span><span class="sxs-lookup"><span data-stu-id="6bdcf-119">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="6bdcf-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6bdcf-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
