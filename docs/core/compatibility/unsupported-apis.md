---
title: API non prises en charge sur .NET Core
titleSuffix: ''
description: Découvrez les API de la .NET Framework qui lèvent toujours une exception sur .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: 941e9149c7679afe4a888149108d0a9a28e5e7ab
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794596"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="91753-103">API qui lèvent toujours des exceptions sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="91753-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="91753-104">Les API suivantes lèvent toujours une <xref:System.PlatformNotSupportedException> sur .net Core sur tout ou partie des plateformes.</span><span class="sxs-lookup"><span data-stu-id="91753-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="91753-105">Cet article organise les membres d’API affectés par espace de noms.</span><span class="sxs-lookup"><span data-stu-id="91753-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="91753-106">Cet article est un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="91753-106">This article is a work-in-progress.</span></span> <span data-ttu-id="91753-107">Il ne s’agit pas d’une liste complète des API qui lèvent des exceptions sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91753-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="91753-108">Cet article n’inclut pas les implémentations d’interface explicites pour la sérialisation binaire qui lèvent sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91753-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="91753-109">Pour plus d’informations, consultez [sérialisation binaire dans .net Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="91753-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="91753-110">Système</span><span class="sxs-lookup"><span data-stu-id="91753-110">System</span></span>

| <span data-ttu-id="91753-111">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-111">Member</span></span> | <span data-ttu-id="91753-112">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-113">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="91753-114">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="91753-115">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="91753-116">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-117">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="91753-118">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="91753-119">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="91753-120">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-121">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="91753-122">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="91753-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="91753-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="91753-124">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-124">Member</span></span> | <span data-ttu-id="91753-125">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-126">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-127">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-128">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="91753-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="91753-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="91753-130">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-130">Member</span></span> | <span data-ttu-id="91753-131">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-132">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-133">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="91753-134">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="91753-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="91753-135">System.Configuration</span></span>

| <span data-ttu-id="91753-136">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-136">Member</span></span> | <span data-ttu-id="91753-137">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="91753-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(tous les membres)</span><span class="sxs-lookup"><span data-stu-id="91753-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="91753-139">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="91753-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="91753-140">System.Console</span></span>

| <span data-ttu-id="91753-141">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-141">Member</span></span> | <span data-ttu-id="91753-142">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="91753-143">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-143">Linux and macOS</span></span> |
| <span data-ttu-id="91753-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-145">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-145">Linux and macOS</span></span> |
| <span data-ttu-id="91753-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-147">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-147">Linux and macOS</span></span> |
| <span data-ttu-id="91753-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-149">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-149">Linux and macOS</span></span> |
| <span data-ttu-id="91753-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="91753-151">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-152">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-153">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-154">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-154">Linux and macOS</span></span> |
| <span data-ttu-id="91753-155"><xref:System.Console.Title?displayProperty=nameWithType>(obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="91753-156">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-156">Linux and macOS</span></span> |
| <span data-ttu-id="91753-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-158">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-158">Linux and macOS</span></span> |
| <span data-ttu-id="91753-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-160">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-160">Linux and macOS</span></span> |
| <span data-ttu-id="91753-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-162">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-162">Linux and macOS</span></span> |
| <span data-ttu-id="91753-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-164">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="91753-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="91753-165">System.Data.Common</span></span>

| <span data-ttu-id="91753-166">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-166">Member</span></span> | <span data-ttu-id="91753-167">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="91753-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(levée <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="91753-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="91753-169">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="91753-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="91753-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="91753-171">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-171">Member</span></span> | <span data-ttu-id="91753-172">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="91753-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-174">Linux</span><span class="sxs-lookup"><span data-stu-id="91753-174">Linux</span></span> |
| <span data-ttu-id="91753-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-176">Linux</span><span class="sxs-lookup"><span data-stu-id="91753-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="91753-177">macOS</span><span class="sxs-lookup"><span data-stu-id="91753-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="91753-178">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-179">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="91753-180">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="91753-181">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="91753-182">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="91753-183">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-183">Linux and macOS</span></span> |
| <span data-ttu-id="91753-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-185">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-185">Linux and macOS</span></span> |
| <span data-ttu-id="91753-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="91753-187">macOS</span><span class="sxs-lookup"><span data-stu-id="91753-187">macOS</span></span> |
| <span data-ttu-id="91753-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-189">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="91753-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="91753-190">System.IO</span></span>

| <span data-ttu-id="91753-191">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-191">Member</span></span> | <span data-ttu-id="91753-192">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-193">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-194">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="91753-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="91753-195">System.IO.Pipes</span></span>

| <span data-ttu-id="91753-196">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-196">Member</span></span> | <span data-ttu-id="91753-197">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="91753-198">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="91753-199">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="91753-200">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="91753-201">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-201">Linux and macOS</span></span> |
| <span data-ttu-id="91753-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-203">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="91753-204">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="91753-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="91753-205">System.Media</span></span>

| <span data-ttu-id="91753-206">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-206">Member</span></span> | <span data-ttu-id="91753-207">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-208">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="91753-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="91753-209">System.Net</span></span>

| <span data-ttu-id="91753-210">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-210">Member</span></span> | <span data-ttu-id="91753-211">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="91753-212">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="91753-213">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-214">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-215">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-216">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-217">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-218">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-219">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-220">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-221">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-222">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="91753-223">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-224">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-225">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-226">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-227">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-228">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="91753-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="91753-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="91753-230">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-230">Member</span></span> | <span data-ttu-id="91753-231">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="91753-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="91753-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="91753-233">System.Net.Sockets</span></span>

| <span data-ttu-id="91753-234">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-234">Member</span></span> | <span data-ttu-id="91753-235">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="91753-236">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="91753-237">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="91753-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="91753-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="91753-239">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-239">Member</span></span> | <span data-ttu-id="91753-240">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="91753-241">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="91753-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="91753-242">System.Reflection</span></span>

| <span data-ttu-id="91753-243">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-243">Member</span></span> | <span data-ttu-id="91753-244">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-245">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="91753-246">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-247">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="91753-248">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="91753-249">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-250">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="91753-251">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="91753-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="91753-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="91753-253">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-253">Member</span></span> | <span data-ttu-id="91753-254">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="91753-255">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="91753-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="91753-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="91753-257">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-257">Member</span></span> | <span data-ttu-id="91753-258">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="91753-259">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="91753-260">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="91753-261">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="91753-262">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="91753-263">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="91753-264">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="91753-265">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="91753-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="91753-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="91753-267">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-267">Member</span></span> | <span data-ttu-id="91753-268">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="91753-269">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="91753-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="91753-270">System.Security</span></span>

| <span data-ttu-id="91753-271">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-271">Member</span></span> | <span data-ttu-id="91753-272">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="91753-273">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="91753-274">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="91753-275">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="91753-276">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="91753-277">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="91753-278">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="91753-279">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="91753-280">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="91753-281">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="91753-282">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="91753-283">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="91753-284">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="91753-285">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="91753-286">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="91753-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="91753-287">System.Security.Claims</span></span>

| <span data-ttu-id="91753-288">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-288">Member</span></span> | <span data-ttu-id="91753-289">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="91753-290">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-291">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="91753-292">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-293">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-294">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="91753-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="91753-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="91753-296">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-296">Member</span></span> | <span data-ttu-id="91753-297">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="91753-298">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="91753-299">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="91753-300">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="91753-301">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="91753-302">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="91753-303">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="91753-304">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="91753-305">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="91753-306">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="91753-307">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="91753-308">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="91753-309">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="91753-310">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="91753-311">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="91753-312">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="91753-313">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="91753-314">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-315">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-316">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-317">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="91753-318">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="91753-319">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-320">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-321">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="91753-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-322">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-323">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="91753-324">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="91753-325">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="91753-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="91753-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="91753-327">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-327">Member</span></span> | <span data-ttu-id="91753-328">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="91753-329">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="91753-330">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="91753-331">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="91753-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="91753-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="91753-333">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-333">Member</span></span> | <span data-ttu-id="91753-334">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-335">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-336">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-337">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-337">All</span></span> |
| <span data-ttu-id="91753-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="91753-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="91753-339">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="91753-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="91753-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="91753-341">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-341">Member</span></span> | <span data-ttu-id="91753-342">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-343">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="91753-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="91753-344">System.Security.Policy</span></span>

| <span data-ttu-id="91753-345">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-345">Member</span></span> | <span data-ttu-id="91753-346">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-347">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="91753-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="91753-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="91753-349">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-349">Member</span></span> | <span data-ttu-id="91753-350">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="91753-351">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="91753-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="91753-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="91753-353">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-353">Member</span></span> | <span data-ttu-id="91753-354">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-355">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="91753-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="91753-356">System.Threading</span></span>

| <span data-ttu-id="91753-357">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-357">Member</span></span> | <span data-ttu-id="91753-358">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-359">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="91753-360">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="91753-361">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="91753-362">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="91753-363">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="91753-364">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="91753-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="91753-365">System.Xml</span></span>

| <span data-ttu-id="91753-366">Membre</span><span class="sxs-lookup"><span data-stu-id="91753-366">Member</span></span> | <span data-ttu-id="91753-367">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="91753-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="91753-368">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="91753-369">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="91753-370">Tous</span><span class="sxs-lookup"><span data-stu-id="91753-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="91753-371">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91753-371">See also</span></span>

- [<span data-ttu-id="91753-372">Dernières modifications pour la migration de .NET Framework vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="91753-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="91753-373">Sérialisation binaire dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="91753-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="91753-374">Analyseur de portabilité .NET</span><span class="sxs-lookup"><span data-stu-id="91753-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
