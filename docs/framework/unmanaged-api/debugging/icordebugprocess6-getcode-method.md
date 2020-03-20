---
title: ICorDebugProcess6::GetCode, méthode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: 94882c67752705f9f13b858ae3b386a19dc103a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178556"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="c901b-102">ICorDebugProcess6::GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="c901b-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="c901b-103">Obtient des informations sur le code managé à une adresse de code particulière.</span><span class="sxs-lookup"><span data-stu-id="c901b-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c901b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c901b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c901b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c901b-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="c901b-106">[dans] Une [valeur CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) qui spécifie l’adresse de départ du segment de code géré.</span><span class="sxs-lookup"><span data-stu-id="c901b-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="c901b-107">[out] Un pointeur à l’adresse d’un objet "ICorDebugCode" qui représente un segment de code géré.</span><span class="sxs-lookup"><span data-stu-id="c901b-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c901b-108">Notes </span><span class="sxs-lookup"><span data-stu-id="c901b-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c901b-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c901b-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c901b-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c901b-110">Requirements</span></span>  
 <span data-ttu-id="c901b-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c901b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c901b-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c901b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c901b-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c901b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c901b-114">**.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c901b-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c901b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c901b-115">See also</span></span>

- [<span data-ttu-id="c901b-116">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="c901b-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="c901b-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c901b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
