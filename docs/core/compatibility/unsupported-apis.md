---
title: API non prises en charge sur .NET Core
description: Découvrez les API de la .NET Framework qui lèvent toujours une exception sur .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: f27aeca31226a95dacf100813762eedb56876fbd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936973"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="64b0a-103">API qui lèvent toujours des exceptions sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="64b0a-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="64b0a-104">Les API suivantes lèvent toujours une <xref:System.PlatformNotSupportedException> sur .NET Core sur tout ou partie des plateformes.</span><span class="sxs-lookup"><span data-stu-id="64b0a-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="64b0a-105">Cet article organise les membres d’API affectés par espace de noms.</span><span class="sxs-lookup"><span data-stu-id="64b0a-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="64b0a-106">Cet article est un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="64b0a-106">This article is a work-in-progress.</span></span> <span data-ttu-id="64b0a-107">Il ne s’agit pas d’une liste complète des API qui lèvent des exceptions sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="64b0a-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="64b0a-108">Cet article n’inclut pas les implémentations d’interface explicites pour la sérialisation binaire qui lèvent sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="64b0a-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="64b0a-109">Pour plus d’informations, consultez [sérialisation binaire dans .net Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="64b0a-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="64b0a-110">System</span><span class="sxs-lookup"><span data-stu-id="64b0a-110">System</span></span>

| <span data-ttu-id="64b0a-111">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-111">Member</span></span> | <span data-ttu-id="64b0a-112">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-113">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-114">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="64b0a-115">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="64b0a-116">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-117">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="64b0a-118">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="64b0a-119">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="64b0a-120">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-121">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-122">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="64b0a-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="64b0a-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="64b0a-124">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-124">Member</span></span> | <span data-ttu-id="64b0a-125">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-126">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-127">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-128">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="64b0a-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="64b0a-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="64b0a-130">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-130">Member</span></span> | <span data-ttu-id="64b0a-131">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-132">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-133">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-134">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="64b0a-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="64b0a-135">System.Configuration</span></span>

| <span data-ttu-id="64b0a-136">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-136">Member</span></span> | <span data-ttu-id="64b0a-137">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="64b0a-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tous les membres)</span><span class="sxs-lookup"><span data-stu-id="64b0a-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="64b0a-139">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="64b0a-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="64b0a-140">System.Console</span></span>

| <span data-ttu-id="64b0a-141">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-141">Member</span></span> | <span data-ttu-id="64b0a-142">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="64b0a-143">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-143">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-145">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-145">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-147">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-147">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-149">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-149">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (récupération uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="64b0a-151">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-152">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-153">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-154">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-154">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-155"><xref:System.Console.Title?displayProperty=nameWithType> (récupération uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="64b0a-156">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-156">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-158">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-158">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-160">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-160">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-162">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-162">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-164">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="64b0a-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="64b0a-165">System.Data.Common</span></span>

| <span data-ttu-id="64b0a-166">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-166">Member</span></span> | <span data-ttu-id="64b0a-167">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="64b0a-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (lève <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="64b0a-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="64b0a-169">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="64b0a-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="64b0a-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="64b0a-171">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-171">Member</span></span> | <span data-ttu-id="64b0a-172">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="64b0a-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-174">Linux</span><span class="sxs-lookup"><span data-stu-id="64b0a-174">Linux</span></span> |
| <span data-ttu-id="64b0a-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-176">Linux</span><span class="sxs-lookup"><span data-stu-id="64b0a-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="64b0a-177">macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="64b0a-178">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-179">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="64b0a-180">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="64b0a-181">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="64b0a-182">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="64b0a-183">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-183">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-185">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-185">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (récupération uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="64b0a-187">macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-187">macOS</span></span> |
| <span data-ttu-id="64b0a-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-189">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="64b0a-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="64b0a-190">System.IO</span></span>

| <span data-ttu-id="64b0a-191">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-191">Member</span></span> | <span data-ttu-id="64b0a-192">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-193">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-194">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="64b0a-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="64b0a-195">System.IO.Pipes</span></span>

| <span data-ttu-id="64b0a-196">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-196">Member</span></span> | <span data-ttu-id="64b0a-197">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="64b0a-198">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="64b0a-199">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="64b0a-200">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="64b0a-201">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-201">Linux and macOS</span></span> |
| <span data-ttu-id="64b0a-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-203">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="64b0a-204">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="64b0a-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="64b0a-205">System.Media</span></span>

| <span data-ttu-id="64b0a-206">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-206">Member</span></span> | <span data-ttu-id="64b0a-207">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-208">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="64b0a-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="64b0a-209">System.Net</span></span>

| <span data-ttu-id="64b0a-210">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-210">Member</span></span> | <span data-ttu-id="64b0a-211">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-212">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-213">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-214">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-215">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-216">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-217">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-218">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-219">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-220">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-221">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-222">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="64b0a-223">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-224">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-225">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-226">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-227">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-228">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="64b0a-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="64b0a-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="64b0a-230">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-230">Member</span></span> | <span data-ttu-id="64b0a-231">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="64b0a-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="64b0a-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="64b0a-233">System.Net.Sockets</span></span>

| <span data-ttu-id="64b0a-234">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-234">Member</span></span> | <span data-ttu-id="64b0a-235">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-236">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-236">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="64b0a-237">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="64b0a-237">System.Net.WebSockets</span></span>

| <span data-ttu-id="64b0a-238">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-238">Member</span></span> | <span data-ttu-id="64b0a-239">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-239">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="64b0a-240">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-240">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="64b0a-241">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="64b0a-241">System.Reflection</span></span>

| <span data-ttu-id="64b0a-242">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-242">Member</span></span> | <span data-ttu-id="64b0a-243">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-243">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-244">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-244">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-245">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-245">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-246">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-247">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-247">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-248">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-249">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="64b0a-250">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-250">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="64b0a-251">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="64b0a-251">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="64b0a-252">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-252">Member</span></span> | <span data-ttu-id="64b0a-253">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-253">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="64b0a-254">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-254">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="64b0a-255">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="64b0a-255">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="64b0a-256">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-256">Member</span></span> | <span data-ttu-id="64b0a-257">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-257">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-258">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-258">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="64b0a-259">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-260">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-261">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-261">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-262">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-262">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-263">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-264">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-264">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="64b0a-265">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="64b0a-265">System.Runtime.Serialization</span></span>

| <span data-ttu-id="64b0a-266">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-266">Member</span></span> | <span data-ttu-id="64b0a-267">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-267">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="64b0a-268">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-268">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="64b0a-269">System.Security</span><span class="sxs-lookup"><span data-stu-id="64b0a-269">System.Security</span></span>

| <span data-ttu-id="64b0a-270">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-270">Member</span></span> | <span data-ttu-id="64b0a-271">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-271">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="64b0a-272">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-272">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="64b0a-273">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-273">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-274">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-274">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="64b0a-275">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-275">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="64b0a-276">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-276">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="64b0a-277">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-277">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="64b0a-278">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-278">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="64b0a-279">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-279">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="64b0a-280">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="64b0a-281">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-281">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="64b0a-282">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-282">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-283">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-283">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="64b0a-284">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="64b0a-285">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-285">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="64b0a-286">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="64b0a-286">System.Security.Claims</span></span>

| <span data-ttu-id="64b0a-287">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-287">Member</span></span> | <span data-ttu-id="64b0a-288">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-288">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="64b0a-289">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-289">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-290">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-291">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-292">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-293">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-293">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="64b0a-294">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="64b0a-294">System.Security.Cryptography</span></span>

| <span data-ttu-id="64b0a-295">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-295">Member</span></span> | <span data-ttu-id="64b0a-296">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-296">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-297">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-297">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-298">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-298">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="64b0a-299">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="64b0a-300">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="64b0a-301">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="64b0a-302">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="64b0a-303">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="64b0a-304">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="64b0a-305">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="64b0a-306">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="64b0a-307">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="64b0a-308">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="64b0a-309">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="64b0a-310">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="64b0a-311">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-311">All</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-312">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="64b0a-313">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-314">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-315">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-316">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-317">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="64b0a-318">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-319">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-320">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-321">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="64b0a-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-322">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-323">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="64b0a-324">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-325">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="64b0a-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="64b0a-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="64b0a-327">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-327">Member</span></span> | <span data-ttu-id="64b0a-328">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-329">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-330">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="64b0a-331">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="64b0a-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="64b0a-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="64b0a-333">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-333">Member</span></span> | <span data-ttu-id="64b0a-334">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-335">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-336">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-337">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-337">All</span></span> |
| <span data-ttu-id="64b0a-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="64b0a-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="64b0a-339">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="64b0a-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="64b0a-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="64b0a-341">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-341">Member</span></span> | <span data-ttu-id="64b0a-342">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-343">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="64b0a-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="64b0a-344">System.Security.Policy</span></span>

| <span data-ttu-id="64b0a-345">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-345">Member</span></span> | <span data-ttu-id="64b0a-346">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-347">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="64b0a-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="64b0a-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="64b0a-349">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-349">Member</span></span> | <span data-ttu-id="64b0a-350">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-351">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="64b0a-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="64b0a-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="64b0a-353">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-353">Member</span></span> | <span data-ttu-id="64b0a-354">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-355">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="64b0a-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="64b0a-356">System.Threading</span></span>

| <span data-ttu-id="64b0a-357">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-357">Member</span></span> | <span data-ttu-id="64b0a-358">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-359">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-360">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="64b0a-361">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="64b0a-362">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="64b0a-363">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="64b0a-364">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="64b0a-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="64b0a-365">System.Xml</span></span>

| <span data-ttu-id="64b0a-366">Member</span><span class="sxs-lookup"><span data-stu-id="64b0a-366">Member</span></span> | <span data-ttu-id="64b0a-367">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="64b0a-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-368">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-369">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="64b0a-370">Toutes les</span><span class="sxs-lookup"><span data-stu-id="64b0a-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="64b0a-371">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64b0a-371">See also</span></span>

- [<span data-ttu-id="64b0a-372">Dernières modifications pour la migration de .NET Framework vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="64b0a-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="64b0a-373">Sérialisation binaire dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="64b0a-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="64b0a-374">Analyseur de portabilité .NET</span><span class="sxs-lookup"><span data-stu-id="64b0a-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
