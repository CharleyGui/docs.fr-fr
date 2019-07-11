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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1afb87e063a18bd05bedf856f8b7ebdf0e47e91
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767419"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="ff982-102">ICorDebugProcess5::GetArrayLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="ff982-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="ff982-103">Fournit des informations sur la disposition de types de tableau.</span><span class="sxs-lookup"><span data-stu-id="ff982-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff982-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff982-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff982-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ff982-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="ff982-106">[in] Un [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) jeton qui spécifie le tableau dont la disposition est souhaitée.</span><span class="sxs-lookup"><span data-stu-id="ff982-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="ff982-107">[out] Un pointeur vers un [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure qui contient des informations sur la mise en page du tableau dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="ff982-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff982-108">Notes</span><span class="sxs-lookup"><span data-stu-id="ff982-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff982-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ff982-109">Requirements</span></span>  
 <span data-ttu-id="ff982-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff982-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff982-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff982-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff982-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff982-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff982-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff982-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff982-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff982-114">See also</span></span>

- [<span data-ttu-id="ff982-115">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="ff982-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="ff982-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ff982-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
