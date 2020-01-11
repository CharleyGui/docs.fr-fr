---
title: API non prises en charge sur .NET Core
description: Découvrez les API de la .NET Framework qui lèvent toujours une exception sur .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: 0cb533f10d53fd3d287265032e3de13c242a8ae0
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901494"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="958ac-103">API qui lèvent toujours des exceptions sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="958ac-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="958ac-104">Les API suivantes passent toujours par un <xref:System.PlatformNotSupportedException> lorsqu’elles sont exécutées sur .NET Core sur la plateforme spécifiée.</span><span class="sxs-lookup"><span data-stu-id="958ac-104">The following APIs will always through a <xref:System.PlatformNotSupportedException> when run on .NET Core on the specified platform.</span></span>

<span data-ttu-id="958ac-105">Cet article organise les membres d’API affectés par espace de noms.</span><span class="sxs-lookup"><span data-stu-id="958ac-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="958ac-106">Cet article est un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="958ac-106">This article is a work-in-progress.</span></span> <span data-ttu-id="958ac-107">Il ne s’agit pas d’une liste complète des API qui lèvent des exceptions sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="958ac-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="958ac-108">Cet article n’inclut pas les implémentations d’interface explicites pour la sérialisation binaire qui lèvent sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="958ac-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="958ac-109">Pour plus d’informations, consultez [sérialisation binaire dans .net Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="958ac-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="958ac-110">System</span><span class="sxs-lookup"><span data-stu-id="958ac-110">System</span></span>

| <span data-ttu-id="958ac-111">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-111">Member</span></span> | <span data-ttu-id="958ac-112">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-112">Platform</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-113">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="958ac-114">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="958ac-115">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="958ac-116">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-117">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="958ac-118">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="958ac-119">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="958ac-120">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-121">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="958ac-122">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="958ac-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="958ac-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="958ac-124">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-124">Member</span></span> | <span data-ttu-id="958ac-125">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-125">Platform</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-126">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-127">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-128">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="958ac-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="958ac-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="958ac-130">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-130">Member</span></span> | <span data-ttu-id="958ac-131">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-131">Platform</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-132">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-133">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="958ac-134">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="958ac-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="958ac-135">System.Configuration</span></span>

| <span data-ttu-id="958ac-136">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-136">Member</span></span> | <span data-ttu-id="958ac-137">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-137">Platform</span></span> |
| - | - |
| <span data-ttu-id="958ac-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tous les membres)</span><span class="sxs-lookup"><span data-stu-id="958ac-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="958ac-139">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="958ac-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="958ac-140">System.Console</span></span>

| <span data-ttu-id="958ac-141">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-141">Member</span></span> | <span data-ttu-id="958ac-142">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-142">Platform</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="958ac-143">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-143">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-145">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-145">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-147">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-147">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-149">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-149">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (récupération uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="958ac-151">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-152">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-153">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-154">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-154">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-155"><xref:System.Console.Title?displayProperty=nameWithType> (récupération uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="958ac-156">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-156">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-158">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-158">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-160">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-160">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-162">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-162">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-164">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="958ac-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="958ac-165">System.Data.Common</span></span>

| <span data-ttu-id="958ac-166">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-166">Member</span></span> | <span data-ttu-id="958ac-167">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-167">Platform</span></span> |
| - | - |
| <span data-ttu-id="958ac-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (lève <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="958ac-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="958ac-169">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="958ac-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="958ac-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="958ac-171">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-171">Member</span></span> | <span data-ttu-id="958ac-172">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-172">Platform</span></span> |
| - | - |
| <span data-ttu-id="958ac-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-174">Linux</span><span class="sxs-lookup"><span data-stu-id="958ac-174">Linux</span></span> |
| <span data-ttu-id="958ac-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-176">Linux</span><span class="sxs-lookup"><span data-stu-id="958ac-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="958ac-177">macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="958ac-178">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-179">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="958ac-180">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="958ac-181">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="958ac-182">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="958ac-183">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-183">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-185">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-185">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (récupération uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="958ac-187">macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-187">macOS</span></span> |
| <span data-ttu-id="958ac-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-189">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="958ac-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="958ac-190">System.IO</span></span>

| <span data-ttu-id="958ac-191">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-191">Member</span></span> | <span data-ttu-id="958ac-192">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-192">Platform</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-193">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-194">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="958ac-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="958ac-195">System.IO.Pipes</span></span>

| <span data-ttu-id="958ac-196">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-196">Member</span></span> | <span data-ttu-id="958ac-197">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-197">Platform</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="958ac-198">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="958ac-199">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="958ac-200">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="958ac-201">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-201">Linux and macOS</span></span> |
| <span data-ttu-id="958ac-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-203">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="958ac-204">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="958ac-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="958ac-205">System.Media</span></span>

| <span data-ttu-id="958ac-206">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-206">Member</span></span> | <span data-ttu-id="958ac-207">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-207">Platform</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-208">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="958ac-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="958ac-209">System.Net</span></span>

| <span data-ttu-id="958ac-210">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-210">Member</span></span> | <span data-ttu-id="958ac-211">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-211">Platform</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="958ac-212">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="958ac-213">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-214">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-215">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-216">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-217">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-218">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-219">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-220">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-221">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-222">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="958ac-223">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-224">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-225">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-226">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-227">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-228">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="958ac-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="958ac-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="958ac-230">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-230">Member</span></span> | <span data-ttu-id="958ac-231">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-231">Platform</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="958ac-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="958ac-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="958ac-233">System.Net.Sockets</span></span>

| <span data-ttu-id="958ac-234">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-234">Member</span></span> | <span data-ttu-id="958ac-235">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-235">Platform</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="958ac-236">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-236">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="958ac-237">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="958ac-237">System.Net.WebSockets</span></span>

| <span data-ttu-id="958ac-238">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-238">Member</span></span> | <span data-ttu-id="958ac-239">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-239">Platform</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="958ac-240">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-240">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="958ac-241">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="958ac-241">System.Reflection</span></span>

| <span data-ttu-id="958ac-242">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-242">Member</span></span> | <span data-ttu-id="958ac-243">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-243">Platform</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-244">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-244">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="958ac-245">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-245">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-246">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="958ac-247">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-247">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="958ac-248">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-249">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="958ac-250">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-250">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="958ac-251">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="958ac-251">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="958ac-252">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-252">Member</span></span> | <span data-ttu-id="958ac-253">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-253">Platform</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="958ac-254">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-254">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="958ac-255">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="958ac-255">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="958ac-256">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-256">Member</span></span> | <span data-ttu-id="958ac-257">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-257">Platform</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="958ac-258">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-258">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="958ac-259">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="958ac-260">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="958ac-261">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-261">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="958ac-262">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-262">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="958ac-263">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="958ac-264">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-264">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="958ac-265">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="958ac-265">System.Runtime.Serialization</span></span>

| <span data-ttu-id="958ac-266">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-266">Member</span></span> | <span data-ttu-id="958ac-267">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-267">Platform</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="958ac-268">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-268">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="958ac-269">System.Security</span><span class="sxs-lookup"><span data-stu-id="958ac-269">System.Security</span></span>

| <span data-ttu-id="958ac-270">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-270">Member</span></span> | <span data-ttu-id="958ac-271">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-271">Platform</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="958ac-272">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-272">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="958ac-273">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-273">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="958ac-274">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-274">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="958ac-275">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-275">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="958ac-276">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-276">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="958ac-277">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-277">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="958ac-278">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-278">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="958ac-279">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-279">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="958ac-280">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="958ac-281">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-281">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="958ac-282">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-282">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="958ac-283">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-283">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="958ac-284">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="958ac-285">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-285">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="958ac-286">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="958ac-286">System.Security.Claims</span></span>

| <span data-ttu-id="958ac-287">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-287">Member</span></span> | <span data-ttu-id="958ac-288">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-288">Platform</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="958ac-289">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-289">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-290">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="958ac-291">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-292">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-293">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-293">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="958ac-294">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="958ac-294">System.Security.Cryptography</span></span>

| <span data-ttu-id="958ac-295">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-295">Member</span></span> | <span data-ttu-id="958ac-296">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-296">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="958ac-297">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-297">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-298">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-298">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="958ac-299">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="958ac-300">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="958ac-301">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="958ac-302">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="958ac-303">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="958ac-304">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="958ac-305">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="958ac-306">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="958ac-307">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="958ac-308">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="958ac-309">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="958ac-310">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="958ac-311">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-311">All</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="958ac-312">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="958ac-313">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="958ac-314">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-315">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-316">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-317">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="958ac-318">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="958ac-319">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-320">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-321">Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="958ac-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-322">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-323">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="958ac-324">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="958ac-325">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="958ac-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="958ac-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="958ac-327">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-327">Member</span></span> | <span data-ttu-id="958ac-328">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-328">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="958ac-329">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="958ac-330">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="958ac-331">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="958ac-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="958ac-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="958ac-333">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-333">Member</span></span> | <span data-ttu-id="958ac-334">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-334">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-335">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-336">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-337">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-337">All</span></span> |
| <span data-ttu-id="958ac-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (définir uniquement)</span><span class="sxs-lookup"><span data-stu-id="958ac-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="958ac-339">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="958ac-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="958ac-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="958ac-341">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-341">Member</span></span> | <span data-ttu-id="958ac-342">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-342">Platform</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-343">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="958ac-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="958ac-344">System.Security.Policy</span></span>

| <span data-ttu-id="958ac-345">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-345">Member</span></span> | <span data-ttu-id="958ac-346">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-346">Platform</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-347">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="958ac-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="958ac-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="958ac-349">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-349">Member</span></span> | <span data-ttu-id="958ac-350">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-350">Platform</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-351">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="958ac-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="958ac-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="958ac-353">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-353">Member</span></span> | <span data-ttu-id="958ac-354">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-354">Platform</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-355">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="958ac-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="958ac-356">System.Threading</span></span>

| <span data-ttu-id="958ac-357">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-357">Member</span></span> | <span data-ttu-id="958ac-358">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-358">Platform</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-359">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="958ac-360">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="958ac-361">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="958ac-362">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="958ac-363">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="958ac-364">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="958ac-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="958ac-365">System.Xml</span></span>

| <span data-ttu-id="958ac-366">Member</span><span class="sxs-lookup"><span data-stu-id="958ac-366">Member</span></span> | <span data-ttu-id="958ac-367">Platform</span><span class="sxs-lookup"><span data-stu-id="958ac-367">Platform</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="958ac-368">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="958ac-369">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="958ac-370">Toutes les</span><span class="sxs-lookup"><span data-stu-id="958ac-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="958ac-371">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="958ac-371">See also</span></span>

- [<span data-ttu-id="958ac-372">Dernières modifications pour la migration de .NET Framework vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="958ac-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="958ac-373">Sérialisation binaire dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="958ac-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="958ac-374">Analyseur de portabilité .NET</span><span class="sxs-lookup"><span data-stu-id="958ac-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
