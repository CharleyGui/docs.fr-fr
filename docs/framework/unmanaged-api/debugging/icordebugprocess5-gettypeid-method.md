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
ms.openlocfilehash: 3a9ef06f312126319875544caf272903b9f7c716
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701027"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="3e2d3-102">ICorDebugProcess5::GetTypeID, méthode</span><span class="sxs-lookup"><span data-stu-id="3e2d3-102">ICorDebugProcess5::GetTypeID Method</span></span>

<span data-ttu-id="3e2d3-103">Convertit une adresse d’objet en un identificateur de [COR_TYPEID](cor-typeid-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="3e2d3-103">Converts an object address to a [COR_TYPEID](cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e2d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e2d3-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e2d3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e2d3-105">Parameters</span></span>  

 `obj`  
 <span data-ttu-id="3e2d3-106">dans Adresse de l’objet.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="3e2d3-107">Pointeur vers la valeur [COR_TYPEID](cor-typeid-structure.md) qui identifie l’objet.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-107">A pointer to the [COR_TYPEID](cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e2d3-108">Notes</span><span class="sxs-lookup"><span data-stu-id="3e2d3-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e2d3-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3e2d3-109">Requirements</span></span>  

 <span data-ttu-id="3e2d3-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e2d3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e2d3-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e2d3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e2d3-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e2d3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e2d3-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e2d3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e2d3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e2d3-114">See also</span></span>

- [<span data-ttu-id="3e2d3-115">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="3e2d3-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="3e2d3-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3e2d3-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
