---
title: ICorDebugProcess5::GetTypeID, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess5.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type:
- apiref
ms.openlocfilehash: 6c159780b9019127d166e8437ea4ed214284011f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121265"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="f6f70-102">ICorDebugProcess5::GetTypeID, méthode</span><span class="sxs-lookup"><span data-stu-id="f6f70-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="f6f70-103">Convertit une adresse d’objet en un identificateur [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f6f70-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6f70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6f70-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6f70-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f6f70-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="f6f70-106">dans Adresse de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f6f70-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="f6f70-107">Pointeur vers la valeur [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) qui identifie l’objet.</span><span class="sxs-lookup"><span data-stu-id="f6f70-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6f70-108">Notes</span><span class="sxs-lookup"><span data-stu-id="f6f70-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6f70-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="f6f70-109">Requirements</span></span>  
 <span data-ttu-id="f6f70-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6f70-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6f70-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6f70-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6f70-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6f70-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6f70-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6f70-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f70-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6f70-114">See also</span></span>

- [<span data-ttu-id="f6f70-115">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="f6f70-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="f6f70-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f6f70-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
