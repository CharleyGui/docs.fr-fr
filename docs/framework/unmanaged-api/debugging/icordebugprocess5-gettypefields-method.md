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
ms.openlocfilehash: 29006eba3d3a523fd24a461207ab12222a639782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178587"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="13a17-102">ICorDebugProcess5::GetTypeFields, méthode</span><span class="sxs-lookup"><span data-stu-id="13a17-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="13a17-103">Fournit des informations sur les champs qui appartiennent à un type.</span><span class="sxs-lookup"><span data-stu-id="13a17-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13a17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13a17-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="13a17-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="13a17-106">[dans] L’identifiant du type dont les informations sur le terrain sont récupérées.</span><span class="sxs-lookup"><span data-stu-id="13a17-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="13a17-107">[dans] Nombre d’objets [COR_FIELD](cor-field-structure.md) dont les informations sur le terrain doivent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="13a17-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="13a17-108">[out] Un éventail d’objets [COR_FIELD](cor-field-structure.md) qui fournissent des informations sur les champs qui appartiennent au type.</span><span class="sxs-lookup"><span data-stu-id="13a17-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="13a17-109">[out] Un pointeur sur le nombre d’objets [COR_FIELD](cor-field-structure.md) inclus dans `fields`.</span><span class="sxs-lookup"><span data-stu-id="13a17-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13a17-110">Notes </span><span class="sxs-lookup"><span data-stu-id="13a17-110">Remarks</span></span>  
 <span data-ttu-id="13a17-111">Le `celt` paramètre, qui précise le nombre de champs dont `fields`l’information sur le `COR_TYPE_LAYOUT::numFields` terrain utilisée par la méthode pour peupler, doit correspondre à la valeur du champ.</span><span class="sxs-lookup"><span data-stu-id="13a17-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13a17-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="13a17-112">Requirements</span></span>  
 <span data-ttu-id="13a17-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a17-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a17-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13a17-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13a17-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13a17-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13a17-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13a17-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a17-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13a17-117">See also</span></span>

- [<span data-ttu-id="13a17-118">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="13a17-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="13a17-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="13a17-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
