---
title: ICorDebugILFrame4::GetCodeEx, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: ef2e4bc0caddd6b13c8dbe8edb59e0673519421b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178792"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="50a8b-102">ICorDebugILFrame4::GetCodeEx, méthode</span><span class="sxs-lookup"><span data-stu-id="50a8b-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="50a8b-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="50a8b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="50a8b-104">Obtient un pointeur vers le code exécuté par ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="50a8b-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50a8b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50a8b-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50a8b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="50a8b-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="50a8b-107">[dans] Un membre de l’énumération [ILCodeKind](ilcodekind-enumeration.md) qui précise si le langage intermédiaire (IL) défini par la demande ReJIT du profileur est inclus dans le cadre.</span><span class="sxs-lookup"><span data-stu-id="50a8b-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="50a8b-108">[out] Un pointeur à l’adresse d’un objet "ICorDebugCode" qui représente le code que ce cadre de pile exécute.</span><span class="sxs-lookup"><span data-stu-id="50a8b-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50a8b-109">Notes </span><span class="sxs-lookup"><span data-stu-id="50a8b-109">Remarks</span></span>  
 <span data-ttu-id="50a8b-110">Cette méthode est similaire à la méthode [ICorDebugFrame::GetCode,](icordebugframe-getcode-method.md) sauf qu’elle accède optionnellement au code défini par la demande ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="50a8b-110">This method is similar to the [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="50a8b-111">Appeler cette méthode `flags` avec `ILCODE_ORIGINAL_IL` une valeur de est équivalent à appeler [GetCode](icordebugframe-getcode-method.md); si la méthode est instrumentée, son IL ne sera pas accessible.</span><span class="sxs-lookup"><span data-stu-id="50a8b-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="50a8b-112">`ILCODE_REJIT_IL` permet au débogueur d'accéder au langage intermédiaire défini par la demande ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="50a8b-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="50a8b-113">Si l’IL n’est pas `ppCode` instrumenté, `S_OK`est **nul,** et la méthode revient .</span><span class="sxs-lookup"><span data-stu-id="50a8b-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50a8b-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="50a8b-114">Requirements</span></span>  
 <span data-ttu-id="50a8b-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50a8b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50a8b-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50a8b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50a8b-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50a8b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50a8b-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50a8b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a8b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50a8b-119">See also</span></span>

- [<span data-ttu-id="50a8b-120">ICorDebugILFrame4, interface</span><span class="sxs-lookup"><span data-stu-id="50a8b-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="50a8b-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="50a8b-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="50a8b-122">ReJIT: Un guide de comment se passer</span><span class="sxs-lookup"><span data-stu-id="50a8b-122">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
