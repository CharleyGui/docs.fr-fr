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
ms.openlocfilehash: 3252e3b33da743c0e146e25f798c0e669aeb74ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718603"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="d1283-102">COR_PRF_CODEGEN_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="d1283-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>

<span data-ttu-id="d1283-103">Définit les indicateurs de génération de code qui peuvent être définis avec la méthode [ICorProfilerFunctionControl :: setcodegenflags,](icorprofilerfunctioncontrol-setcodegenflags-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d1283-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1283-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1283-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="d1283-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d1283-105">Members</span></span>  
  
|<span data-ttu-id="d1283-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d1283-106">Member</span></span>|<span data-ttu-id="d1283-107">Description</span><span class="sxs-lookup"><span data-stu-id="d1283-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="d1283-108">Aucune fonction n’est insérée dans le corps de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="d1283-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="d1283-109">Toutefois, la fonction elle-même peut être inline dans ses appelants.</span><span class="sxs-lookup"><span data-stu-id="d1283-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="d1283-110">Toutes les optimisations sont désactivées pour le corps de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="d1283-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="d1283-111">Toutefois, la fonction elle-même peut toujours être inline dans ses appelants.</span><span class="sxs-lookup"><span data-stu-id="d1283-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1283-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="d1283-112">Remarks</span></span>  

 <span data-ttu-id="d1283-113">L' `COR_PRF_CODEGEN_FLAGS` énumération est utilisée par la méthode [ICorProfilerFunctionControl :: setcodegenflags,](icorprofilerfunctioncontrol-setcodegenflags-method.md) pour permettre au profileur de contrôler la génération de code pour la fonction recompilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="d1283-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1283-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d1283-114">Requirements</span></span>  

 <span data-ttu-id="d1283-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1283-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1283-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1283-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1283-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1283-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1283-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1283-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1283-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1283-119">See also</span></span>

- [<span data-ttu-id="d1283-120">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="d1283-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
