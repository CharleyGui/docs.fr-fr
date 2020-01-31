---
title: COR_PRF_CODEGEN_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
ms.openlocfilehash: 4dd4e39c9092d018f13e3bd2822e9492d71141ad
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867293"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="60ffb-102">COR_PRF_CODEGEN_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="60ffb-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="60ffb-103">Définit les indicateurs de génération de code qui peuvent être définis avec la méthode [ICorProfilerFunctionControl :: setcodegenflags,](icorprofilerfunctioncontrol-setcodegenflags-method.md) .</span><span class="sxs-lookup"><span data-stu-id="60ffb-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ffb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60ffb-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="60ffb-105">Members</span><span class="sxs-lookup"><span data-stu-id="60ffb-105">Members</span></span>  
  
|<span data-ttu-id="60ffb-106">Member</span><span class="sxs-lookup"><span data-stu-id="60ffb-106">Member</span></span>|<span data-ttu-id="60ffb-107">Description</span><span class="sxs-lookup"><span data-stu-id="60ffb-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="60ffb-108">Aucune fonction n’est insérée dans le corps de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="60ffb-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="60ffb-109">Toutefois, la fonction elle-même peut être inline dans ses appelants.</span><span class="sxs-lookup"><span data-stu-id="60ffb-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="60ffb-110">Toutes les optimisations sont désactivées pour le corps de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="60ffb-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="60ffb-111">Toutefois, la fonction elle-même peut toujours être inline dans ses appelants.</span><span class="sxs-lookup"><span data-stu-id="60ffb-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60ffb-112">Notes</span><span class="sxs-lookup"><span data-stu-id="60ffb-112">Remarks</span></span>  
 <span data-ttu-id="60ffb-113">L’énumération `COR_PRF_CODEGEN_FLAGS` est utilisée par la méthode [ICorProfilerFunctionControl :: setcodegenflags,](icorprofilerfunctioncontrol-setcodegenflags-method.md) pour permettre au profileur de contrôler la génération de code pour la fonction recompilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="60ffb-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60ffb-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="60ffb-114">Requirements</span></span>  
 <span data-ttu-id="60ffb-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60ffb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60ffb-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60ffb-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60ffb-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60ffb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60ffb-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60ffb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ffb-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60ffb-119">See also</span></span>

- [<span data-ttu-id="60ffb-120">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="60ffb-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
