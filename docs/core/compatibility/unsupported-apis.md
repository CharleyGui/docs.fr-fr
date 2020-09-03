---
title: API non prises en charge sur .NET Core
titleSuffix: ''
description: Découvrez les API de la .NET Framework qui lèvent toujours une exception sur .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: 94f334d7e4b7daf407f489ba274172ced9eefa81
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414433"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="2c909-103">API qui lèvent toujours des exceptions sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c909-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="2c909-104">Les API suivantes lèvent toujours une <xref:System.PlatformNotSupportedException> sur .net Core sur tout ou partie des plateformes.</span><span class="sxs-lookup"><span data-stu-id="2c909-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="2c909-105">Cet article organise les membres d’API affectés par espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2c909-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="2c909-106">Cet article est un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="2c909-106">This article is a work-in-progress.</span></span> <span data-ttu-id="2c909-107">Il ne s’agit pas d’une liste complète des API qui lèvent des exceptions sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2c909-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="2c909-108">Cet article n’inclut pas les implémentations d’interface explicites pour la sérialisation binaire qui lèvent sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2c909-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="2c909-109">Pour plus d’informations, consultez [sérialisation binaire dans .net Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="2c909-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="2c909-110">Système</span><span class="sxs-lookup"><span data-stu-id="2c909-110">System</span></span>

| <span data-ttu-id="2c909-111">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-111">Member</span></span> | <span data-ttu-id="2c909-112">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-113">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="2c909-114">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="2c909-115">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="2c909-116">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-117">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="2c909-118">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="2c909-119">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="2c909-120">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-121">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="2c909-122">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="2c909-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="2c909-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="2c909-124">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-124">Member</span></span> | <span data-ttu-id="2c909-125">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-126">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-127">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-128">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="2c909-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="2c909-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="2c909-130">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-130">Member</span></span> | <span data-ttu-id="2c909-131">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-132">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-133">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2c909-134">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="2c909-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="2c909-135">System.Configuration</span></span>

| <span data-ttu-id="2c909-136">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-136">Member</span></span> | <span data-ttu-id="2c909-137">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="2c909-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tous les membres)</span><span class="sxs-lookup"><span data-stu-id="2c909-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="2c909-139">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="2c909-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="2c909-140">System.Console</span></span>

| <span data-ttu-id="2c909-141">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-141">Member</span></span> | <span data-ttu-id="2c909-142">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="2c909-143">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-143">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-145">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-145">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-147">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-147">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-149">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-149">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="2c909-151">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-152">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-153">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-154">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-154">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-155"><xref:System.Console.Title?displayProperty=nameWithType> (obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="2c909-156">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-156">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-158">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-158">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-160">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-160">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-162">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-162">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-164">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="2c909-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="2c909-165">System.Data.Common</span></span>

| <span data-ttu-id="2c909-166">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-166">Member</span></span> | <span data-ttu-id="2c909-167">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="2c909-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (levée <xref:System.NotSupportedException> )</span><span class="sxs-lookup"><span data-stu-id="2c909-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="2c909-169">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="2c909-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="2c909-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="2c909-171">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-171">Member</span></span> | <span data-ttu-id="2c909-172">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="2c909-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-174">Linux</span><span class="sxs-lookup"><span data-stu-id="2c909-174">Linux</span></span> |
| <span data-ttu-id="2c909-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-176">Linux</span><span class="sxs-lookup"><span data-stu-id="2c909-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="2c909-177">macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="2c909-178">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-179">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="2c909-180">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="2c909-181">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="2c909-182">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="2c909-183">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-183">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-185">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-185">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (obtient uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="2c909-187">macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-187">macOS</span></span> |
| <span data-ttu-id="2c909-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-189">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="2c909-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="2c909-190">System.IO</span></span>

| <span data-ttu-id="2c909-191">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-191">Member</span></span> | <span data-ttu-id="2c909-192">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-193">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-194">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="2c909-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="2c909-195">System.IO.Pipes</span></span>

| <span data-ttu-id="2c909-196">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-196">Member</span></span> | <span data-ttu-id="2c909-197">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="2c909-198">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="2c909-199">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="2c909-200">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="2c909-201">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-201">Linux and macOS</span></span> |
| <span data-ttu-id="2c909-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-203">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="2c909-204">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="2c909-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="2c909-205">System.Media</span></span>

| <span data-ttu-id="2c909-206">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-206">Member</span></span> | <span data-ttu-id="2c909-207">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-208">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="2c909-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="2c909-209">System.Net</span></span>

| <span data-ttu-id="2c909-210">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-210">Member</span></span> | <span data-ttu-id="2c909-211">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="2c909-212">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="2c909-213">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-214">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-215">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-216">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-217">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-218">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-219">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-220">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-221">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-222">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="2c909-223">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-224">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-225">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-226">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-227">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-228">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="2c909-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="2c909-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="2c909-230">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-230">Member</span></span> | <span data-ttu-id="2c909-231">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="2c909-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="2c909-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="2c909-233">System.Net.Sockets</span></span>

| <span data-ttu-id="2c909-234">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-234">Member</span></span> | <span data-ttu-id="2c909-235">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="2c909-236">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="2c909-237">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="2c909-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="2c909-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="2c909-239">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-239">Member</span></span> | <span data-ttu-id="2c909-240">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="2c909-241">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="2c909-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="2c909-242">System.Reflection</span></span>

| <span data-ttu-id="2c909-243">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-243">Member</span></span> | <span data-ttu-id="2c909-244">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-245">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2c909-246">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-247">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2c909-248">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="2c909-249">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-250">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="2c909-251">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="2c909-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="2c909-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="2c909-253">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-253">Member</span></span> | <span data-ttu-id="2c909-254">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="2c909-255">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="2c909-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="2c909-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="2c909-257">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-257">Member</span></span> | <span data-ttu-id="2c909-258">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2c909-259">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="2c909-260">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="2c909-261">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="2c909-262">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2c909-263">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="2c909-264">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="2c909-265">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="2c909-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="2c909-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="2c909-267">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-267">Member</span></span> | <span data-ttu-id="2c909-268">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="2c909-269">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="2c909-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="2c909-270">System.Security</span></span>

| <span data-ttu-id="2c909-271">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-271">Member</span></span> | <span data-ttu-id="2c909-272">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="2c909-273">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="2c909-274">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="2c909-275">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="2c909-276">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="2c909-277">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="2c909-278">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="2c909-279">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="2c909-280">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="2c909-281">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="2c909-282">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="2c909-283">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2c909-284">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="2c909-285">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="2c909-286">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="2c909-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="2c909-287">System.Security.Claims</span></span>

| <span data-ttu-id="2c909-288">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-288">Member</span></span> | <span data-ttu-id="2c909-289">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="2c909-290">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-291">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="2c909-292">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-293">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-294">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="2c909-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="2c909-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="2c909-296">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-296">Member</span></span> | <span data-ttu-id="2c909-297">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2c909-298">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="2c909-299">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="2c909-300">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="2c909-301">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="2c909-302">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="2c909-303">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="2c909-304">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="2c909-305">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="2c909-306">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="2c909-307">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="2c909-308">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="2c909-309">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="2c909-310">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="2c909-311">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="2c909-312">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="2c909-313">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2c909-314">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-315">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-316">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-317">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="2c909-318">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2c909-319">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-320">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-321">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="2c909-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-322">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-323">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="2c909-324">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2c909-325">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="2c909-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="2c909-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="2c909-327">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-327">Member</span></span> | <span data-ttu-id="2c909-328">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="2c909-329">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="2c909-330">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="2c909-331">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="2c909-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="2c909-332">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-332">Member</span></span> | <span data-ttu-id="2c909-333">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-334">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-335">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-336">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-336">All</span></span> |
| <span data-ttu-id="2c909-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="2c909-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2c909-338">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="2c909-339">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="2c909-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="2c909-340">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-340">Member</span></span> | <span data-ttu-id="2c909-341">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-342">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="2c909-343">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="2c909-343">System.Security.Policy</span></span>

| <span data-ttu-id="2c909-344">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-344">Member</span></span> | <span data-ttu-id="2c909-345">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-346">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="2c909-347">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="2c909-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="2c909-348">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-348">Member</span></span> | <span data-ttu-id="2c909-349">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2c909-350">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="2c909-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="2c909-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="2c909-352">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-352">Member</span></span> | <span data-ttu-id="2c909-353">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-354">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="2c909-355">System.Threading</span><span class="sxs-lookup"><span data-stu-id="2c909-355">System.Threading</span></span>

| <span data-ttu-id="2c909-356">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-356">Member</span></span> | <span data-ttu-id="2c909-357">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-358">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2c909-359">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="2c909-360">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="2c909-361">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="2c909-362">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="2c909-363">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="2c909-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="2c909-364">System.Xml</span></span>

| <span data-ttu-id="2c909-365">Membre</span><span class="sxs-lookup"><span data-stu-id="2c909-365">Member</span></span> | <span data-ttu-id="2c909-366">Plateformes qui lèvent</span><span class="sxs-lookup"><span data-stu-id="2c909-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="2c909-367">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="2c909-368">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="2c909-369">Tous</span><span class="sxs-lookup"><span data-stu-id="2c909-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="2c909-370">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c909-370">See also</span></span>

- [<span data-ttu-id="2c909-371">Dernières modifications pour la migration de .NET Framework vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c909-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="2c909-372">Sérialisation binaire dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c909-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="2c909-373">Analyseur de portabilité .NET</span><span class="sxs-lookup"><span data-stu-id="2c909-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
