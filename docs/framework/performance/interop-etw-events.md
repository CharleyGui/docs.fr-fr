---
title: Événements ETW d'interopérabilité
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 787c6221b651a53dbb932a5a9d0edea123e1d97d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046434"
---
# <a name="interop-etw-events"></a><span data-ttu-id="86b69-102">Événements ETW d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="86b69-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="86b69-103">Les événements d'interopérabilité capturent des informations sur la création et la mise en cache du stub MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="86b69-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="86b69-104">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="86b69-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="86b69-105">Événement ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="86b69-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="86b69-106">Événement ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="86b69-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="86b69-107">Événement ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="86b69-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="86b69-108">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="86b69-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="86b69-109">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="86b69-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="86b69-110">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="86b69-110">Keyword for raising the event</span></span>|<span data-ttu-id="86b69-111">Niveau</span><span class="sxs-lookup"><span data-stu-id="86b69-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="86b69-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="86b69-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="86b69-113">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="86b69-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="86b69-114">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="86b69-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="86b69-115">Événement</span><span class="sxs-lookup"><span data-stu-id="86b69-115">Event</span></span>|<span data-ttu-id="86b69-116">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="86b69-116">Event ID</span></span>|<span data-ttu-id="86b69-117">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="86b69-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="86b69-118">88</span><span class="sxs-lookup"><span data-stu-id="86b69-118">88</span></span>|<span data-ttu-id="86b69-119">Le stub MSIL a été généré.</span><span class="sxs-lookup"><span data-stu-id="86b69-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="86b69-120">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="86b69-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="86b69-121">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="86b69-121">Field name</span></span>|<span data-ttu-id="86b69-122">Type de données</span><span class="sxs-lookup"><span data-stu-id="86b69-122">Data type</span></span>|<span data-ttu-id="86b69-123">Description</span><span class="sxs-lookup"><span data-stu-id="86b69-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="86b69-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="86b69-124">ModuleID</span></span>|<span data-ttu-id="86b69-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="86b69-125">win:UInt16</span></span>|<span data-ttu-id="86b69-126">Identificateur du module</span><span class="sxs-lookup"><span data-stu-id="86b69-126">The module identifier.</span></span>|  
|<span data-ttu-id="86b69-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="86b69-127">StubMethodID</span></span>|<span data-ttu-id="86b69-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="86b69-128">win:UInt64</span></span>|<span data-ttu-id="86b69-129">Identificateur de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="86b69-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="86b69-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="86b69-130">StubFlags</span></span>|<span data-ttu-id="86b69-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="86b69-131">win:UInt64</span></span>|<span data-ttu-id="86b69-132">Indicateurs du stub :</span><span class="sxs-lookup"><span data-stu-id="86b69-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="86b69-133">0x1 – Interopérabilité inversée.</span><span class="sxs-lookup"><span data-stu-id="86b69-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="86b69-134">0x2 – COM Interop</span><span class="sxs-lookup"><span data-stu-id="86b69-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="86b69-135">0x4 – Stub généré par NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="86b69-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="86b69-136">0x8 – Délégué</span><span class="sxs-lookup"><span data-stu-id="86b69-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="86b69-137">0x10 : argument de variable.</span><span class="sxs-lookup"><span data-stu-id="86b69-137">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="86b69-138">0x20 – Appelé non managé</span><span class="sxs-lookup"><span data-stu-id="86b69-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="86b69-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="86b69-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="86b69-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="86b69-140">win:UInt32</span></span>|<span data-ttu-id="86b69-141">Jeton de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="86b69-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="86b69-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="86b69-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="86b69-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="86b69-143">win:UnicodeString</span></span>|<span data-ttu-id="86b69-144">Espace de noms de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="86b69-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="86b69-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="86b69-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="86b69-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="86b69-146">win:UnicodeString</span></span>|<span data-ttu-id="86b69-147">Nom de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="86b69-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="86b69-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="86b69-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="86b69-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="86b69-149">win:UnicodeString</span></span>|<span data-ttu-id="86b69-150">Signature de la méthode d'interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="86b69-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="86b69-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="86b69-151">NativeMethodSignature</span></span>|<span data-ttu-id="86b69-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="86b69-152">win:UnicodeString</span></span>|<span data-ttu-id="86b69-153">Signature de la méthode native</span><span class="sxs-lookup"><span data-stu-id="86b69-153">The native method signature.</span></span>|  
|<span data-ttu-id="86b69-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="86b69-154">StubMethodSignature</span></span>|<span data-ttu-id="86b69-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="86b69-155">win:UnicodeString</span></span>|<span data-ttu-id="86b69-156">Signature de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="86b69-156">The stub method signature.</span></span>|  
|<span data-ttu-id="86b69-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="86b69-157">StubMethodILCode</span></span>|<span data-ttu-id="86b69-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="86b69-158">win:UnicodeString</span></span>|<span data-ttu-id="86b69-159">Code MSIL de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="86b69-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="86b69-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="86b69-160">ClrInstanceID</span></span>|<span data-ttu-id="86b69-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="86b69-161">win:UInt16</span></span>|<span data-ttu-id="86b69-162">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="86b69-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="86b69-163">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="86b69-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="86b69-164">Événement ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="86b69-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="86b69-165">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="86b69-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="86b69-166">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="86b69-166">Keyword for raising the event</span></span>|<span data-ttu-id="86b69-167">Niveau</span><span class="sxs-lookup"><span data-stu-id="86b69-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="86b69-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="86b69-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="86b69-169">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="86b69-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="86b69-170">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="86b69-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="86b69-171">Événement</span><span class="sxs-lookup"><span data-stu-id="86b69-171">Event</span></span>|<span data-ttu-id="86b69-172">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="86b69-172">Event ID</span></span>|<span data-ttu-id="86b69-173">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="86b69-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="86b69-174">89</span><span class="sxs-lookup"><span data-stu-id="86b69-174">89</span></span>|<span data-ttu-id="86b69-175">Le cache MSIL a fait l’objet d’un accès.</span><span class="sxs-lookup"><span data-stu-id="86b69-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="86b69-176">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="86b69-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="86b69-177">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="86b69-177">Field name</span></span>|<span data-ttu-id="86b69-178">Type de données</span><span class="sxs-lookup"><span data-stu-id="86b69-178">Data type</span></span>|<span data-ttu-id="86b69-179">Description</span><span class="sxs-lookup"><span data-stu-id="86b69-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="86b69-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="86b69-180">ModuleID</span></span>|<span data-ttu-id="86b69-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="86b69-181">win:UInt16</span></span>|<span data-ttu-id="86b69-182">Identificateur du module</span><span class="sxs-lookup"><span data-stu-id="86b69-182">The module identifier.</span></span>|  
|<span data-ttu-id="86b69-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="86b69-183">StubMethodID</span></span>|<span data-ttu-id="86b69-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="86b69-184">win:UInt64</span></span>|<span data-ttu-id="86b69-185">Identificateur de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="86b69-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="86b69-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="86b69-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="86b69-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="86b69-187">win:UInt32</span></span>|<span data-ttu-id="86b69-188">Jeton de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="86b69-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="86b69-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="86b69-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="86b69-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="86b69-190">win:UnicodeString</span></span>|<span data-ttu-id="86b69-191">Espace de noms de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="86b69-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="86b69-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="86b69-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="86b69-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="86b69-193">win:UnicodeString</span></span>|<span data-ttu-id="86b69-194">Nom de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="86b69-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="86b69-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="86b69-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="86b69-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="86b69-196">win:UnicodeString</span></span>|<span data-ttu-id="86b69-197">Signature de la méthode d'interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="86b69-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="86b69-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="86b69-198">ClrInstanceID</span></span>|<span data-ttu-id="86b69-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="86b69-199">win:UInt16</span></span>|<span data-ttu-id="86b69-200">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="86b69-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="86b69-201">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="86b69-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="86b69-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86b69-202">See also</span></span>

- [<span data-ttu-id="86b69-203">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="86b69-203">CLR ETW Events</span></span>](clr-etw-events.md)
