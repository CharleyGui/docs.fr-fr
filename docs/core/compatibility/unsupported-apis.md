---
title: API non prises en charge sur .NET Core et .NET 5 +
titleSuffix: ''
description: Découvrez les API .NET qui lèvent toujours une exception sur .NET Core et .NET 5,0 et versions ultérieures.
ms.date: 10/13/2020
ms.openlocfilehash: 51d73557a48910d9cb1c4d3cdced34dfe4d849d8
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329779"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="cde62-103">API qui lèvent toujours des exceptions sur .NET Core et .NET 5 +</span><span class="sxs-lookup"><span data-stu-id="cde62-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="cde62-104">Les API suivantes lèvent toujours une <xref:System.PlatformNotSupportedException> sur .net 5,0 et versions ultérieures (y compris toutes les versions de .net Core) sur l’ensemble ou sur un sous-ensemble de plateformes.</span><span class="sxs-lookup"><span data-stu-id="cde62-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="cde62-105">Cet article organise les API affectées par espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cde62-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="cde62-106">Cet article est un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="cde62-106">This article is a work-in-progress.</span></span> <span data-ttu-id="cde62-107">Il ne s’agit pas d’une liste complète des API qui lèvent des exceptions sur .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="cde62-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="cde62-108">Cet article n’inclut pas les implémentations d’interface explicites pour la sérialisation binaire qui lèvent sur .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="cde62-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="cde62-109">Pour plus d’informations, consultez [sérialisation binaire dans .net Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="cde62-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="cde62-110">Système</span><span class="sxs-lookup"><span data-stu-id="cde62-110">System</span></span>

| <span data-ttu-id="cde62-111">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-111">Member</span></span> | <span data-ttu-id="cde62-112">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-113">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="cde62-114">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="cde62-115">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="cde62-116">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-117">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="cde62-118">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="cde62-119">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="cde62-120">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-121">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="cde62-122">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="cde62-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="cde62-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="cde62-124">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-124">Member</span></span> | <span data-ttu-id="cde62-125">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-126">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-127">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-128">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="cde62-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="cde62-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="cde62-130">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-130">Member</span></span> | <span data-ttu-id="cde62-131">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-132">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-133">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="cde62-134">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="cde62-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="cde62-135">System.Configuration</span></span>

| <span data-ttu-id="cde62-136">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-136">Member</span></span> | <span data-ttu-id="cde62-137">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="cde62-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tous les membres)</span><span class="sxs-lookup"><span data-stu-id="cde62-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="cde62-139">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="cde62-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="cde62-140">System.Console</span></span>

| <span data-ttu-id="cde62-141">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-141">Member</span></span> | <span data-ttu-id="cde62-142">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="cde62-143">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-143">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-145">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-145">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-147">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-147">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-149">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-149">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="cde62-151">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-152">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-153">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-154">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-154">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-155"><xref:System.Console.Title?displayProperty=nameWithType> (obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="cde62-156">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-156">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-158">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-158">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-160">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-160">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-162">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-162">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-164">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="cde62-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="cde62-165">System.Data.Common</span></span>

| <span data-ttu-id="cde62-166">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-166">Member</span></span> | <span data-ttu-id="cde62-167">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="cde62-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (levée <xref:System.NotSupportedException> )</span><span class="sxs-lookup"><span data-stu-id="cde62-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="cde62-169">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="cde62-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="cde62-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="cde62-171">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-171">Member</span></span> | <span data-ttu-id="cde62-172">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="cde62-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-174">Linux</span><span class="sxs-lookup"><span data-stu-id="cde62-174">Linux</span></span> |
| <span data-ttu-id="cde62-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-176">Linux</span><span class="sxs-lookup"><span data-stu-id="cde62-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="cde62-177">macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="cde62-178">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-179">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="cde62-180">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="cde62-181">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="cde62-182">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="cde62-183">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-183">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-185">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-185">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="cde62-187">macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-187">macOS</span></span> |
| <span data-ttu-id="cde62-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-189">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="cde62-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="cde62-190">System.IO</span></span>

| <span data-ttu-id="cde62-191">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-191">Member</span></span> | <span data-ttu-id="cde62-192">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-193">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-194">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="cde62-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="cde62-195">System.IO.Pipes</span></span>

| <span data-ttu-id="cde62-196">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-196">Member</span></span> | <span data-ttu-id="cde62-197">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="cde62-198">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="cde62-199">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="cde62-200">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="cde62-201">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-201">Linux and macOS</span></span> |
| <span data-ttu-id="cde62-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-203">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="cde62-204">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="cde62-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="cde62-205">System.Media</span></span>

| <span data-ttu-id="cde62-206">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-206">Member</span></span> | <span data-ttu-id="cde62-207">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-208">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="cde62-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="cde62-209">System.Net</span></span>

| <span data-ttu-id="cde62-210">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-210">Member</span></span> | <span data-ttu-id="cde62-211">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="cde62-212">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="cde62-213">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-214">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-215">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-216">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-217">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-218">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-219">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-220">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-221">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-222">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="cde62-223">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-224">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-225">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-226">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-227">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-228">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="cde62-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="cde62-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="cde62-230">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-230">Member</span></span> | <span data-ttu-id="cde62-231">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="cde62-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="cde62-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="cde62-233">System.Net.Sockets</span></span>

| <span data-ttu-id="cde62-234">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-234">Member</span></span> | <span data-ttu-id="cde62-235">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="cde62-236">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="cde62-237">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="cde62-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="cde62-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="cde62-239">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-239">Member</span></span> | <span data-ttu-id="cde62-240">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="cde62-241">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="cde62-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="cde62-242">System.Reflection</span></span>

| <span data-ttu-id="cde62-243">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-243">Member</span></span> | <span data-ttu-id="cde62-244">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-245">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cde62-246">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-247">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="cde62-248">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="cde62-249">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-250">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="cde62-251">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="cde62-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="cde62-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="cde62-253">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-253">Member</span></span> | <span data-ttu-id="cde62-254">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="cde62-255">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="cde62-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="cde62-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="cde62-257">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-257">Member</span></span> | <span data-ttu-id="cde62-258">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="cde62-259">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="cde62-260">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="cde62-261">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="cde62-262">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cde62-263">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="cde62-264">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="cde62-265">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="cde62-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="cde62-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="cde62-267">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-267">Member</span></span> | <span data-ttu-id="cde62-268">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="cde62-269">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="cde62-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="cde62-270">System.Security</span></span>

| <span data-ttu-id="cde62-271">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-271">Member</span></span> | <span data-ttu-id="cde62-272">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="cde62-273">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="cde62-274">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="cde62-275">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="cde62-276">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="cde62-277">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="cde62-278">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="cde62-279">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="cde62-280">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="cde62-281">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="cde62-282">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="cde62-283">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="cde62-284">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="cde62-285">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="cde62-286">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="cde62-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="cde62-287">System.Security.Claims</span></span>

| <span data-ttu-id="cde62-288">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-288">Member</span></span> | <span data-ttu-id="cde62-289">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-290">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-291">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="cde62-292">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-293">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-294">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="cde62-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="cde62-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="cde62-296">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-296">Member</span></span> | <span data-ttu-id="cde62-297">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cde62-298">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="cde62-299">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="cde62-300">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="cde62-301">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="cde62-302">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="cde62-303">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="cde62-304">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="cde62-305">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="cde62-306">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="cde62-307">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="cde62-308">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="cde62-309">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="cde62-310">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="cde62-311">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="cde62-312">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="cde62-313">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cde62-314">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-315">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-316">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-317">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="cde62-318">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cde62-319">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-320">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-321">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="cde62-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-322">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-323">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="cde62-324">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cde62-325">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="cde62-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="cde62-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="cde62-327">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-327">Member</span></span> | <span data-ttu-id="cde62-328">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="cde62-329">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="cde62-330">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="cde62-331">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="cde62-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="cde62-332">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-332">Member</span></span> | <span data-ttu-id="cde62-333">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-334">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-335">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-336">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-336">All</span></span> |
| <span data-ttu-id="cde62-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="cde62-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cde62-338">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="cde62-339">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="cde62-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="cde62-340">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-340">Member</span></span> | <span data-ttu-id="cde62-341">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-342">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="cde62-343">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="cde62-343">System.Security.Policy</span></span>

| <span data-ttu-id="cde62-344">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-344">Member</span></span> | <span data-ttu-id="cde62-345">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-346">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="cde62-347">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="cde62-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="cde62-348">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-348">Member</span></span> | <span data-ttu-id="cde62-349">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="cde62-350">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="cde62-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="cde62-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="cde62-352">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-352">Member</span></span> | <span data-ttu-id="cde62-353">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-354">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="cde62-355">System.Threading</span><span class="sxs-lookup"><span data-stu-id="cde62-355">System.Threading</span></span>

| <span data-ttu-id="cde62-356">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-356">Member</span></span> | <span data-ttu-id="cde62-357">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-358">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cde62-359">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="cde62-360">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="cde62-361">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="cde62-362">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="cde62-363">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="cde62-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="cde62-364">System.Xml</span></span>

| <span data-ttu-id="cde62-365">Membre</span><span class="sxs-lookup"><span data-stu-id="cde62-365">Member</span></span> | <span data-ttu-id="cde62-366">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="cde62-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="cde62-367">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="cde62-368">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="cde62-369">Tous</span><span class="sxs-lookup"><span data-stu-id="cde62-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="cde62-370">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cde62-370">See also</span></span>

- [<span data-ttu-id="cde62-371">Dernières modifications pour la migration de .NET Framework vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="cde62-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="cde62-372">Sérialisation binaire dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="cde62-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="cde62-373">Analyseur de portabilité .NET</span><span class="sxs-lookup"><span data-stu-id="cde62-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
