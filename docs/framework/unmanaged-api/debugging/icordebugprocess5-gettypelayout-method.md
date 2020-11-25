---
title: ICorDebugProcess5::GetTypeLayout, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
ms.openlocfilehash: 32277e8adcd4bb08c8d0480eb3b4e7e4b5949479
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723127"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="21b0d-102">ICorDebugProcess5::GetTypeLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="21b0d-102">ICorDebugProcess5::GetTypeLayout Method</span></span>

<span data-ttu-id="21b0d-103">Obtient des informations sur la disposition d’un objet en mémoire en fonction de son identificateur de type.</span><span class="sxs-lookup"><span data-stu-id="21b0d-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21b0d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21b0d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21b0d-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="21b0d-106">dans Jeton [COR_TYPEID](cor-typeid-structure.md) qui spécifie le type dont la disposition est souhaitée.</span><span class="sxs-lookup"><span data-stu-id="21b0d-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="21b0d-107">à Pointeur vers une structure [COR_TYPE_LAYOUT](cor-type-layout-structure.md) qui contient des informations sur la disposition de l’objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="21b0d-107">[out] A pointer to a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21b0d-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="21b0d-108">Remarks</span></span>  

 <span data-ttu-id="21b0d-109">La `ICorDebugProcess5::GetTypeLayout` méthode fournit des informations à propos d’un objet en fonction de son [COR_TYPEID](cor-typeid-structure.md), qui est retourné par un certain nombre d’autres méthodes [ICorDebugProcess5](icordebugprocess5-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="21b0d-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="21b0d-110">Les informations sont fournies par une structure [COR_TYPE_LAYOUT](cor-type-layout-structure.md) qui est remplie par la méthode.</span><span class="sxs-lookup"><span data-stu-id="21b0d-110">The information is provided by a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21b0d-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="21b0d-111">Requirements</span></span>  

 <span data-ttu-id="21b0d-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21b0d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21b0d-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21b0d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21b0d-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21b0d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21b0d-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21b0d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b0d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21b0d-116">See also</span></span>

- [<span data-ttu-id="21b0d-117">COR_TYPE_LAYOUT, structure</span><span class="sxs-lookup"><span data-stu-id="21b0d-117">COR_TYPE_LAYOUT Structure</span></span>](cor-type-layout-structure.md)
- [<span data-ttu-id="21b0d-118">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="21b0d-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="21b0d-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="21b0d-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
