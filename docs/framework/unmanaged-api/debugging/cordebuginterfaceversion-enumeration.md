---
title: CorDebugInterfaceVersion, énumération
ms.date: 03/30/2017
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
ms.openlocfilehash: ae65c60440a90959006cd8db94dda479e80613d4
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795805"
---
# <a name="cordebuginterfaceversion-enumeration"></a><span data-ttu-id="dbcfb-102">CorDebugInterfaceVersion, énumération</span><span class="sxs-lookup"><span data-stu-id="dbcfb-102">CorDebugInterfaceVersion Enumeration</span></span>
<span data-ttu-id="dbcfb-103">Spécifie une interface, une version de .NET Framework ou une version de .NET Framework où une interface a été introduite.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-103">Specifies an interface, a version of the .NET Framework, or a version of the .NET Framework in which an interface was introduced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbcfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbcfb-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a><span data-ttu-id="dbcfb-105">Membres</span><span class="sxs-lookup"><span data-stu-id="dbcfb-105">Members</span></span>  
 <span data-ttu-id="dbcfb-106">Le tableau suivant fournit des liens de chaque valeur de l'énumération vers l'interface correspondante.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-106">The following table provides links from each enumeration value to the corresponding interface.</span></span> <span data-ttu-id="dbcfb-107">En outre, le tableau indique la première version de .NET Framework qui a pris en charge l'interface.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-107">In addition, the table indicates the first version of the .NET Framework that the interface was supported in.</span></span>  
  
|<span data-ttu-id="dbcfb-108">Membre</span><span class="sxs-lookup"><span data-stu-id="dbcfb-108">Member</span></span>|<span data-ttu-id="dbcfb-109">Spécifie</span><span class="sxs-lookup"><span data-stu-id="dbcfb-109">Specifies</span></span>|<span data-ttu-id="dbcfb-110">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dbcfb-110">.NET Framework version</span></span>|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|<span data-ttu-id="dbcfb-111">La version de .NET Framework est non valide.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-111">The version of the .NET Framework is invalid.</span></span>|-|  
|`CorDebugVersion_1_0`|<span data-ttu-id="dbcfb-112">La version de .NET Framework, y compris tous ses Service Packs, est 1.0.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-112">The version of the .NET Framework, including all its service packs, is 1.0.</span></span>|<span data-ttu-id="dbcfb-113">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-113">1.0</span></span>|  
|`CorDebugVersion_1_1`|<span data-ttu-id="dbcfb-114">La version de .NET Framework, y compris tous les Service Packs, est 1.1.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-114">The version of the .NET Framework, including all service packs, is 1.1.</span></span>|<span data-ttu-id="dbcfb-115">1.1</span><span class="sxs-lookup"><span data-stu-id="dbcfb-115">1.1</span></span>|  
|`CorDebugVersion_2_0`|<span data-ttu-id="dbcfb-116">La version de .NET Framework, y compris tous les Service Packs, est 2.0.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-116">The version of the .NET Framework, including all service packs, is 2.0.</span></span>|<span data-ttu-id="dbcfb-117">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-117">2.0</span></span>|  
|`CorDebugVersion_4_0`|<span data-ttu-id="dbcfb-118">La version de .NET Framework, y compris tous les Service Packs, est 4.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-118">The version of the .NET Framework, including all service packs, is 4.</span></span>|<span data-ttu-id="dbcfb-119">4</span><span class="sxs-lookup"><span data-stu-id="dbcfb-119">4</span></span>|  
|`CorDebugVersion_4_5`|<span data-ttu-id="dbcfb-120">La version de .NET Framework, y compris tous les Service Packs, est 4.5.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-120">The version of the .NET Framework, including all service packs, is 4.5.</span></span>|<span data-ttu-id="dbcfb-121">4.5</span><span class="sxs-lookup"><span data-stu-id="dbcfb-121">4.5</span></span>|  
|`ver_ICorDebugManagedCallback`|[<span data-ttu-id="dbcfb-122">ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="dbcfb-122">ICorDebugManagedCallback</span></span>](icordebugmanagedcallback-interface.md)|<span data-ttu-id="dbcfb-123">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-123">1.0</span></span>|  
|`ver_ICorDebugUnmanagedCallback`|[<span data-ttu-id="dbcfb-124">ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="dbcfb-124">ICorDebugUnmanagedCallback</span></span>](icordebugunmanagedcallback-interface.md)|<span data-ttu-id="dbcfb-125">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-125">1.0</span></span>|  
|`ver_ICorDebug`|[<span data-ttu-id="dbcfb-126">ICorDebug</span><span class="sxs-lookup"><span data-stu-id="dbcfb-126">ICorDebug</span></span>](icordebug-interface.md)|<span data-ttu-id="dbcfb-127">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-127">1.0</span></span>|  
|`ver_ICorDebugController`|[<span data-ttu-id="dbcfb-128">ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="dbcfb-128">ICorDebugController</span></span>](icordebugcontroller-interface.md)|<span data-ttu-id="dbcfb-129">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-129">1.0</span></span>|  
|`ver_ICorDebugAppDomain`|[<span data-ttu-id="dbcfb-130">ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="dbcfb-130">ICorDebugAppDomain</span></span>](icordebugappdomain-interface.md)|<span data-ttu-id="dbcfb-131">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-131">1.0</span></span>|  
|`ver_ICorDebugAssembly`|[<span data-ttu-id="dbcfb-132">ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="dbcfb-132">ICorDebugAssembly</span></span>](icordebugassembly-interface.md)|<span data-ttu-id="dbcfb-133">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-133">1.0</span></span>|  
|`ver_ICorDebugProcess`|[<span data-ttu-id="dbcfb-134">ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="dbcfb-134">ICorDebugProcess</span></span>](icordebugprocess-interface.md)|<span data-ttu-id="dbcfb-135">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-135">1.0</span></span>|  
|`ver_ICorDebugBreakpoint`|[<span data-ttu-id="dbcfb-136">ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="dbcfb-136">ICorDebugBreakpoint</span></span>](icordebugbreakpoint-interface.md)|<span data-ttu-id="dbcfb-137">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-137">1.0</span></span>|  
|`ver_ICorDebugFunctionBreakpoint`|[<span data-ttu-id="dbcfb-138">ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="dbcfb-138">ICorDebugFunctionBreakpoint</span></span>](icordebugfunctionbreakpoint-interface.md)|<span data-ttu-id="dbcfb-139">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-139">1.0</span></span>|  
|`ver_ICorDebugModuleBreakpoint`|[<span data-ttu-id="dbcfb-140">ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="dbcfb-140">ICorDebugModuleBreakpoint</span></span>](icordebugmodulebreakpoint-interface.md)|<span data-ttu-id="dbcfb-141">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-141">1.0</span></span>|  
|`ver_ICorDebugValueBreakpoint`|[<span data-ttu-id="dbcfb-142">ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="dbcfb-142">ICorDebugValueBreakpoint</span></span>](icordebugvaluebreakpoint-interface.md)|<span data-ttu-id="dbcfb-143">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-143">1.0</span></span>|  
|`ver_ICorDebugStepper`|[<span data-ttu-id="dbcfb-144">ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="dbcfb-144">ICorDebugStepper</span></span>](icordebugstepper-interface.md)|<span data-ttu-id="dbcfb-145">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-145">1.0</span></span>|  
|`ver_ICorDebugRegisterSet`|[<span data-ttu-id="dbcfb-146">ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="dbcfb-146">ICorDebugRegisterSet</span></span>](icordebugregisterset-interface.md)|<span data-ttu-id="dbcfb-147">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-147">1.0</span></span>|  
|`ver_ICorDebugThread`|[<span data-ttu-id="dbcfb-148">ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="dbcfb-148">ICorDebugThread</span></span>](icordebugthread-interface.md)|<span data-ttu-id="dbcfb-149">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-149">1.0</span></span>|  
|`ver_ICorDebugChain`|[<span data-ttu-id="dbcfb-150">ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="dbcfb-150">ICorDebugChain</span></span>](icordebugchain-interface.md)|<span data-ttu-id="dbcfb-151">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-151">1.0</span></span>|  
|`ver_ICorDebugFrame`|[<span data-ttu-id="dbcfb-152">ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="dbcfb-152">ICorDebugFrame</span></span>](icordebugframe-interface.md)|<span data-ttu-id="dbcfb-153">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-153">1.0</span></span>|  
|`ver_ICorDebugILFrame`|[<span data-ttu-id="dbcfb-154">ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="dbcfb-154">ICorDebugILFrame</span></span>](icordebugilframe-interface.md)|<span data-ttu-id="dbcfb-155">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-155">1.0</span></span>|  
|`ver_ICorDebugNativeFrame`|[<span data-ttu-id="dbcfb-156">ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="dbcfb-156">ICorDebugNativeFrame</span></span>](icordebugnativeframe-interface.md)|<span data-ttu-id="dbcfb-157">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-157">1.0</span></span>|  
|`ver_ICorDebugModule`|[<span data-ttu-id="dbcfb-158">ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="dbcfb-158">ICorDebugModule</span></span>](icordebugmodule-interface.md)|<span data-ttu-id="dbcfb-159">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-159">1.0</span></span>|  
|`ver_ICorDebugFunction`|[<span data-ttu-id="dbcfb-160">ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="dbcfb-160">ICorDebugFunction</span></span>](icordebugfunction-interface1.md)|<span data-ttu-id="dbcfb-161">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-161">1.0</span></span>|  
|`ver_ICorDebugCode`|[<span data-ttu-id="dbcfb-162">ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="dbcfb-162">ICorDebugCode</span></span>](icordebugcode-interface1.md)|<span data-ttu-id="dbcfb-163">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-163">1.0</span></span>|  
|`ver_ICorDebugClass`|[<span data-ttu-id="dbcfb-164">ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="dbcfb-164">ICorDebugClass</span></span>](icordebugclass-interface.md)|<span data-ttu-id="dbcfb-165">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-165">1.0</span></span>|  
|`ver_ICorDebugEval`|[<span data-ttu-id="dbcfb-166">ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="dbcfb-166">ICorDebugEval</span></span>](icordebugeval-interface.md)|<span data-ttu-id="dbcfb-167">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-167">1.0</span></span>|  
|`ver_ICorDebugValue`|[<span data-ttu-id="dbcfb-168">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="dbcfb-168">ICorDebugValue</span></span>](icordebugvalue-interface.md)|<span data-ttu-id="dbcfb-169">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-169">1.0</span></span>|  
|`ver_ICorDebugGenericValue`|[<span data-ttu-id="dbcfb-170">ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="dbcfb-170">ICorDebugGenericValue</span></span>](icordebuggenericvalue-interface.md)|<span data-ttu-id="dbcfb-171">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-171">1.0</span></span>|  
|`ver_ICorDebugReferenceValue`|[<span data-ttu-id="dbcfb-172">ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="dbcfb-172">ICorDebugReferenceValue</span></span>](icordebugreferencevalue-interface.md)|<span data-ttu-id="dbcfb-173">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-173">1.0</span></span>|  
|`ver_ICorDebugHeapValue`|[<span data-ttu-id="dbcfb-174">ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="dbcfb-174">ICorDebugHeapValue</span></span>](icordebugheapvalue-interface.md)|<span data-ttu-id="dbcfb-175">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-175">1.0</span></span>|  
|`ver_ICorDebugObjectValue`|[<span data-ttu-id="dbcfb-176">ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="dbcfb-176">ICorDebugObjectValue</span></span>](icordebugobjectvalue-interface.md)|<span data-ttu-id="dbcfb-177">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-177">1.0</span></span>|  
|`ver_ICorDebugBoxValue`|[<span data-ttu-id="dbcfb-178">ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="dbcfb-178">ICorDebugBoxValue</span></span>](icordebugboxvalue-interface.md)|<span data-ttu-id="dbcfb-179">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-179">1.0</span></span>|  
|`ver_ICorDebugStringValue`|[<span data-ttu-id="dbcfb-180">ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="dbcfb-180">ICorDebugStringValue</span></span>](icordebugstringvalue-interface.md)|<span data-ttu-id="dbcfb-181">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-181">1.0</span></span>|  
|`ver_ICorDebugArrayValue`|[<span data-ttu-id="dbcfb-182">ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="dbcfb-182">ICorDebugArrayValue</span></span>](icordebugarrayvalue-interface.md)|<span data-ttu-id="dbcfb-183">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-183">1.0</span></span>|  
|`ver_ICorDebugContext`|[<span data-ttu-id="dbcfb-184">ICorDebugContext</span><span class="sxs-lookup"><span data-stu-id="dbcfb-184">ICorDebugContext</span></span>](icordebugcontext-interface.md)|<span data-ttu-id="dbcfb-185">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-185">1.0</span></span>|  
|`ver_ICorDebugEnum`|[<span data-ttu-id="dbcfb-186">ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-186">ICorDebugEnum</span></span>](icordebugenum-interface1.md)|<span data-ttu-id="dbcfb-187">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-187">1.0</span></span>|  
|`ver_ICorDebugObjectEnum`|[<span data-ttu-id="dbcfb-188">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-188">ICorDebugObjectEnum</span></span>](icordebugobjectenum-interface.md)|<span data-ttu-id="dbcfb-189">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-189">1.0</span></span>|  
|`ver_ICorDebugBreakpointEnum`|[<span data-ttu-id="dbcfb-190">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-190">ICorDebugBreakpointEnum</span></span>](icordebugbreakpointenum-interface.md)|<span data-ttu-id="dbcfb-191">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-191">1.0</span></span>|  
|`ver_ICorDebugStepperEnum`|[<span data-ttu-id="dbcfb-192">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-192">ICorDebugStepperEnum</span></span>](icordebugstepperenum-interface.md)|<span data-ttu-id="dbcfb-193">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-193">1.0</span></span>|  
|`ver_ICorDebugProcessEnum`|[<span data-ttu-id="dbcfb-194">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-194">ICorDebugProcessEnum</span></span>](icordebugprocessenum-interface.md)|<span data-ttu-id="dbcfb-195">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-195">1.0</span></span>|  
|`ver_ICorDebugThreadEnum`|[<span data-ttu-id="dbcfb-196">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-196">ICorDebugThreadEnum</span></span>](icordebugthreadenum-interface1.md)|<span data-ttu-id="dbcfb-197">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-197">1.0</span></span>|  
|`ver_ICorDebugFrameEnum`|[<span data-ttu-id="dbcfb-198">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-198">ICorDebugFrameEnum</span></span>](icordebugframeenum-interface.md)|<span data-ttu-id="dbcfb-199">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-199">1.0</span></span>|  
|`ver_ICorDebugChainEnum`|[<span data-ttu-id="dbcfb-200">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-200">ICorDebugChainEnum</span></span>](icordebugchainenum-interface.md)|<span data-ttu-id="dbcfb-201">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-201">1.0</span></span>|  
|`ver_ICorDebugModuleEnum`|[<span data-ttu-id="dbcfb-202">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-202">ICorDebugModuleEnum</span></span>](icordebugmoduleenum-interface.md)|<span data-ttu-id="dbcfb-203">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-203">1.0</span></span>|  
|`ver_ICorDebugValueEnum`|[<span data-ttu-id="dbcfb-204">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-204">ICorDebugValueEnum</span></span>](icordebugvalueenum-interface.md)|<span data-ttu-id="dbcfb-205">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-205">1.0</span></span>|  
|`ver_ICorDebugCodeEnum`|[<span data-ttu-id="dbcfb-206">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-206">ICorDebugCodeEnum</span></span>](icordebugcodeenum-interface.md)|<span data-ttu-id="dbcfb-207">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-207">1.0</span></span>|  
|`ver_ICorDebugTypeEnum`|[<span data-ttu-id="dbcfb-208">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-208">ICorDebugTypeEnum</span></span>](icordebugtypeenum-interface.md)|<span data-ttu-id="dbcfb-209">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-209">1.0</span></span>|  
|`ver_ICorDebugErrorInfoEnum`|[<span data-ttu-id="dbcfb-210">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-210">ICorDebugErrorInfoEnum</span></span>](icordebugerrorinfoenum-interface.md)|<span data-ttu-id="dbcfb-211">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-211">1.0</span></span>|  
|`ver_ICorDebugAppDomainEnum`|[<span data-ttu-id="dbcfb-212">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-212">ICorDebugAppDomainEnum</span></span>](icordebugappdomainenum-interface.md)|<span data-ttu-id="dbcfb-213">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-213">1.0</span></span>|  
|`ver_ICorDebugAssemblyEnum`|[<span data-ttu-id="dbcfb-214">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="dbcfb-214">ICorDebugAssemblyEnum</span></span>](icordebugassemblyenum-interface.md)|<span data-ttu-id="dbcfb-215">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-215">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[<span data-ttu-id="dbcfb-216">ICorDebugEditAndContinueErrorInfo</span><span class="sxs-lookup"><span data-stu-id="dbcfb-216">ICorDebugEditAndContinueErrorInfo</span></span>](icordebugeditandcontinueerrorinfo-interface.md)|<span data-ttu-id="dbcfb-217">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-217">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueSnapshot`|[<span data-ttu-id="dbcfb-218">ICorDebugEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="dbcfb-218">ICorDebugEditAndContinueSnapshot</span></span>](icordebugeditandcontinuesnapshot-interface.md)|<span data-ttu-id="dbcfb-219">1.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-219">1.0</span></span>|  
|`ver_ICorDebugManagedCallback2`|[<span data-ttu-id="dbcfb-220">ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-220">ICorDebugManagedCallback2</span></span>](icordebugmanagedcallback2-interface.md)|<span data-ttu-id="dbcfb-221">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-221">2.0</span></span>|  
|`ver_ICorDebugAppDomain2`|[<span data-ttu-id="dbcfb-222">ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-222">ICorDebugAppDomain2</span></span>](icordebugappdomain2-interface.md)|<span data-ttu-id="dbcfb-223">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-223">2.0</span></span>|  
|`ver_ICorDebugProcess2`|[<span data-ttu-id="dbcfb-224">ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-224">ICorDebugProcess2</span></span>](icordebugprocess2-interface1.md)|<span data-ttu-id="dbcfb-225">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-225">2.0</span></span>|  
|`ver_ICorDebugStepper2`|[<span data-ttu-id="dbcfb-226">ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-226">ICorDebugStepper2</span></span>](icordebugstepper2-interface1.md)|<span data-ttu-id="dbcfb-227">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-227">2.0</span></span>|  
|`ver_ICorDebugRegisterSet2`|[<span data-ttu-id="dbcfb-228">ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-228">ICorDebugRegisterSet2</span></span>](icordebugregisterset2-interface.md)|<span data-ttu-id="dbcfb-229">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-229">2.0</span></span>|  
|`ver_ICorDebugThread2`|[<span data-ttu-id="dbcfb-230">ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-230">ICorDebugThread2</span></span>](icordebugthread2-interface.md)|<span data-ttu-id="dbcfb-231">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-231">2.0</span></span>|  
|`ver_ICorDebugILFrame2`|[<span data-ttu-id="dbcfb-232">ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-232">ICorDebugILFrame2</span></span>](icordebugilframe2-interface.md)|<span data-ttu-id="dbcfb-233">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-233">2.0</span></span>|  
|`ver_ICorDebugModule2`|[<span data-ttu-id="dbcfb-234">ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-234">ICorDebugModule2</span></span>](icordebugmodule2-interface.md)|<span data-ttu-id="dbcfb-235">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-235">2.0</span></span>|  
|`ver_ICorDebugFunction2`|[<span data-ttu-id="dbcfb-236">ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-236">ICorDebugFunction2</span></span>](icordebugfunction2-interface.md)|<span data-ttu-id="dbcfb-237">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-237">2.0</span></span>|  
|`ver_ICorDebugCode2`|[<span data-ttu-id="dbcfb-238">ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-238">ICorDebugCode2</span></span>](icordebugcode2-interface.md)|<span data-ttu-id="dbcfb-239">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-239">2.0</span></span>|  
|`ver_ICorDebugClass2`|<span data-ttu-id="dbcfb-240">ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-240">"ICorDebugClass2"</span></span>|<span data-ttu-id="dbcfb-241">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-241">2.0</span></span>|  
|`ver_ICorDebugValue2`|<span data-ttu-id="dbcfb-242">ICorDebugValue2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-242">"ICorDebugValue2"</span></span>|<span data-ttu-id="dbcfb-243">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-243">2.0</span></span>|  
|`ver_ICorDebugEval2`|<span data-ttu-id="dbcfb-244">« ICorDebugEval2 ».</span><span class="sxs-lookup"><span data-stu-id="dbcfb-244">The "ICorDebugEval2".</span></span>|<span data-ttu-id="dbcfb-245">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-245">2.0</span></span>|  
|`ver_ICorDebugObjectValue2`|<span data-ttu-id="dbcfb-246">ICorDebugObjectValue2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-246">"ICorDebugObjectValue2"</span></span>|<span data-ttu-id="dbcfb-247">2.0</span><span class="sxs-lookup"><span data-stu-id="dbcfb-247">2.0</span></span>|  
|`ver_ICorDebugThread3`|[<span data-ttu-id="dbcfb-248">ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="dbcfb-248">ICorDebugThread3</span></span>](icordebugthread3-interface.md)|<span data-ttu-id="dbcfb-249">4</span><span class="sxs-lookup"><span data-stu-id="dbcfb-249">4</span></span>|  
|`ver_ICorDebugThread4`|[<span data-ttu-id="dbcfb-250">ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="dbcfb-250">ICorDebugThread4</span></span>](icordebugthread4-interface.md)|<span data-ttu-id="dbcfb-251">4</span><span class="sxs-lookup"><span data-stu-id="dbcfb-251">4</span></span>|  
|`ver_ICorDebugStackWalk`|[<span data-ttu-id="dbcfb-252">ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="dbcfb-252">ICorDebugStackWalk</span></span>](icordebugstackwalk-interface.md)|<span data-ttu-id="dbcfb-253">4</span><span class="sxs-lookup"><span data-stu-id="dbcfb-253">4</span></span>|  
|`ver_ICorDebugNativeFrame2`|[<span data-ttu-id="dbcfb-254">ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-254">ICorDebugNativeFrame2</span></span>](icordebugnativeframe2-interface.md)|<span data-ttu-id="dbcfb-255">4</span><span class="sxs-lookup"><span data-stu-id="dbcfb-255">4</span></span>|  
|`ver_ICorDebugInternalFrame2`|[<span data-ttu-id="dbcfb-256">ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="dbcfb-256">ICorDebugInternalFrame2</span></span>](icordebuginternalframe2-interface.md)|<span data-ttu-id="dbcfb-257">4</span><span class="sxs-lookup"><span data-stu-id="dbcfb-257">4</span></span>|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[<span data-ttu-id="dbcfb-258">ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="dbcfb-258">ICorDebugRuntimeUnwindableFrame</span></span>](icordebugruntimeunwindableframe-interface.md)|<span data-ttu-id="dbcfb-259">4</span><span class="sxs-lookup"><span data-stu-id="dbcfb-259">4</span></span>|  
|`ver_ICorDebugHeapValue3`|[<span data-ttu-id="dbcfb-260">ICorDebugHeapValue3, interface</span><span class="sxs-lookup"><span data-stu-id="dbcfb-260">ICorDebugHeapValue3 Interface</span></span>](icordebugheapvalue3-interface.md)|<span data-ttu-id="dbcfb-261">4</span><span class="sxs-lookup"><span data-stu-id="dbcfb-261">4</span></span>|  
|`ver_ICorDebugBlockingObjectEnum`|[<span data-ttu-id="dbcfb-262">ICorDebugBlockingObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="dbcfb-262">ICorDebugBlockingObjectEnum Interface</span></span>](icordebugblockingobjectenum-interface.md)|<span data-ttu-id="dbcfb-263">4</span><span class="sxs-lookup"><span data-stu-id="dbcfb-263">4</span></span>|  
|`ver_ICorDebugValue3`|[<span data-ttu-id="dbcfb-264">ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="dbcfb-264">ICorDebugValue3</span></span>](icordebugvalue3-interface.md)|<span data-ttu-id="dbcfb-265">4</span><span class="sxs-lookup"><span data-stu-id="dbcfb-265">4</span></span>|  
|`ver_ICorDebugComObjectValue`|[<span data-ttu-id="dbcfb-266">ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="dbcfb-266">ICorDebugComObjectValue</span></span>](icordebugcomobjectvalue-interface.md)|<span data-ttu-id="dbcfb-267">4.5</span><span class="sxs-lookup"><span data-stu-id="dbcfb-267">4.5</span></span>|  
|`ver_ICorDebugAppDomain3`|[<span data-ttu-id="dbcfb-268">ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="dbcfb-268">ICorDebugAppDomain3</span></span>](icordebugappdomain3-interface.md)|<span data-ttu-id="dbcfb-269">4.5</span><span class="sxs-lookup"><span data-stu-id="dbcfb-269">4.5</span></span>|  
|`ver_ICorDebugCode3`|[<span data-ttu-id="dbcfb-270">ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="dbcfb-270">ICorDebugCode3</span></span>](icordebugcode3-interface.md)|<span data-ttu-id="dbcfb-271">4.5</span><span class="sxs-lookup"><span data-stu-id="dbcfb-271">4.5</span></span>|  
|`ver_ICorDebugILFrame3`|[<span data-ttu-id="dbcfb-272">ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="dbcfb-272">ICorDebugILFrame3</span></span>](icordebugilframe3-interface.md)|<span data-ttu-id="dbcfb-273">4.5</span><span class="sxs-lookup"><span data-stu-id="dbcfb-273">4.5</span></span>|  
|`CorDebugLatestVersion`|<span data-ttu-id="dbcfb-274">La version de .NET Framework, y compris tous ses Service Packs, est la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-274">The version of the .NET Framework, including all of its service packs, is the latest version.</span></span>|-|  
  
## <a name="remarks"></a><span data-ttu-id="dbcfb-275">Notes </span><span class="sxs-lookup"><span data-stu-id="dbcfb-275">Remarks</span></span>  
 <span data-ttu-id="dbcfb-276">Un débogueur peut utiliser l' `CorDebugInterfaceVersion` énumération dans la fonction [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) pour spécifier la version la plus récente du .NET Framework que le débogueur prend en charge.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-276">A debugger can use the `CorDebugInterfaceVersion` enumeration in the [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) function to specify the highest version of the .NET Framework that the debugger supports.</span></span>  
  
## <a name="interface-names"></a><span data-ttu-id="dbcfb-277">Noms d'interface</span><span class="sxs-lookup"><span data-stu-id="dbcfb-277">Interface Names</span></span>  
 <span data-ttu-id="dbcfb-278">Le numéro qui figure à la fin des noms d'interface dans l'API de débogage (par exemple le « 3 » dans `ICorDebugThread3`) spécifie la version de l'interface et non pas la version de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-278">The number that appears at the end of the interface names in the debugging API (for example, the "3" in `ICorDebugThread3`) specifies the version of the interface, not the version of the .NET Framework.</span></span> <span data-ttu-id="dbcfb-279">Tous les noms d'interface de l'API de débogage incluent des numéros de version, excepté pour les interfaces qui ont été introduites dans .NET Framework version 1.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-279">All interface names in the debugging API include version numbers except for interfaces that were introduced in the .NET Framework version 1.</span></span> <span data-ttu-id="dbcfb-280">Toute correspondance entre le numéro de version de l'interface et le numéro de version de .NET Framework n'est qu'une pure coïncidence.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-280">Any correspondence between interface version numbers and.NET Framework version numbers are coincidental.</span></span>  
  
- <span data-ttu-id="dbcfb-281">Les interfaces qui ont été introduites dans .NET Framework version 1.0 n'incluent pas de numéro, car elles sont toutes implicitement en version 1.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-281">Interfaces that were introduced in the .NET Framework version 1.0 do not include numbers, because they are all implicitly version 1.</span></span>  
  
- <span data-ttu-id="dbcfb-282">.NET Framework version 1.1 utilise des interfaces version 1.0 et n'introduit aucune nouvelle interface de débogage.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-282">The .NET Framework version 1.1 uses version 1.0 interfaces, and does not introduce any new debugging interfaces.</span></span>  
  
- <span data-ttu-id="dbcfb-283">Les 14 interfaces de débogage introduites dans .NET Framework version 2.0 sont des extensions logiques de leur équivalent en version 1. Le numéro « 2 » figure dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-283">The 14 debugging interfaces introduced in the .NET Framework version 2.0 are logical extensions of their version 1 counterparts and include the number "2" in their names.</span></span>  
  
- <span data-ttu-id="dbcfb-284">Les versions 3.0 et 3.5 de .NET Framework utilisent les interfaces existantes de .NET Framework 2.0 et n'introduisent aucune nouvelle interface.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-284">The .NET Framework versions 3.0 and 3.5 use the existing .NET Framework 2.0 interfaces, and do not introduce any new interfaces.</span></span>  
  
- <span data-ttu-id="dbcfb-285">Le .NET Framework 4 introduit une combinaison de versions d’interface.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-285">The .NET Framework 4 introduces a mix of interface versions.</span></span> <span data-ttu-id="dbcfb-286">Par exemple, `ICorDebugThread3` et `ICorDebugThread4` apparaissent respectivement comme la troisième et la quatrième version de l'interface d'`ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="dbcfb-286">For example, both `ICorDebugThread3` and `ICorDebugThread4` appear as the third and fourth versions of the `ICorDebugThread` interface.</span></span> <span data-ttu-id="dbcfb-287">Le .NET Framework 4 introduit également la première version de l' `ICorDebugStackWalk` interface et la deuxième version de l' `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span><span class="sxs-lookup"><span data-stu-id="dbcfb-287">The .NET Framework 4 also introduces the first version of the `ICorDebugStackWalk` interface and the second version of the `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbcfb-288">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dbcfb-288">Requirements</span></span>  
 <span data-ttu-id="dbcfb-289">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbcfb-289">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbcfb-290">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbcfb-290">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbcfb-291">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbcfb-291">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbcfb-292">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbcfb-292">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbcfb-293">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbcfb-293">See also</span></span>

- [<span data-ttu-id="dbcfb-294">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="dbcfb-294">Debugging Enumerations</span></span>](debugging-enumerations.md)
