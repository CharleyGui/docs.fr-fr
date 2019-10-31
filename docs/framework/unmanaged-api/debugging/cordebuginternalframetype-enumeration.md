---
title: CorDebugInternalFrameType, énumération
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
ms.openlocfilehash: e76800316885c27c697421d454341d5f0789c611
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097950"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="33023-102">CorDebugInternalFrameType, énumération</span><span class="sxs-lookup"><span data-stu-id="33023-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="33023-103">Identifie le type de frame de pile.</span><span class="sxs-lookup"><span data-stu-id="33023-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="33023-104">Cette énumération est utilisée par la méthode [ICorDebugInternalFrame :: GetFrameType,](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="33023-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33023-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33023-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="33023-106">Membres</span><span class="sxs-lookup"><span data-stu-id="33023-106">Members</span></span>  
  
|<span data-ttu-id="33023-107">Membre</span><span class="sxs-lookup"><span data-stu-id="33023-107">Member</span></span>|<span data-ttu-id="33023-108">Description</span><span class="sxs-lookup"><span data-stu-id="33023-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="33023-109">Valeur null.</span><span class="sxs-lookup"><span data-stu-id="33023-109">A null value.</span></span> <span data-ttu-id="33023-110">La méthode `ICorDebugInternalFrame::GetFrameType` ne retourne jamais cette valeur.</span><span class="sxs-lookup"><span data-stu-id="33023-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="33023-111">Frame stub managé vers non managé.</span><span class="sxs-lookup"><span data-stu-id="33023-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="33023-112">Frame stub non managé vers managé.</span><span class="sxs-lookup"><span data-stu-id="33023-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="33023-113">Transition entre des domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="33023-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="33023-114">Appel de méthode allégé.</span><span class="sxs-lookup"><span data-stu-id="33023-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="33023-115">Début de l’évaluation de la fonction.</span><span class="sxs-lookup"><span data-stu-id="33023-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="33023-116">Appel interne dans le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="33023-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="33023-117">Début d’une initialisation de classe.</span><span class="sxs-lookup"><span data-stu-id="33023-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="33023-118">Exception levée.</span><span class="sxs-lookup"><span data-stu-id="33023-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="33023-119">Frame utilisé pour la sécurité d’accès du code.</span><span class="sxs-lookup"><span data-stu-id="33023-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="33023-120">Le runtime fait la compilation juste-à-temps d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="33023-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33023-121">spécifications</span><span class="sxs-lookup"><span data-stu-id="33023-121">Requirements</span></span>  
 <span data-ttu-id="33023-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33023-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33023-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33023-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33023-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33023-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33023-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33023-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33023-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33023-126">See also</span></span>

- [<span data-ttu-id="33023-127">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="33023-127">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
