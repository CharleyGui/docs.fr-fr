---
title: Événements ETW d'interopérabilité
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c52c9bf37e67e4d26867d2b3754945e86e2bf609
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422421"
---
# <a name="interop-etw-events"></a><span data-ttu-id="2d4ba-102">Événements ETW d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="2d4ba-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="2d4ba-103">Les événements d'interopérabilité capturent des informations sur la création et la mise en cache du stub MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="2d4ba-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="2d4ba-104">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="2d4ba-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="2d4ba-105">Événement ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="2d4ba-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="2d4ba-106">Événement ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="2d4ba-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="2d4ba-107">Événement ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="2d4ba-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="2d4ba-108">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="2d4ba-109">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="2d4ba-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="2d4ba-110">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="2d4ba-110">Keyword for raising the event</span></span>|<span data-ttu-id="2d4ba-111">Niveau</span><span class="sxs-lookup"><span data-stu-id="2d4ba-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2d4ba-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="2d4ba-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="2d4ba-113">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="2d4ba-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="2d4ba-114">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2d4ba-115">Événement</span><span class="sxs-lookup"><span data-stu-id="2d4ba-115">Event</span></span>|<span data-ttu-id="2d4ba-116">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="2d4ba-116">Event ID</span></span>|<span data-ttu-id="2d4ba-117">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="2d4ba-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="2d4ba-118">88</span><span class="sxs-lookup"><span data-stu-id="2d4ba-118">88</span></span>|<span data-ttu-id="2d4ba-119">Le stub MSIL a été généré.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="2d4ba-120">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2d4ba-121">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="2d4ba-121">Field name</span></span>|<span data-ttu-id="2d4ba-122">Type de données</span><span class="sxs-lookup"><span data-stu-id="2d4ba-122">Data type</span></span>|<span data-ttu-id="2d4ba-123">Description</span><span class="sxs-lookup"><span data-stu-id="2d4ba-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2d4ba-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="2d4ba-124">ModuleID</span></span>|<span data-ttu-id="2d4ba-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2d4ba-125">win:UInt16</span></span>|<span data-ttu-id="2d4ba-126">Identificateur du module</span><span class="sxs-lookup"><span data-stu-id="2d4ba-126">The module identifier.</span></span>|  
|<span data-ttu-id="2d4ba-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="2d4ba-127">StubMethodID</span></span>|<span data-ttu-id="2d4ba-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2d4ba-128">win:UInt64</span></span>|<span data-ttu-id="2d4ba-129">Identificateur de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="2d4ba-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="2d4ba-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="2d4ba-130">StubFlags</span></span>|<span data-ttu-id="2d4ba-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2d4ba-131">win:UInt64</span></span>|<span data-ttu-id="2d4ba-132">Indicateurs du stub :</span><span class="sxs-lookup"><span data-stu-id="2d4ba-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="2d4ba-133">0x1 – Interopérabilité inversée.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="2d4ba-134">0x2 – COM Interop</span><span class="sxs-lookup"><span data-stu-id="2d4ba-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="2d4ba-135">0x4 – Stub généré par NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="2d4ba-136">0x8 – Délégué</span><span class="sxs-lookup"><span data-stu-id="2d4ba-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="2d4ba-137">0 x 10 - argument variable.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-137">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="2d4ba-138">0x20 – Appelé non managé</span><span class="sxs-lookup"><span data-stu-id="2d4ba-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="2d4ba-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="2d4ba-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="2d4ba-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2d4ba-140">win:UInt32</span></span>|<span data-ttu-id="2d4ba-141">Jeton de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="2d4ba-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="2d4ba-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="2d4ba-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="2d4ba-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2d4ba-143">win:UnicodeString</span></span>|<span data-ttu-id="2d4ba-144">Espace de noms de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="2d4ba-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="2d4ba-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="2d4ba-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="2d4ba-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2d4ba-146">win:UnicodeString</span></span>|<span data-ttu-id="2d4ba-147">Nom de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="2d4ba-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="2d4ba-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="2d4ba-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="2d4ba-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2d4ba-149">win:UnicodeString</span></span>|<span data-ttu-id="2d4ba-150">Signature de la méthode d'interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="2d4ba-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="2d4ba-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="2d4ba-151">NativeMethodSignature</span></span>|<span data-ttu-id="2d4ba-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2d4ba-152">win:UnicodeString</span></span>|<span data-ttu-id="2d4ba-153">Signature de la méthode native</span><span class="sxs-lookup"><span data-stu-id="2d4ba-153">The native method signature.</span></span>|  
|<span data-ttu-id="2d4ba-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="2d4ba-154">StubMethodSignature</span></span>|<span data-ttu-id="2d4ba-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2d4ba-155">win:UnicodeString</span></span>|<span data-ttu-id="2d4ba-156">Signature de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="2d4ba-156">The stub method signature.</span></span>|  
|<span data-ttu-id="2d4ba-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="2d4ba-157">StubMethodILCode</span></span>|<span data-ttu-id="2d4ba-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2d4ba-158">win:UnicodeString</span></span>|<span data-ttu-id="2d4ba-159">Code MSIL de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="2d4ba-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="2d4ba-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2d4ba-160">ClrInstanceID</span></span>|<span data-ttu-id="2d4ba-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2d4ba-161">win:UInt16</span></span>|<span data-ttu-id="2d4ba-162">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2d4ba-163">Retour au début</span><span class="sxs-lookup"><span data-stu-id="2d4ba-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="2d4ba-164">Événement ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="2d4ba-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="2d4ba-165">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2d4ba-166">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="2d4ba-166">Keyword for raising the event</span></span>|<span data-ttu-id="2d4ba-167">Niveau</span><span class="sxs-lookup"><span data-stu-id="2d4ba-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2d4ba-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="2d4ba-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="2d4ba-169">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="2d4ba-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="2d4ba-170">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2d4ba-171">Événement</span><span class="sxs-lookup"><span data-stu-id="2d4ba-171">Event</span></span>|<span data-ttu-id="2d4ba-172">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="2d4ba-172">Event ID</span></span>|<span data-ttu-id="2d4ba-173">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="2d4ba-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="2d4ba-174">89</span><span class="sxs-lookup"><span data-stu-id="2d4ba-174">89</span></span>|<span data-ttu-id="2d4ba-175">Le cache MSIL a fait l’objet d’un accès.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="2d4ba-176">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2d4ba-177">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="2d4ba-177">Field name</span></span>|<span data-ttu-id="2d4ba-178">Type de données</span><span class="sxs-lookup"><span data-stu-id="2d4ba-178">Data type</span></span>|<span data-ttu-id="2d4ba-179">Description</span><span class="sxs-lookup"><span data-stu-id="2d4ba-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2d4ba-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="2d4ba-180">ModuleID</span></span>|<span data-ttu-id="2d4ba-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2d4ba-181">win:UInt16</span></span>|<span data-ttu-id="2d4ba-182">Identificateur du module</span><span class="sxs-lookup"><span data-stu-id="2d4ba-182">The module identifier.</span></span>|  
|<span data-ttu-id="2d4ba-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="2d4ba-183">StubMethodID</span></span>|<span data-ttu-id="2d4ba-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2d4ba-184">win:UInt64</span></span>|<span data-ttu-id="2d4ba-185">Identificateur de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="2d4ba-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="2d4ba-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="2d4ba-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="2d4ba-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2d4ba-187">win:UInt32</span></span>|<span data-ttu-id="2d4ba-188">Jeton de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="2d4ba-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="2d4ba-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="2d4ba-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="2d4ba-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2d4ba-190">win:UnicodeString</span></span>|<span data-ttu-id="2d4ba-191">Espace de noms de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="2d4ba-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="2d4ba-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="2d4ba-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="2d4ba-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2d4ba-193">win:UnicodeString</span></span>|<span data-ttu-id="2d4ba-194">Nom de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="2d4ba-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="2d4ba-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="2d4ba-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="2d4ba-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2d4ba-196">win:UnicodeString</span></span>|<span data-ttu-id="2d4ba-197">Signature de la méthode d'interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="2d4ba-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="2d4ba-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2d4ba-198">ClrInstanceID</span></span>|<span data-ttu-id="2d4ba-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2d4ba-199">win:UInt16</span></span>|<span data-ttu-id="2d4ba-200">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="2d4ba-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2d4ba-201">Retour au début</span><span class="sxs-lookup"><span data-stu-id="2d4ba-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="2d4ba-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d4ba-202">See also</span></span>

- [<span data-ttu-id="2d4ba-203">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="2d4ba-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
