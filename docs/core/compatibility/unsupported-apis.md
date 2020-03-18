---
title: API non pris en œtté sur .NET Core
titleSuffix: ''
description: Apprenez quelles API du cadre .NET qui jettent toujours une exception sur .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: c4b94321d30cacd90d5c2ee23c258681683a6faa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092965"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="22ea9-103">API qui jettent toujours des exceptions sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="22ea9-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="22ea9-104">Les API suivantes jetteront toujours un <xref:System.PlatformNotSupportedException> noyau sur .NET sur tout ou un sous-ensemble de plates-formes.</span><span class="sxs-lookup"><span data-stu-id="22ea9-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="22ea9-105">Cet article organise les membres concernés de l’API par espace de nom.</span><span class="sxs-lookup"><span data-stu-id="22ea9-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="22ea9-106">Cet article est un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="22ea9-106">This article is a work-in-progress.</span></span> <span data-ttu-id="22ea9-107">Ce n’est pas une liste complète d’API qui jettent des exceptions sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22ea9-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="22ea9-108">Cet article n’inclut pas les implémentations d’interface explicites pour la sérialisation binaire qui jettent sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22ea9-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="22ea9-109">Pour plus d’informations, voir [la sérialisation binaire dans .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="22ea9-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="22ea9-110">Système</span><span class="sxs-lookup"><span data-stu-id="22ea9-110">System</span></span>

| <span data-ttu-id="22ea9-111">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-111">Member</span></span> | <span data-ttu-id="22ea9-112">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-113">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-114">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="22ea9-115">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="22ea9-116">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-117">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="22ea9-118">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="22ea9-119">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="22ea9-120">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-121">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-122">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="22ea9-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="22ea9-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="22ea9-124">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-124">Member</span></span> | <span data-ttu-id="22ea9-125">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-126">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-127">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-128">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="22ea9-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="22ea9-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="22ea9-130">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-130">Member</span></span> | <span data-ttu-id="22ea9-131">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-132">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-133">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-134">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="22ea9-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="22ea9-135">System.Configuration</span></span>

| <span data-ttu-id="22ea9-136">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-136">Member</span></span> | <span data-ttu-id="22ea9-137">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="22ea9-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(tous les membres)</span><span class="sxs-lookup"><span data-stu-id="22ea9-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="22ea9-139">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="22ea9-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="22ea9-140">System.Console</span></span>

| <span data-ttu-id="22ea9-141">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-141">Member</span></span> | <span data-ttu-id="22ea9-142">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="22ea9-143">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-143">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-145">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-145">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-147">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-147">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-149">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-149">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(obtenir seulement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="22ea9-151">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-152">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-153">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-154">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-154">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-155"><xref:System.Console.Title?displayProperty=nameWithType>(obtenir seulement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="22ea9-156">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-156">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-158">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-158">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-160">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-160">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-162">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-162">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-164">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="22ea9-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="22ea9-165">System.Data.Common</span></span>

| <span data-ttu-id="22ea9-166">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-166">Member</span></span> | <span data-ttu-id="22ea9-167">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="22ea9-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(jette <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="22ea9-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="22ea9-169">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="22ea9-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="22ea9-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="22ea9-171">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-171">Member</span></span> | <span data-ttu-id="22ea9-172">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="22ea9-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-174">Linux</span><span class="sxs-lookup"><span data-stu-id="22ea9-174">Linux</span></span> |
| <span data-ttu-id="22ea9-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-176">Linux</span><span class="sxs-lookup"><span data-stu-id="22ea9-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="22ea9-177">macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="22ea9-178">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-179">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="22ea9-180">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="22ea9-181">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="22ea9-182">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="22ea9-183">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-183">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-185">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-185">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(obtenir seulement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="22ea9-187">macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-187">macOS</span></span> |
| <span data-ttu-id="22ea9-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-189">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="22ea9-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="22ea9-190">System.IO</span></span>

| <span data-ttu-id="22ea9-191">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-191">Member</span></span> | <span data-ttu-id="22ea9-192">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-193">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-194">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="22ea9-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="22ea9-195">System.IO.Pipes</span></span>

| <span data-ttu-id="22ea9-196">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-196">Member</span></span> | <span data-ttu-id="22ea9-197">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="22ea9-198">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="22ea9-199">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="22ea9-200">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="22ea9-201">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-201">Linux and macOS</span></span> |
| <span data-ttu-id="22ea9-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-203">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="22ea9-204">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="22ea9-205">System.Médias</span><span class="sxs-lookup"><span data-stu-id="22ea9-205">System.Media</span></span>

| <span data-ttu-id="22ea9-206">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-206">Member</span></span> | <span data-ttu-id="22ea9-207">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-208">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="22ea9-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="22ea9-209">System.Net</span></span>

| <span data-ttu-id="22ea9-210">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-210">Member</span></span> | <span data-ttu-id="22ea9-211">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-212">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-213">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-214">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-215">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-216">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-217">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-218">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-219">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-220">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-221">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-222">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="22ea9-223">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-224">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-225">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-226">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-227">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-228">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="22ea9-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="22ea9-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="22ea9-230">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-230">Member</span></span> | <span data-ttu-id="22ea9-231">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="22ea9-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="22ea9-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="22ea9-233">System.Net.Sockets</span></span>

| <span data-ttu-id="22ea9-234">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-234">Member</span></span> | <span data-ttu-id="22ea9-235">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-236">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-237">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="22ea9-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="22ea9-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="22ea9-239">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-239">Member</span></span> | <span data-ttu-id="22ea9-240">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="22ea9-241">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="22ea9-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="22ea9-242">System.Reflection</span></span>

| <span data-ttu-id="22ea9-243">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-243">Member</span></span> | <span data-ttu-id="22ea9-244">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-245">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-246">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-247">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-248">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-249">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-250">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="22ea9-251">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="22ea9-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="22ea9-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="22ea9-253">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-253">Member</span></span> | <span data-ttu-id="22ea9-254">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="22ea9-255">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="22ea9-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="22ea9-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="22ea9-257">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-257">Member</span></span> | <span data-ttu-id="22ea9-258">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-259">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="22ea9-260">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-261">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-262">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-263">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-264">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-265">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="22ea9-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="22ea9-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="22ea9-267">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-267">Member</span></span> | <span data-ttu-id="22ea9-268">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="22ea9-269">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="22ea9-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="22ea9-270">System.Security</span></span>

| <span data-ttu-id="22ea9-271">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-271">Member</span></span> | <span data-ttu-id="22ea9-272">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="22ea9-273">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="22ea9-274">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-275">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="22ea9-276">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="22ea9-277">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="22ea9-278">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="22ea9-279">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="22ea9-280">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="22ea9-281">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="22ea9-282">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="22ea9-283">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-284">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="22ea9-285">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="22ea9-286">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="22ea9-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="22ea9-287">System.Security.Claims</span></span>

| <span data-ttu-id="22ea9-288">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-288">Member</span></span> | <span data-ttu-id="22ea9-289">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="22ea9-290">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-291">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-292">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-293">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-294">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="22ea9-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="22ea9-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="22ea9-296">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-296">Member</span></span> | <span data-ttu-id="22ea9-297">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-298">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-299">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="22ea9-300">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="22ea9-301">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="22ea9-302">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="22ea9-303">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="22ea9-304">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="22ea9-305">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="22ea9-306">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="22ea9-307">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="22ea9-308">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="22ea9-309">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="22ea9-310">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="22ea9-311">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="22ea9-312">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="22ea9-313">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-314">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-315">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-316">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-317">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="22ea9-318">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-319">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-320">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-321">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="22ea9-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-322">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-323">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="22ea9-324">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-325">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="22ea9-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="22ea9-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="22ea9-327">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-327">Member</span></span> | <span data-ttu-id="22ea9-328">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-329">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-330">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="22ea9-331">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="22ea9-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="22ea9-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="22ea9-333">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-333">Member</span></span> | <span data-ttu-id="22ea9-334">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-335">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-336">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-337">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-337">All</span></span> |
| <span data-ttu-id="22ea9-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(réglé uniquement)</span><span class="sxs-lookup"><span data-stu-id="22ea9-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="22ea9-339">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="22ea9-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="22ea9-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="22ea9-341">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-341">Member</span></span> | <span data-ttu-id="22ea9-342">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-343">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="22ea9-344">System.security.policy</span><span class="sxs-lookup"><span data-stu-id="22ea9-344">System.Security.Policy</span></span>

| <span data-ttu-id="22ea9-345">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-345">Member</span></span> | <span data-ttu-id="22ea9-346">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-347">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="22ea9-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="22ea9-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="22ea9-349">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-349">Member</span></span> | <span data-ttu-id="22ea9-350">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-351">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="22ea9-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="22ea9-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="22ea9-353">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-353">Member</span></span> | <span data-ttu-id="22ea9-354">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-355">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="22ea9-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="22ea9-356">System.Threading</span></span>

| <span data-ttu-id="22ea9-357">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-357">Member</span></span> | <span data-ttu-id="22ea9-358">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-359">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-360">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="22ea9-361">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="22ea9-362">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="22ea9-363">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="22ea9-364">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="22ea9-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="22ea9-365">System.Xml</span></span>

| <span data-ttu-id="22ea9-366">Membre</span><span class="sxs-lookup"><span data-stu-id="22ea9-366">Member</span></span> | <span data-ttu-id="22ea9-367">Plates-formes qui jettent</span><span class="sxs-lookup"><span data-stu-id="22ea9-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-368">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-369">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="22ea9-370">Tous</span><span class="sxs-lookup"><span data-stu-id="22ea9-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="22ea9-371">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22ea9-371">See also</span></span>

- [<span data-ttu-id="22ea9-372">Breaking changes for migration from .NET Framework to .NET Core</span><span class="sxs-lookup"><span data-stu-id="22ea9-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="22ea9-373">Sérialisation binaire dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="22ea9-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="22ea9-374">analyseur de portabilité .NET</span><span class="sxs-lookup"><span data-stu-id="22ea9-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
