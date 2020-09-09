---
title: Modifications importantes de la bibliothèque de classes de base
description: Répertorie les modifications avec rupture dans les bibliothèques .NET de base.
ms.date: 07/27/2020
ms.openlocfilehash: c73909514bc738387a21f5ea68defe49c6a2c839
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598164"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="3d388-103">Modifications importantes des bibliothèques .NET principales</span><span class="sxs-lookup"><span data-stu-id="3d388-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="3d388-104">Les bibliothèques .NET de base fournissent les primitives et d’autres types généraux utilisés par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3d388-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="3d388-105">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="3d388-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="3d388-106">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="3d388-106">Breaking change</span></span> | <span data-ttu-id="3d388-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3d388-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="3d388-108">Thread. Abort est obsolète</span><span class="sxs-lookup"><span data-stu-id="3d388-108">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="3d388-109">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-109">5.0</span></span> |
| [<span data-ttu-id="3d388-110">Propriétés obsolètes sur ConsoleLoggerOptions</span><span class="sxs-lookup"><span data-stu-id="3d388-110">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="3d388-111">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-111">5.0</span></span> |
| [<span data-ttu-id="3d388-112">Les contrôles de IsSupported intrinsèques matériels peuvent être différents pour les types imbriqués</span><span class="sxs-lookup"><span data-stu-id="3d388-112">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="3d388-113">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-113">5.0</span></span> |
| [<span data-ttu-id="3d388-114">Noms de paramètres modifiés dans les assemblys de référence</span><span class="sxs-lookup"><span data-stu-id="3d388-114">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="3d388-115">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-115">5.0</span></span> |
| [<span data-ttu-id="3d388-116">Les chemins d’accès URI avec des caractères non-ASCII sont analysés correctement sur UNIX</span><span class="sxs-lookup"><span data-stu-id="3d388-116">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="3d388-117">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-117">5.0</span></span> |
| [<span data-ttu-id="3d388-118">Reconnaissance d’URI de chemins d’accès UNC sur UNIX</span><span class="sxs-lookup"><span data-stu-id="3d388-118">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="3d388-119">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-119">5.0</span></span> |
| [<span data-ttu-id="3d388-120">Environment. OSVersion retourne la version appropriée du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="3d388-120">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="3d388-121">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-121">5.0</span></span> |
| [<span data-ttu-id="3d388-122">Complexité de LINQ OrderBy. la première {OrDefault} a augmenté</span><span class="sxs-lookup"><span data-stu-id="3d388-122">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="3d388-123">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-123">5.0</span></span> |
| [<span data-ttu-id="3d388-124">IntPtr et UIntPtr implémentent IFormattable</span><span class="sxs-lookup"><span data-stu-id="3d388-124">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="3d388-125">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-125">5.0</span></span> |
| [<span data-ttu-id="3d388-126">PrincipalPermissionAttribute est obsolète en tant qu’erreur</span><span class="sxs-lookup"><span data-stu-id="3d388-126">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="3d388-127">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-127">5.0</span></span> |
| [<span data-ttu-id="3d388-128">Les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3d388-128">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="3d388-129">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-129">5.0</span></span> |
| [<span data-ttu-id="3d388-130">Les chemins d’accès de code UTF-7 sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="3d388-130">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="3d388-131">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-131">5.0</span></span> |
| [<span data-ttu-id="3d388-132">Vector \<T> lève toujours l’exception NotSupportedException pour les types non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3d388-132">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="3d388-133">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-133">5.0</span></span> |
| [<span data-ttu-id="3d388-134">Le ActivityIdFormat par défaut est W3C</span><span class="sxs-lookup"><span data-stu-id="3d388-134">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="3d388-135">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-135">5.0</span></span> |
| [<span data-ttu-id="3d388-136">Changement de comportement pour Vector2. Lerp et Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="3d388-136">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="3d388-137">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-137">5.0</span></span> |
| [<span data-ttu-id="3d388-138">Les méthodes SSE et SSE2 CompareGreaterThan gèrent correctement les entrées NaN</span><span class="sxs-lookup"><span data-stu-id="3d388-138">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="3d388-139">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-139">5.0</span></span> |
| [<span data-ttu-id="3d388-140">CounterSet. CreateCounterSetInstance lève désormais une exception InvalidOperationException si l’instance existe déjà</span><span class="sxs-lookup"><span data-stu-id="3d388-140">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="3d388-141">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-141">5.0</span></span> |
| [<span data-ttu-id="3d388-142">Package Microsoft. DotNet. PlatformAbstractions supprimé</span><span class="sxs-lookup"><span data-stu-id="3d388-142">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="3d388-143">5.0</span><span class="sxs-lookup"><span data-stu-id="3d388-143">5.0</span></span> |
| [<span data-ttu-id="3d388-144">API qui signalent la version du produit et non de la version du fichier</span><span class="sxs-lookup"><span data-stu-id="3d388-144">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="3d388-145">3.0</span><span class="sxs-lookup"><span data-stu-id="3d388-145">3.0</span></span> |
| [<span data-ttu-id="3d388-146">Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive</span><span class="sxs-lookup"><span data-stu-id="3d388-146">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="3d388-147">3.0</span><span class="sxs-lookup"><span data-stu-id="3d388-147">3.0</span></span> |
| [<span data-ttu-id="3d388-148">Modifications du comportement de l’analyse et de la mise en forme à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="3d388-148">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="3d388-149">3.0</span><span class="sxs-lookup"><span data-stu-id="3d388-149">3.0</span></span> |
| [<span data-ttu-id="3d388-150">Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException</span><span class="sxs-lookup"><span data-stu-id="3d388-150">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="3d388-151">3.0</span><span class="sxs-lookup"><span data-stu-id="3d388-151">3.0</span></span> |
| [<span data-ttu-id="3d388-152">InvalidAsynchronousStateException déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="3d388-152">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="3d388-153">3.0</span><span class="sxs-lookup"><span data-stu-id="3d388-153">3.0</span></span> |
| [<span data-ttu-id="3d388-154">Le remplacement des séquences d’octets UTF-8 incorrectes suit les instructions Unicode</span><span class="sxs-lookup"><span data-stu-id="3d388-154">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="3d388-155">3.0</span><span class="sxs-lookup"><span data-stu-id="3d388-155">3.0</span></span> |
| [<span data-ttu-id="3d388-156">TypeDescriptionProviderAttribute déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="3d388-156">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="3d388-157">3.0</span><span class="sxs-lookup"><span data-stu-id="3d388-157">3.0</span></span> |
| [<span data-ttu-id="3d388-158">ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes</span><span class="sxs-lookup"><span data-stu-id="3d388-158">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="3d388-159">3.0</span><span class="sxs-lookup"><span data-stu-id="3d388-159">3.0</span></span> |
| [<span data-ttu-id="3d388-160">FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule</span><span class="sxs-lookup"><span data-stu-id="3d388-160">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="3d388-161">3.0</span><span class="sxs-lookup"><span data-stu-id="3d388-161">3.0</span></span> |
| [<span data-ttu-id="3d388-162">Champs privés ajoutés aux types struct intégrés</span><span class="sxs-lookup"><span data-stu-id="3d388-162">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="3d388-163">2.1</span><span class="sxs-lookup"><span data-stu-id="3d388-163">2.1</span></span> |
| [<span data-ttu-id="3d388-164">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="3d388-164">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="3d388-165">2.1</span><span class="sxs-lookup"><span data-stu-id="3d388-165">2.1</span></span> |
| [<span data-ttu-id="3d388-166">Versions OpenSSL sur macOS</span><span class="sxs-lookup"><span data-stu-id="3d388-166">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="3d388-167">2.1</span><span class="sxs-lookup"><span data-stu-id="3d388-167">2.1</span></span> |
| [<span data-ttu-id="3d388-168">UnauthorizedAccessException levée par FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="3d388-168">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="3d388-169">1.0</span><span class="sxs-lookup"><span data-stu-id="3d388-169">1.0</span></span> |
| [<span data-ttu-id="3d388-170">La gestion des exceptions d’état de processus endommagées n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="3d388-170">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="3d388-171">1.0</span><span class="sxs-lookup"><span data-stu-id="3d388-171">1.0</span></span> |
| [<span data-ttu-id="3d388-172">Les propriétés UriBuilder n’ajoutent plus de caractères de début</span><span class="sxs-lookup"><span data-stu-id="3d388-172">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="3d388-173">1.0</span><span class="sxs-lookup"><span data-stu-id="3d388-173">1.0</span></span> |
| [<span data-ttu-id="3d388-174">Process. StartInfo lève une exception InvalidOperationException pour les processus que vous n’avez pas démarrés</span><span class="sxs-lookup"><span data-stu-id="3d388-174">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="3d388-175">1.0</span><span class="sxs-lookup"><span data-stu-id="3d388-175">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="3d388-176">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="3d388-176">.NET 5.0</span></span>

[!INCLUDE [thread-abort-obsolete](../../../includes/core-changes/corefx/5.0/thread-abort-obsolete.md)]

***

[!INCLUDE [obsolete-consoleloggeroptions-properties](../../../includes/core-changes/corefx/5.0/obsolete-consoleloggeroptions-properties.md)]

***

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

***

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

***

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

***

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

***

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

***

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

***

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

***

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

***

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

***

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

***

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

***

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="3d388-177">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3d388-177">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="3d388-178">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3d388-178">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="3d388-179">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3d388-179">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
