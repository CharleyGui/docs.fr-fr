---
title: ICorDebugProcess6::GetCode, méthode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d896cc4316c2de6fa1cb0bacc9ff8b1f3713129
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967557"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="eb09d-102">ICorDebugProcess6::GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="eb09d-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="eb09d-103">Obtient des informations sur le code managé à une adresse de code particulière.</span><span class="sxs-lookup"><span data-stu-id="eb09d-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb09d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb09d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb09d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eb09d-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="eb09d-106">dans Valeur [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) qui spécifie l’adresse de départ du segment de code managé.</span><span class="sxs-lookup"><span data-stu-id="eb09d-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="eb09d-107">à Pointeur vers l’adresse d’un objet «ICorDebugCode» qui représente un segment de code managé.</span><span class="sxs-lookup"><span data-stu-id="eb09d-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb09d-108">Notes</span><span class="sxs-lookup"><span data-stu-id="eb09d-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb09d-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="eb09d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb09d-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eb09d-110">Requirements</span></span>  
 <span data-ttu-id="eb09d-111">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb09d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb09d-112">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eb09d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb09d-113">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb09d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb09d-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb09d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb09d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb09d-115">See also</span></span>

- [<span data-ttu-id="eb09d-116">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="eb09d-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="eb09d-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="eb09d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
