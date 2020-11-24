---
title: ICorDebugProcess5::GetArrayLayout, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
ms.openlocfilehash: 8b7fab5fc5a02f8e43dc5f6fe8fc98087859ee3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671107"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="1a0ed-102">ICorDebugProcess5::GetArrayLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="1a0ed-102">ICorDebugProcess5::GetArrayLayout Method</span></span>

<span data-ttu-id="1a0ed-103">Fournit des informations sur la disposition des types tableau.</span><span class="sxs-lookup"><span data-stu-id="1a0ed-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a0ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a0ed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a0ed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a0ed-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="1a0ed-106">dans Jeton [COR_TYPEID](cor-typeid-structure.md) qui spécifie le tableau dont la disposition est souhaitée.</span><span class="sxs-lookup"><span data-stu-id="1a0ed-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="1a0ed-107">à Pointeur vers une structure [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) qui contient des informations sur la disposition du tableau en mémoire.</span><span class="sxs-lookup"><span data-stu-id="1a0ed-107">[out] A pointer to a [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a0ed-108">Notes</span><span class="sxs-lookup"><span data-stu-id="1a0ed-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a0ed-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1a0ed-109">Requirements</span></span>  

 <span data-ttu-id="1a0ed-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a0ed-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a0ed-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a0ed-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a0ed-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a0ed-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a0ed-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a0ed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a0ed-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a0ed-114">See also</span></span>

- [<span data-ttu-id="1a0ed-115">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="1a0ed-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="1a0ed-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1a0ed-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
