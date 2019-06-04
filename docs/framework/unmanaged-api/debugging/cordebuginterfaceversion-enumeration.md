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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37551d2b43e5343ca27da69c08d522c176b2caa7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489640"
---
# <a name="cordebuginterfaceversion-enumeration"></a><span data-ttu-id="6c4b3-102">CorDebugInterfaceVersion, énumération</span><span class="sxs-lookup"><span data-stu-id="6c4b3-102">CorDebugInterfaceVersion Enumeration</span></span>
<span data-ttu-id="6c4b3-103">Spécifie une interface, une version de .NET Framework ou une version de .NET Framework où une interface a été introduite.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-103">Specifies an interface, a version of the .NET Framework, or a version of the .NET Framework in which an interface was introduced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c4b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c4b3-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="6c4b3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6c4b3-105">Members</span></span>  
 <span data-ttu-id="6c4b3-106">Le tableau suivant fournit des liens de chaque valeur de l'énumération vers l'interface correspondante.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-106">The following table provides links from each enumeration value to the corresponding interface.</span></span> <span data-ttu-id="6c4b3-107">En outre, le tableau indique la première version de .NET Framework qui a pris en charge l'interface.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-107">In addition, the table indicates the first version of the .NET Framework that the interface was supported in.</span></span>  
  
|<span data-ttu-id="6c4b3-108">Membre</span><span class="sxs-lookup"><span data-stu-id="6c4b3-108">Member</span></span>|<span data-ttu-id="6c4b3-109">Informations fournies</span><span class="sxs-lookup"><span data-stu-id="6c4b3-109">Specifies</span></span>|<span data-ttu-id="6c4b3-110">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6c4b3-110">.NET Framework version</span></span>|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|<span data-ttu-id="6c4b3-111">La version de .NET Framework est non valide.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-111">The version of the .NET Framework is invalid.</span></span>|-|  
|`CorDebugVersion_1_0`|<span data-ttu-id="6c4b3-112">La version de .NET Framework, y compris tous ses Service Packs, est 1.0.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-112">The version of the .NET Framework, including all its service packs, is 1.0.</span></span>|<span data-ttu-id="6c4b3-113">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-113">1.0</span></span>|  
|`CorDebugVersion_1_1`|<span data-ttu-id="6c4b3-114">La version de .NET Framework, y compris tous les Service Packs, est 1.1.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-114">The version of the .NET Framework, including all service packs, is 1.1.</span></span>|<span data-ttu-id="6c4b3-115">1.1</span><span class="sxs-lookup"><span data-stu-id="6c4b3-115">1.1</span></span>|  
|`CorDebugVersion_2_0`|<span data-ttu-id="6c4b3-116">La version de .NET Framework, y compris tous les Service Packs, est 2.0.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-116">The version of the .NET Framework, including all service packs, is 2.0.</span></span>|<span data-ttu-id="6c4b3-117">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-117">2.0</span></span>|  
|`CorDebugVersion_4_0`|<span data-ttu-id="6c4b3-118">La version de .NET Framework, y compris tous les Service Packs, est 4.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-118">The version of the .NET Framework, including all service packs, is 4.</span></span>|<span data-ttu-id="6c4b3-119">4</span><span class="sxs-lookup"><span data-stu-id="6c4b3-119">4</span></span>|  
|`CorDebugVersion_4_5`|<span data-ttu-id="6c4b3-120">La version de .NET Framework, y compris tous les Service Packs, est 4.5.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-120">The version of the .NET Framework, including all service packs, is 4.5.</span></span>|<span data-ttu-id="6c4b3-121">4.5</span><span class="sxs-lookup"><span data-stu-id="6c4b3-121">4.5</span></span>|  
|`ver_ICorDebugManagedCallback`|[<span data-ttu-id="6c4b3-122">ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="6c4b3-122">ICorDebugManagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)|<span data-ttu-id="6c4b3-123">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-123">1.0</span></span>|  
|`ver_ICorDebugUnmanagedCallback`|[<span data-ttu-id="6c4b3-124">ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="6c4b3-124">ICorDebugUnmanagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)|<span data-ttu-id="6c4b3-125">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-125">1.0</span></span>|  
|`ver_ICorDebug`|[<span data-ttu-id="6c4b3-126">ICorDebug</span><span class="sxs-lookup"><span data-stu-id="6c4b3-126">ICorDebug</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)|<span data-ttu-id="6c4b3-127">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-127">1.0</span></span>|  
|`ver_ICorDebugController`|[<span data-ttu-id="6c4b3-128">ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="6c4b3-128">ICorDebugController</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)|<span data-ttu-id="6c4b3-129">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-129">1.0</span></span>|  
|`ver_ICorDebugAppDomain`|[<span data-ttu-id="6c4b3-130">ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="6c4b3-130">ICorDebugAppDomain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)|<span data-ttu-id="6c4b3-131">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-131">1.0</span></span>|  
|`ver_ICorDebugAssembly`|[<span data-ttu-id="6c4b3-132">ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="6c4b3-132">ICorDebugAssembly</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)|<span data-ttu-id="6c4b3-133">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-133">1.0</span></span>|  
|`ver_ICorDebugProcess`|[<span data-ttu-id="6c4b3-134">ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="6c4b3-134">ICorDebugProcess</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)|<span data-ttu-id="6c4b3-135">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-135">1.0</span></span>|  
|`ver_ICorDebugBreakpoint`|[<span data-ttu-id="6c4b3-136">ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="6c4b3-136">ICorDebugBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)|<span data-ttu-id="6c4b3-137">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-137">1.0</span></span>|  
|`ver_ICorDebugFunctionBreakpoint`|[<span data-ttu-id="6c4b3-138">ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="6c4b3-138">ICorDebugFunctionBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)|<span data-ttu-id="6c4b3-139">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-139">1.0</span></span>|  
|`ver_ICorDebugModuleBreakpoint`|[<span data-ttu-id="6c4b3-140">ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="6c4b3-140">ICorDebugModuleBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)|<span data-ttu-id="6c4b3-141">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-141">1.0</span></span>|  
|`ver_ICorDebugValueBreakpoint`|[<span data-ttu-id="6c4b3-142">ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="6c4b3-142">ICorDebugValueBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-interface.md)|<span data-ttu-id="6c4b3-143">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-143">1.0</span></span>|  
|`ver_ICorDebugStepper`|[<span data-ttu-id="6c4b3-144">ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="6c4b3-144">ICorDebugStepper</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)|<span data-ttu-id="6c4b3-145">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-145">1.0</span></span>|  
|`ver_ICorDebugRegisterSet`|[<span data-ttu-id="6c4b3-146">ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="6c4b3-146">ICorDebugRegisterSet</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)|<span data-ttu-id="6c4b3-147">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-147">1.0</span></span>|  
|`ver_ICorDebugThread`|[<span data-ttu-id="6c4b3-148">ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="6c4b3-148">ICorDebugThread</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)|<span data-ttu-id="6c4b3-149">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-149">1.0</span></span>|  
|`ver_ICorDebugChain`|[<span data-ttu-id="6c4b3-150">ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="6c4b3-150">ICorDebugChain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)|<span data-ttu-id="6c4b3-151">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-151">1.0</span></span>|  
|`ver_ICorDebugFrame`|[<span data-ttu-id="6c4b3-152">ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="6c4b3-152">ICorDebugFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)|<span data-ttu-id="6c4b3-153">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-153">1.0</span></span>|  
|`ver_ICorDebugILFrame`|[<span data-ttu-id="6c4b3-154">ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="6c4b3-154">ICorDebugILFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)|<span data-ttu-id="6c4b3-155">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-155">1.0</span></span>|  
|`ver_ICorDebugNativeFrame`|[<span data-ttu-id="6c4b3-156">ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="6c4b3-156">ICorDebugNativeFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)|<span data-ttu-id="6c4b3-157">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-157">1.0</span></span>|  
|`ver_ICorDebugModule`|[<span data-ttu-id="6c4b3-158">ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="6c4b3-158">ICorDebugModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)|<span data-ttu-id="6c4b3-159">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-159">1.0</span></span>|  
|`ver_ICorDebugFunction`|[<span data-ttu-id="6c4b3-160">ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="6c4b3-160">ICorDebugFunction</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)|<span data-ttu-id="6c4b3-161">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-161">1.0</span></span>|  
|`ver_ICorDebugCode`|[<span data-ttu-id="6c4b3-162">ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="6c4b3-162">ICorDebugCode</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)|<span data-ttu-id="6c4b3-163">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-163">1.0</span></span>|  
|`ver_ICorDebugClass`|[<span data-ttu-id="6c4b3-164">ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="6c4b3-164">ICorDebugClass</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)|<span data-ttu-id="6c4b3-165">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-165">1.0</span></span>|  
|`ver_ICorDebugEval`|[<span data-ttu-id="6c4b3-166">ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="6c4b3-166">ICorDebugEval</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)|<span data-ttu-id="6c4b3-167">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-167">1.0</span></span>|  
|`ver_ICorDebugValue`|[<span data-ttu-id="6c4b3-168">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="6c4b3-168">ICorDebugValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)|<span data-ttu-id="6c4b3-169">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-169">1.0</span></span>|  
|`ver_ICorDebugGenericValue`|[<span data-ttu-id="6c4b3-170">ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="6c4b3-170">ICorDebugGenericValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)|<span data-ttu-id="6c4b3-171">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-171">1.0</span></span>|  
|`ver_ICorDebugReferenceValue`|[<span data-ttu-id="6c4b3-172">ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="6c4b3-172">ICorDebugReferenceValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)|<span data-ttu-id="6c4b3-173">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-173">1.0</span></span>|  
|`ver_ICorDebugHeapValue`|[<span data-ttu-id="6c4b3-174">ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="6c4b3-174">ICorDebugHeapValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)|<span data-ttu-id="6c4b3-175">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-175">1.0</span></span>|  
|`ver_ICorDebugObjectValue`|[<span data-ttu-id="6c4b3-176">ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="6c4b3-176">ICorDebugObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)|<span data-ttu-id="6c4b3-177">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-177">1.0</span></span>|  
|`ver_ICorDebugBoxValue`|[<span data-ttu-id="6c4b3-178">ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="6c4b3-178">ICorDebugBoxValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)|<span data-ttu-id="6c4b3-179">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-179">1.0</span></span>|  
|`ver_ICorDebugStringValue`|[<span data-ttu-id="6c4b3-180">ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="6c4b3-180">ICorDebugStringValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)|<span data-ttu-id="6c4b3-181">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-181">1.0</span></span>|  
|`ver_ICorDebugArrayValue`|[<span data-ttu-id="6c4b3-182">ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="6c4b3-182">ICorDebugArrayValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)|<span data-ttu-id="6c4b3-183">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-183">1.0</span></span>|  
|`ver_ICorDebugContext`|[<span data-ttu-id="6c4b3-184">ICorDebugContext</span><span class="sxs-lookup"><span data-stu-id="6c4b3-184">ICorDebugContext</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)|<span data-ttu-id="6c4b3-185">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-185">1.0</span></span>|  
|`ver_ICorDebugEnum`|[<span data-ttu-id="6c4b3-186">ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-186">ICorDebugEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)|<span data-ttu-id="6c4b3-187">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-187">1.0</span></span>|  
|`ver_ICorDebugObjectEnum`|[<span data-ttu-id="6c4b3-188">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-188">ICorDebugObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)|<span data-ttu-id="6c4b3-189">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-189">1.0</span></span>|  
|`ver_ICorDebugBreakpointEnum`|[<span data-ttu-id="6c4b3-190">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-190">ICorDebugBreakpointEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)|<span data-ttu-id="6c4b3-191">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-191">1.0</span></span>|  
|`ver_ICorDebugStepperEnum`|[<span data-ttu-id="6c4b3-192">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-192">ICorDebugStepperEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)|<span data-ttu-id="6c4b3-193">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-193">1.0</span></span>|  
|`ver_ICorDebugProcessEnum`|[<span data-ttu-id="6c4b3-194">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-194">ICorDebugProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)|<span data-ttu-id="6c4b3-195">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-195">1.0</span></span>|  
|`ver_ICorDebugThreadEnum`|[<span data-ttu-id="6c4b3-196">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-196">ICorDebugThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)|<span data-ttu-id="6c4b3-197">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-197">1.0</span></span>|  
|`ver_ICorDebugFrameEnum`|[<span data-ttu-id="6c4b3-198">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-198">ICorDebugFrameEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)|<span data-ttu-id="6c4b3-199">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-199">1.0</span></span>|  
|`ver_ICorDebugChainEnum`|[<span data-ttu-id="6c4b3-200">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-200">ICorDebugChainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)|<span data-ttu-id="6c4b3-201">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-201">1.0</span></span>|  
|`ver_ICorDebugModuleEnum`|[<span data-ttu-id="6c4b3-202">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-202">ICorDebugModuleEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)|<span data-ttu-id="6c4b3-203">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-203">1.0</span></span>|  
|`ver_ICorDebugValueEnum`|[<span data-ttu-id="6c4b3-204">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-204">ICorDebugValueEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-interface.md)|<span data-ttu-id="6c4b3-205">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-205">1.0</span></span>|  
|`ver_ICorDebugCodeEnum`|[<span data-ttu-id="6c4b3-206">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-206">ICorDebugCodeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)|<span data-ttu-id="6c4b3-207">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-207">1.0</span></span>|  
|`ver_ICorDebugTypeEnum`|[<span data-ttu-id="6c4b3-208">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-208">ICorDebugTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)|<span data-ttu-id="6c4b3-209">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-209">1.0</span></span>|  
|`ver_ICorDebugErrorInfoEnum`|[<span data-ttu-id="6c4b3-210">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-210">ICorDebugErrorInfoEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)|<span data-ttu-id="6c4b3-211">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-211">1.0</span></span>|  
|`ver_ICorDebugAppDomainEnum`|[<span data-ttu-id="6c4b3-212">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-212">ICorDebugAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)|<span data-ttu-id="6c4b3-213">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-213">1.0</span></span>|  
|`ver_ICorDebugAssemblyEnum`|[<span data-ttu-id="6c4b3-214">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="6c4b3-214">ICorDebugAssemblyEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)|<span data-ttu-id="6c4b3-215">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-215">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[<span data-ttu-id="6c4b3-216">ICorDebugEditAndContinueErrorInfo</span><span class="sxs-lookup"><span data-stu-id="6c4b3-216">ICorDebugEditAndContinueErrorInfo</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)|<span data-ttu-id="6c4b3-217">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-217">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueSnapshot`|[<span data-ttu-id="6c4b3-218">ICorDebugEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="6c4b3-218">ICorDebugEditAndContinueSnapshot</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)|<span data-ttu-id="6c4b3-219">1.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-219">1.0</span></span>|  
|`ver_ICorDebugManagedCallback2`|[<span data-ttu-id="6c4b3-220">ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-220">ICorDebugManagedCallback2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)|<span data-ttu-id="6c4b3-221">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-221">2.0</span></span>|  
|`ver_ICorDebugAppDomain2`|[<span data-ttu-id="6c4b3-222">ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-222">ICorDebugAppDomain2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)|<span data-ttu-id="6c4b3-223">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-223">2.0</span></span>|  
|`ver_ICorDebugProcess2`|[<span data-ttu-id="6c4b3-224">ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-224">ICorDebugProcess2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)|<span data-ttu-id="6c4b3-225">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-225">2.0</span></span>|  
|`ver_ICorDebugStepper2`|[<span data-ttu-id="6c4b3-226">ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-226">ICorDebugStepper2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)|<span data-ttu-id="6c4b3-227">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-227">2.0</span></span>|  
|`ver_ICorDebugRegisterSet2`|[<span data-ttu-id="6c4b3-228">ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-228">ICorDebugRegisterSet2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)|<span data-ttu-id="6c4b3-229">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-229">2.0</span></span>|  
|`ver_ICorDebugThread2`|[<span data-ttu-id="6c4b3-230">ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-230">ICorDebugThread2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)|<span data-ttu-id="6c4b3-231">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-231">2.0</span></span>|  
|`ver_ICorDebugILFrame2`|[<span data-ttu-id="6c4b3-232">ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-232">ICorDebugILFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)|<span data-ttu-id="6c4b3-233">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-233">2.0</span></span>|  
|`ver_ICorDebugModule2`|[<span data-ttu-id="6c4b3-234">ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-234">ICorDebugModule2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)|<span data-ttu-id="6c4b3-235">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-235">2.0</span></span>|  
|`ver_ICorDebugFunction2`|[<span data-ttu-id="6c4b3-236">ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-236">ICorDebugFunction2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)|<span data-ttu-id="6c4b3-237">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-237">2.0</span></span>|  
|`ver_ICorDebugCode2`|[<span data-ttu-id="6c4b3-238">ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-238">ICorDebugCode2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)|<span data-ttu-id="6c4b3-239">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-239">2.0</span></span>|  
|`ver_ICorDebugClass2`|<span data-ttu-id="6c4b3-240">"ICorDebugClass2"</span><span class="sxs-lookup"><span data-stu-id="6c4b3-240">"ICorDebugClass2"</span></span>|<span data-ttu-id="6c4b3-241">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-241">2.0</span></span>|  
|`ver_ICorDebugValue2`|<span data-ttu-id="6c4b3-242">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="6c4b3-242">"ICorDebugValue2"</span></span>|<span data-ttu-id="6c4b3-243">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-243">2.0</span></span>|  
|`ver_ICorDebugEval2`|<span data-ttu-id="6c4b3-244">« ICorDebugEval2 ».</span><span class="sxs-lookup"><span data-stu-id="6c4b3-244">The "ICorDebugEval2".</span></span>|<span data-ttu-id="6c4b3-245">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-245">2.0</span></span>|  
|`ver_ICorDebugObjectValue2`|<span data-ttu-id="6c4b3-246">"ICorDebugObjectValue2"</span><span class="sxs-lookup"><span data-stu-id="6c4b3-246">"ICorDebugObjectValue2"</span></span>|<span data-ttu-id="6c4b3-247">2.0</span><span class="sxs-lookup"><span data-stu-id="6c4b3-247">2.0</span></span>|  
|`ver_ICorDebugThread3`|[<span data-ttu-id="6c4b3-248">ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="6c4b3-248">ICorDebugThread3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)|<span data-ttu-id="6c4b3-249">4</span><span class="sxs-lookup"><span data-stu-id="6c4b3-249">4</span></span>|  
|`ver_ICorDebugThread4`|[<span data-ttu-id="6c4b3-250">ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="6c4b3-250">ICorDebugThread4</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)|<span data-ttu-id="6c4b3-251">4</span><span class="sxs-lookup"><span data-stu-id="6c4b3-251">4</span></span>|  
|`ver_ICorDebugStackWalk`|[<span data-ttu-id="6c4b3-252">ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="6c4b3-252">ICorDebugStackWalk</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)|<span data-ttu-id="6c4b3-253">4</span><span class="sxs-lookup"><span data-stu-id="6c4b3-253">4</span></span>|  
|`ver_ICorDebugNativeFrame2`|[<span data-ttu-id="6c4b3-254">ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-254">ICorDebugNativeFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)|<span data-ttu-id="6c4b3-255">4</span><span class="sxs-lookup"><span data-stu-id="6c4b3-255">4</span></span>|  
|`ver_ICorDebugInternalFrame2`|[<span data-ttu-id="6c4b3-256">ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="6c4b3-256">ICorDebugInternalFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)|<span data-ttu-id="6c4b3-257">4</span><span class="sxs-lookup"><span data-stu-id="6c4b3-257">4</span></span>|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[<span data-ttu-id="6c4b3-258">ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="6c4b3-258">ICorDebugRuntimeUnwindableFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)|<span data-ttu-id="6c4b3-259">4</span><span class="sxs-lookup"><span data-stu-id="6c4b3-259">4</span></span>|  
|`ver_ICorDebugHeapValue3`|[<span data-ttu-id="6c4b3-260">ICorDebugHeapValue3, interface</span><span class="sxs-lookup"><span data-stu-id="6c4b3-260">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)|<span data-ttu-id="6c4b3-261">4</span><span class="sxs-lookup"><span data-stu-id="6c4b3-261">4</span></span>|  
|`ver_ICorDebugBlockingObjectEnum`|[<span data-ttu-id="6c4b3-262">ICorDebugBlockingObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="6c4b3-262">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)|<span data-ttu-id="6c4b3-263">4</span><span class="sxs-lookup"><span data-stu-id="6c4b3-263">4</span></span>|  
|`ver_ICorDebugValue3`|[<span data-ttu-id="6c4b3-264">ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="6c4b3-264">ICorDebugValue3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)|<span data-ttu-id="6c4b3-265">4</span><span class="sxs-lookup"><span data-stu-id="6c4b3-265">4</span></span>|  
|`ver_ICorDebugComObjectValue`|[<span data-ttu-id="6c4b3-266">ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="6c4b3-266">ICorDebugComObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)|<span data-ttu-id="6c4b3-267">4.5</span><span class="sxs-lookup"><span data-stu-id="6c4b3-267">4.5</span></span>|  
|`ver_ICorDebugAppDomain3`|[<span data-ttu-id="6c4b3-268">ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="6c4b3-268">ICorDebugAppDomain3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)|<span data-ttu-id="6c4b3-269">4.5</span><span class="sxs-lookup"><span data-stu-id="6c4b3-269">4.5</span></span>|  
|`ver_ICorDebugCode3`|[<span data-ttu-id="6c4b3-270">ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="6c4b3-270">ICorDebugCode3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)|<span data-ttu-id="6c4b3-271">4.5</span><span class="sxs-lookup"><span data-stu-id="6c4b3-271">4.5</span></span>|  
|`ver_ICorDebugILFrame3`|[<span data-ttu-id="6c4b3-272">ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="6c4b3-272">ICorDebugILFrame3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)|<span data-ttu-id="6c4b3-273">4.5</span><span class="sxs-lookup"><span data-stu-id="6c4b3-273">4.5</span></span>|  
|`CorDebugLatestVersion`|<span data-ttu-id="6c4b3-274">La version de .NET Framework, y compris tous ses Service Packs, est la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-274">The version of the .NET Framework, including all of its service packs, is the latest version.</span></span>|-|  
  
## <a name="remarks"></a><span data-ttu-id="6c4b3-275">Notes</span><span class="sxs-lookup"><span data-stu-id="6c4b3-275">Remarks</span></span>  
 <span data-ttu-id="6c4b3-276">Un débogueur peut utiliser le `CorDebugInterfaceVersion` énumération dans le [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) (fonction) pour spécifier la version la plus récente du .NET Framework qui prend en charge par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-276">A debugger can use the `CorDebugInterfaceVersion` enumeration in the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function to specify the highest version of the .NET Framework that the debugger supports.</span></span>  
  
## <a name="interface-names"></a><span data-ttu-id="6c4b3-277">Noms d'interface</span><span class="sxs-lookup"><span data-stu-id="6c4b3-277">Interface Names</span></span>  
 <span data-ttu-id="6c4b3-278">Le numéro qui figure à la fin des noms d'interface dans l'API de débogage (par exemple le « 3 » dans `ICorDebugThread3`) spécifie la version de l'interface et non pas la version de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-278">The number that appears at the end of the interface names in the debugging API (for example, the "3" in `ICorDebugThread3`) specifies the version of the interface, not the version of the .NET Framework.</span></span> <span data-ttu-id="6c4b3-279">Tous les noms d'interface de l'API de débogage incluent des numéros de version, excepté pour les interfaces qui ont été introduites dans .NET Framework version 1.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-279">All interface names in the debugging API include version numbers except for interfaces that were introduced in the .NET Framework version 1.</span></span> <span data-ttu-id="6c4b3-280">Toute correspondance entre le numéro de version de l'interface et le numéro de version de .NET Framework n'est qu'une pure coïncidence.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-280">Any correspondence between interface version numbers and.NET Framework version numbers are coincidental.</span></span>  
  
- <span data-ttu-id="6c4b3-281">Les interfaces qui ont été introduites dans .NET Framework version 1.0 n'incluent pas de numéro, car elles sont toutes implicitement en version 1.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-281">Interfaces that were introduced in the .NET Framework version 1.0 do not include numbers, because they are all implicitly version 1.</span></span>  
  
- <span data-ttu-id="6c4b3-282">.NET Framework version 1.1 utilise des interfaces version 1.0 et n'introduit aucune nouvelle interface de débogage.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-282">The .NET Framework version 1.1 uses version 1.0 interfaces, and does not introduce any new debugging interfaces.</span></span>  
  
- <span data-ttu-id="6c4b3-283">Les 14 interfaces de débogage introduites dans .NET Framework version 2.0 sont des extensions logiques de leur équivalent en version 1. Le numéro « 2 » figure dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-283">The 14 debugging interfaces introduced in the .NET Framework version 2.0 are logical extensions of their version 1 counterparts and include the number "2" in their names.</span></span>  
  
- <span data-ttu-id="6c4b3-284">Les versions 3.0 et 3.5 de .NET Framework utilisent les interfaces existantes de .NET Framework 2.0 et n'introduisent aucune nouvelle interface.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-284">The .NET Framework versions 3.0 and 3.5 use the existing .NET Framework 2.0 interfaces, and do not introduce any new interfaces.</span></span>  
  
- <span data-ttu-id="6c4b3-285">Le .NET Framework 4 introduit un mélange de versions de l’interface.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-285">The .NET Framework 4 introduces a mix of interface versions.</span></span> <span data-ttu-id="6c4b3-286">Par exemple, `ICorDebugThread3` et `ICorDebugThread4` apparaissent respectivement comme la troisième et la quatrième version de l'interface d'`ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="6c4b3-286">For example, both `ICorDebugThread3` and `ICorDebugThread4` appear as the third and fourth versions of the `ICorDebugThread` interface.</span></span> <span data-ttu-id="6c4b3-287">Le .NET Framework 4 introduit également la première version de la `ICorDebugStackWalk` interface et la deuxième version de la `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span><span class="sxs-lookup"><span data-stu-id="6c4b3-287">The .NET Framework 4 also introduces the first version of the `ICorDebugStackWalk` interface and the second version of the `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c4b3-288">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6c4b3-288">Requirements</span></span>  
 <span data-ttu-id="6c4b3-289">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c4b3-289">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c4b3-290">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c4b3-290">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c4b3-291">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c4b3-291">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c4b3-292">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c4b3-292">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4b3-293">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c4b3-293">See also</span></span>

- [<span data-ttu-id="6c4b3-294">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="6c4b3-294">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
