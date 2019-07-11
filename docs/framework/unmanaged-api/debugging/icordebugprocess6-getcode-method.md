---
title: ICorDebugProcess6::GetCode, méthode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 810590f0d1f7f74b778d73d98a9f7f9b1988b75f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736443"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="d2112-102">ICorDebugProcess6::GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="d2112-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="d2112-103">Obtient des informations sur le code managé à une adresse de code particulière.</span><span class="sxs-lookup"><span data-stu-id="d2112-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2112-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2112-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2112-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d2112-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="d2112-106">[in] Un [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valeur qui spécifie l’adresse de départ du segment de code managé.</span><span class="sxs-lookup"><span data-stu-id="d2112-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="d2112-107">[out] Pointeur vers l’adresse d’un objet « ICorDebugCode » qui représente un segment de code managé.</span><span class="sxs-lookup"><span data-stu-id="d2112-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2112-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d2112-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2112-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d2112-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2112-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d2112-110">Requirements</span></span>  
 <span data-ttu-id="d2112-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2112-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2112-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2112-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2112-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2112-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2112-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2112-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2112-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2112-115">See also</span></span>

- [<span data-ttu-id="d2112-116">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="d2112-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="d2112-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d2112-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
