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
ms.openlocfilehash: e77344a99189ec8e234129262d45698c794dc249
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788512"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="ef71f-102">ICorDebugILFrame4::GetCodeEx, méthode</span><span class="sxs-lookup"><span data-stu-id="ef71f-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="ef71f-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="ef71f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ef71f-104">Obtient un pointeur vers le code exécuté par ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="ef71f-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef71f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef71f-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef71f-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="ef71f-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="ef71f-107">dans Membre de l’énumération [ILCodeKind](ilcodekind-enumeration.md) qui spécifie si le langage intermédiaire (il) défini par la demande ReJIT du profileur est inclus dans le frame.</span><span class="sxs-lookup"><span data-stu-id="ef71f-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="ef71f-108">à Pointeur vers l’adresse d’un objet « ICorDebugCode » qui représente le code exécuté par ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="ef71f-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef71f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="ef71f-109">Remarks</span></span>  
 <span data-ttu-id="ef71f-110">Cette méthode est similaire à la méthode [ICorDebugFrame :: GetCode](icordebugframe-getcode-method.md) , à ceci près qu’elle accède éventuellement au code défini par la requête ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="ef71f-110">This method is similar to the [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="ef71f-111">L’appel de cette méthode avec une valeur `flags` de `ILCODE_ORIGINAL_IL` équivaut à appeler [GetCode](icordebugframe-getcode-method.md); Si la méthode est instrumentée, son IL n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="ef71f-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="ef71f-112">`ILCODE_REJIT_IL` permet au débogueur d'accéder au langage intermédiaire défini par la demande ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="ef71f-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="ef71f-113">Si le langage intermédiaire n’est pas instrumenté, `ppCode` a la **valeur null**et la méthode retourne `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="ef71f-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef71f-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ef71f-114">Requirements</span></span>  
 <span data-ttu-id="ef71f-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef71f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef71f-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef71f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef71f-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef71f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef71f-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef71f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef71f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef71f-119">See also</span></span>

- [<span data-ttu-id="ef71f-120">ICorDebugILFrame4, interface</span><span class="sxs-lookup"><span data-stu-id="ef71f-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="ef71f-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ef71f-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ef71f-122">ReJIT : Guide pratique</span><span class="sxs-lookup"><span data-stu-id="ef71f-122">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
