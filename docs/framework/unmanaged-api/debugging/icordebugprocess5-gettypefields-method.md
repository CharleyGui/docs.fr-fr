---
title: ICorDebugProcess5::GetTypeFields, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
ms.openlocfilehash: 0045285a3da22f468c2426bb3b9c4ae7e3e1d7c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132668"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="b5791-102">ICorDebugProcess5::GetTypeFields, méthode</span><span class="sxs-lookup"><span data-stu-id="b5791-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="b5791-103">Fournit des informations sur les champs qui appartiennent à un type.</span><span class="sxs-lookup"><span data-stu-id="b5791-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5791-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5791-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5791-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b5791-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="b5791-106">dans Identificateur du type dont les informations de champ sont récupérées.</span><span class="sxs-lookup"><span data-stu-id="b5791-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="b5791-107">dans Nombre d’objets [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) dont les informations de champ doivent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="b5791-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="b5791-108">à Tableau d’objets [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) qui fournissent des informations sur les champs qui appartiennent au type.</span><span class="sxs-lookup"><span data-stu-id="b5791-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="b5791-109">à Pointeur vers le nombre d’objets [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) inclus dans `fields`.</span><span class="sxs-lookup"><span data-stu-id="b5791-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5791-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b5791-110">Remarks</span></span>  
 <span data-ttu-id="b5791-111">Le paramètre `celt`, qui spécifie le nombre de champs dont la méthode utilise les informations de champ pour remplir `fields`, doit correspondre à la valeur du champ `COR_TYPE_LAYOUT::numFields`.</span><span class="sxs-lookup"><span data-stu-id="b5791-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5791-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="b5791-112">Requirements</span></span>  
 <span data-ttu-id="b5791-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5791-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5791-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5791-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5791-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5791-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5791-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5791-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5791-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5791-117">See also</span></span>

- [<span data-ttu-id="b5791-118">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="b5791-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="b5791-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b5791-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
