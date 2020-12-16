---
title: API non prises en charge sur .NET Core et .NET 5 +
titleSuffix: ''
description: Découvrez les API .NET qui lèvent toujours une exception sur .NET Core et .NET 5,0 et versions ultérieures.
ms.date: 10/13/2020
ms.openlocfilehash: 1bd41192d0d6752d2b659da9fb6387dac321b2c3
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593264"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="01f83-103">API qui lèvent toujours des exceptions sur .NET Core et .NET 5 +</span><span class="sxs-lookup"><span data-stu-id="01f83-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="01f83-104">Les API suivantes lèvent toujours une <xref:System.PlatformNotSupportedException> sur .net 5,0 et versions ultérieures (y compris toutes les versions de .net Core) sur l’ensemble ou sur un sous-ensemble de plateformes.</span><span class="sxs-lookup"><span data-stu-id="01f83-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="01f83-105">Cet article organise les API affectées par espace de noms.</span><span class="sxs-lookup"><span data-stu-id="01f83-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="01f83-106">Cet article est un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="01f83-106">This article is a work-in-progress.</span></span> <span data-ttu-id="01f83-107">Il ne s’agit pas d’une liste complète des API qui lèvent des exceptions sur .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="01f83-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="01f83-108">Cet article n’inclut pas les implémentations d’interface explicites pour la sérialisation binaire qui lèvent sur .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="01f83-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="01f83-109">Pour plus d’informations, consultez [sérialisation binaire dans .net Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="01f83-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="01f83-110">Système</span><span class="sxs-lookup"><span data-stu-id="01f83-110">System</span></span>

| <span data-ttu-id="01f83-111">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-111">Member</span></span> | <span data-ttu-id="01f83-112">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-113">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="01f83-114">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="01f83-115">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="01f83-116">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-117">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="01f83-118">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="01f83-119">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="01f83-120">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-121">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="01f83-122">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="01f83-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="01f83-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="01f83-124">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-124">Member</span></span> | <span data-ttu-id="01f83-125">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-126">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-127">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-128">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="01f83-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="01f83-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="01f83-130">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-130">Member</span></span> | <span data-ttu-id="01f83-131">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-132">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-133">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="01f83-134">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="01f83-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="01f83-135">System.Configuration</span></span>

| <span data-ttu-id="01f83-136">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-136">Member</span></span> | <span data-ttu-id="01f83-137">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="01f83-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tous les membres)</span><span class="sxs-lookup"><span data-stu-id="01f83-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="01f83-139">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="01f83-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="01f83-140">System.Console</span></span>

| <span data-ttu-id="01f83-141">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-141">Member</span></span> | <span data-ttu-id="01f83-142">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="01f83-143">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-143">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-145">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-145">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-147">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-147">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-149">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-149">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="01f83-151">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-152">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-153">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-154">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-154">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-155"><xref:System.Console.Title?displayProperty=nameWithType> (obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="01f83-156">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-156">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-158">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-158">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-160">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-160">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-162">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-162">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-164">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="01f83-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="01f83-165">System.Data.Common</span></span>

| <span data-ttu-id="01f83-166">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-166">Member</span></span> | <span data-ttu-id="01f83-167">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="01f83-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (levée <xref:System.NotSupportedException> )</span><span class="sxs-lookup"><span data-stu-id="01f83-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="01f83-169">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="01f83-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="01f83-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="01f83-171">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-171">Member</span></span> | <span data-ttu-id="01f83-172">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="01f83-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-174">Linux</span><span class="sxs-lookup"><span data-stu-id="01f83-174">Linux</span></span> |
| <span data-ttu-id="01f83-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-176">Linux</span><span class="sxs-lookup"><span data-stu-id="01f83-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="01f83-177">macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="01f83-178">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="01f83-179">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="01f83-180">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="01f83-181">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="01f83-182">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="01f83-183">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-183">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="01f83-184">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-184">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-186">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-186">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="01f83-188">macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-188">macOS</span></span> |
| <span data-ttu-id="01f83-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-190">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-190">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="01f83-191">System.IO</span><span class="sxs-lookup"><span data-stu-id="01f83-191">System.IO</span></span>

| <span data-ttu-id="01f83-192">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-192">Member</span></span> | <span data-ttu-id="01f83-193">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-193">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-194">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-194">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-195">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-195">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="01f83-196">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="01f83-196">System.IO.Pipes</span></span>

| <span data-ttu-id="01f83-197">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-197">Member</span></span> | <span data-ttu-id="01f83-198">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-198">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="01f83-199">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="01f83-200">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="01f83-201">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-201">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="01f83-202">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-202">Linux and macOS</span></span> |
| <span data-ttu-id="01f83-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-204">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-204">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="01f83-205">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-205">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="01f83-206">System. Media</span><span class="sxs-lookup"><span data-stu-id="01f83-206">System.Media</span></span>

| <span data-ttu-id="01f83-207">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-207">Member</span></span> | <span data-ttu-id="01f83-208">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-208">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-209">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-209">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="01f83-210">System.Net</span><span class="sxs-lookup"><span data-stu-id="01f83-210">System.Net</span></span>

| <span data-ttu-id="01f83-211">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-211">Member</span></span> | <span data-ttu-id="01f83-212">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-212">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="01f83-213">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-213">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="01f83-214">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-214">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-215">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-215">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-216">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-216">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-217">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-217">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-218">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-219">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-219">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-220">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-221">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-221">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-222">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-222">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-223">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-223">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="01f83-224">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-224">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-225">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-225">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-226">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-226">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-227">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-227">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-228">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-228">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-229">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-229">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="01f83-230">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="01f83-230">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="01f83-231">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-231">Member</span></span> | <span data-ttu-id="01f83-232">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-232">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-233">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="01f83-233">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="01f83-234">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="01f83-234">System.Net.Sockets</span></span>

| <span data-ttu-id="01f83-235">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-235">Member</span></span> | <span data-ttu-id="01f83-236">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-236">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="01f83-237">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-237">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="01f83-238">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-238">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="01f83-239">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="01f83-239">System.Net.WebSockets</span></span>

| <span data-ttu-id="01f83-240">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-240">Member</span></span> | <span data-ttu-id="01f83-241">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-241">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="01f83-242">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-242">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="01f83-243">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="01f83-243">System.Reflection</span></span>

| <span data-ttu-id="01f83-244">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-244">Member</span></span> | <span data-ttu-id="01f83-245">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-245">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-246">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-246">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="01f83-247">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-248">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-248">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="01f83-249">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="01f83-250">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-251">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-251">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="01f83-252">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-252">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="01f83-253">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="01f83-253">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="01f83-254">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-254">Member</span></span> | <span data-ttu-id="01f83-255">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-255">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="01f83-256">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-256">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="01f83-257">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="01f83-257">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="01f83-258">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-258">Member</span></span> | <span data-ttu-id="01f83-259">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-259">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="01f83-260">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="01f83-261">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="01f83-262">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-262">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="01f83-263">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-263">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="01f83-264">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="01f83-265">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-265">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="01f83-266">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-266">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="01f83-267">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="01f83-267">System.Runtime.Serialization</span></span>

| <span data-ttu-id="01f83-268">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-268">Member</span></span> | <span data-ttu-id="01f83-269">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-269">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="01f83-270">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-270">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="01f83-271">System.Security</span><span class="sxs-lookup"><span data-stu-id="01f83-271">System.Security</span></span>

| <span data-ttu-id="01f83-272">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-272">Member</span></span> | <span data-ttu-id="01f83-273">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-273">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="01f83-274">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-274">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="01f83-275">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-275">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="01f83-276">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-276">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="01f83-277">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-277">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="01f83-278">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-278">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="01f83-279">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-279">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="01f83-280">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-280">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="01f83-281">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="01f83-282">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-282">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="01f83-283">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-283">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="01f83-284">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-284">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="01f83-285">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="01f83-286">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-286">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="01f83-287">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-287">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="01f83-288">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="01f83-288">System.Security.Claims</span></span>

| <span data-ttu-id="01f83-289">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-289">Member</span></span> | <span data-ttu-id="01f83-290">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-290">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-291">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-292">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="01f83-293">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-294">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-294">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-295">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-295">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="01f83-296">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="01f83-296">System.Security.Cryptography</span></span>

| <span data-ttu-id="01f83-297">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-297">Member</span></span> | <span data-ttu-id="01f83-298">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-298">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="01f83-299">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-299">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="01f83-300">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="01f83-301">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="01f83-302">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="01f83-303">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="01f83-304">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="01f83-305">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="01f83-306">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="01f83-307">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="01f83-308">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="01f83-309">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="01f83-310">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="01f83-311">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="01f83-312">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-312">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="01f83-313">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="01f83-314">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="01f83-315">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-316">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-317">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-317">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-318">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="01f83-319">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-319">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="01f83-320">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-320">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-321">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-322">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="01f83-322">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-323">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-323">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-324">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="01f83-325">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-325">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="01f83-326">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-326">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="01f83-327">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="01f83-327">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="01f83-328">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-328">Member</span></span> | <span data-ttu-id="01f83-329">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-329">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="01f83-330">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="01f83-331">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="01f83-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="01f83-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="01f83-333">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-333">Member</span></span> | <span data-ttu-id="01f83-334">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-335">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-336">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-337">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-337">All</span></span> |
| <span data-ttu-id="01f83-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="01f83-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="01f83-339">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="01f83-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="01f83-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="01f83-341">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-341">Member</span></span> | <span data-ttu-id="01f83-342">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-343">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="01f83-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="01f83-344">System.Security.Policy</span></span>

| <span data-ttu-id="01f83-345">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-345">Member</span></span> | <span data-ttu-id="01f83-346">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-347">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="01f83-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="01f83-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="01f83-349">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-349">Member</span></span> | <span data-ttu-id="01f83-350">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="01f83-351">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="01f83-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="01f83-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="01f83-353">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-353">Member</span></span> | <span data-ttu-id="01f83-354">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-355">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="01f83-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="01f83-356">System.Threading</span></span>

| <span data-ttu-id="01f83-357">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-357">Member</span></span> | <span data-ttu-id="01f83-358">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-359">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="01f83-360">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="01f83-361">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="01f83-362">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="01f83-363">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="01f83-364">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="01f83-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="01f83-365">System.Xml</span></span>

| <span data-ttu-id="01f83-366">Membre</span><span class="sxs-lookup"><span data-stu-id="01f83-366">Member</span></span> | <span data-ttu-id="01f83-367">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="01f83-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="01f83-368">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="01f83-369">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="01f83-370">Tous</span><span class="sxs-lookup"><span data-stu-id="01f83-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="01f83-371">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01f83-371">See also</span></span>

- [<span data-ttu-id="01f83-372">Dernières modifications pour la migration de .NET Framework vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="01f83-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="01f83-373">Sérialisation binaire dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="01f83-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="01f83-374">Analyseur de portabilité .NET</span><span class="sxs-lookup"><span data-stu-id="01f83-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
