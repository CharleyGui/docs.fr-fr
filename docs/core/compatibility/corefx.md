---
title: Modifications importantes de la bibliothèque de classes de base
description: Répertorie les modifications avec rupture dans les bibliothèques .NET de base.
ms.date: 07/27/2020
ms.openlocfilehash: 900fd4e0e071f19aa286dec84632006870822f26
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434919"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="f491e-103">Modifications importantes des bibliothèques .NET principales</span><span class="sxs-lookup"><span data-stu-id="f491e-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="f491e-104">Les bibliothèques .NET de base fournissent les primitives et d’autres types généraux utilisés par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f491e-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="f491e-105">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="f491e-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="f491e-106">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="f491e-106">Breaking change</span></span> | <span data-ttu-id="f491e-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f491e-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="f491e-108">Les API du global assembly cache sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="f491e-108">Global assembly cache APIs are obsolete</span></span>](#global-assembly-cache-apis-are-obsolete) | <span data-ttu-id="f491e-109">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-109">5.0</span></span> |
| [<span data-ttu-id="f491e-110">Les API de communication à distance sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="f491e-110">Remoting APIs are obsolete</span></span>](#remoting-apis-are-obsolete) | <span data-ttu-id="f491e-111">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-111">5.0</span></span> |
| [<span data-ttu-id="f491e-112">La plupart des API de sécurité d’accès du code sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="f491e-112">Most code access security APIs are obsolete</span></span>](#most-code-access-security-apis-are-obsolete) | <span data-ttu-id="f491e-113">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-113">5.0</span></span> |
| [<span data-ttu-id="f491e-114">Obsoletions d’API avec ID de diagnostics autres que ceux par défaut</span><span class="sxs-lookup"><span data-stu-id="f491e-114">API obsoletions with non-default diagnostic IDs</span></span>](#api-obsoletions-with-non-default-diagnostic-ids) | <span data-ttu-id="f491e-115">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-115">5.0</span></span> |
| [<span data-ttu-id="f491e-116">La valeur de FrameworkDescription est .NET au lieu de .NET Core</span><span class="sxs-lookup"><span data-stu-id="f491e-116">FrameworkDescription's value is .NET instead of .NET Core</span></span>](#frameworkdescriptions-value-is-net-instead-of-net-core) | <span data-ttu-id="f491e-117">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-117">5.0</span></span> |
| [<span data-ttu-id="f491e-118">Modifications du comportement des API liées à l’assembly pour le format de publication à fichier unique</span><span class="sxs-lookup"><span data-stu-id="f491e-118">Assembly-related API behavior changes for single-file publishing format</span></span>](#assembly-related-api-behavior-changes-for-single-file-publishing-format) | <span data-ttu-id="f491e-119">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-119">5.0</span></span> |
| [<span data-ttu-id="f491e-120">Ordre des balises dans Activity. les balises sont inversées</span><span class="sxs-lookup"><span data-stu-id="f491e-120">Order of tags in Activity.Tags is reversed</span></span>](#order-of-tags-in-activitytags-is-reversed) | <span data-ttu-id="f491e-121">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-121">5.0</span></span> |
| [<span data-ttu-id="f491e-122">Noms de paramètres modifiés dans RC1</span><span class="sxs-lookup"><span data-stu-id="f491e-122">Parameter names changed in RC1</span></span>](#parameter-names-changed-in-rc1) | <span data-ttu-id="f491e-123">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-123">5.0</span></span> |
| [<span data-ttu-id="f491e-124">Attributs OSPlatform renommés ou supprimés</span><span class="sxs-lookup"><span data-stu-id="f491e-124">OSPlatform attributes renamed or removed</span></span>](#osplatform-attributes-renamed-or-removed) | <span data-ttu-id="f491e-125">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-125">5.0</span></span> |
| [<span data-ttu-id="f491e-126">Thread. Abort est obsolète</span><span class="sxs-lookup"><span data-stu-id="f491e-126">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="f491e-127">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-127">5.0</span></span> |
| [<span data-ttu-id="f491e-128">Propriétés obsolètes sur ConsoleLoggerOptions</span><span class="sxs-lookup"><span data-stu-id="f491e-128">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="f491e-129">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-129">5.0</span></span> |
| [<span data-ttu-id="f491e-130">Les contrôles de IsSupported intrinsèques matériels peuvent être différents pour les types imbriqués</span><span class="sxs-lookup"><span data-stu-id="f491e-130">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="f491e-131">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-131">5.0</span></span> |
| [<span data-ttu-id="f491e-132">Noms de paramètres modifiés dans les assemblys de référence</span><span class="sxs-lookup"><span data-stu-id="f491e-132">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="f491e-133">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-133">5.0</span></span> |
| [<span data-ttu-id="f491e-134">Les chemins d’accès URI avec des caractères non-ASCII sont analysés correctement sur UNIX</span><span class="sxs-lookup"><span data-stu-id="f491e-134">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="f491e-135">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-135">5.0</span></span> |
| [<span data-ttu-id="f491e-136">Reconnaissance d’URI de chemins d’accès UNC sur UNIX</span><span class="sxs-lookup"><span data-stu-id="f491e-136">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="f491e-137">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-137">5.0</span></span> |
| [<span data-ttu-id="f491e-138">Environment. OSVersion retourne la version appropriée du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="f491e-138">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="f491e-139">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-139">5.0</span></span> |
| [<span data-ttu-id="f491e-140">Complexité de LINQ OrderBy. la première {OrDefault} a augmenté</span><span class="sxs-lookup"><span data-stu-id="f491e-140">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="f491e-141">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-141">5.0</span></span> |
| [<span data-ttu-id="f491e-142">IntPtr et UIntPtr implémentent IFormattable</span><span class="sxs-lookup"><span data-stu-id="f491e-142">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="f491e-143">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-143">5.0</span></span> |
| [<span data-ttu-id="f491e-144">PrincipalPermissionAttribute est obsolète en tant qu’erreur</span><span class="sxs-lookup"><span data-stu-id="f491e-144">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="f491e-145">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-145">5.0</span></span> |
| [<span data-ttu-id="f491e-146">Les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f491e-146">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="f491e-147">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-147">5.0</span></span> |
| [<span data-ttu-id="f491e-148">Les chemins d’accès de code UTF-7 sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="f491e-148">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="f491e-149">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-149">5.0</span></span> |
| [<span data-ttu-id="f491e-150">Vector \<T> lève toujours l’exception NotSupportedException pour les types non pris en charge</span><span class="sxs-lookup"><span data-stu-id="f491e-150">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="f491e-151">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-151">5.0</span></span> |
| [<span data-ttu-id="f491e-152">Le ActivityIdFormat par défaut est W3C</span><span class="sxs-lookup"><span data-stu-id="f491e-152">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="f491e-153">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-153">5.0</span></span> |
| [<span data-ttu-id="f491e-154">Changement de comportement pour Vector2. Lerp et Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="f491e-154">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="f491e-155">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-155">5.0</span></span> |
| [<span data-ttu-id="f491e-156">Les méthodes SSE et SSE2 CompareGreaterThan gèrent correctement les entrées NaN</span><span class="sxs-lookup"><span data-stu-id="f491e-156">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="f491e-157">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-157">5.0</span></span> |
| [<span data-ttu-id="f491e-158">CounterSet. CreateCounterSetInstance lève désormais une exception InvalidOperationException si l’instance existe déjà</span><span class="sxs-lookup"><span data-stu-id="f491e-158">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="f491e-159">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-159">5.0</span></span> |
| [<span data-ttu-id="f491e-160">Package Microsoft. DotNet. PlatformAbstractions supprimé</span><span class="sxs-lookup"><span data-stu-id="f491e-160">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="f491e-161">5.0</span><span class="sxs-lookup"><span data-stu-id="f491e-161">5.0</span></span> |
| [<span data-ttu-id="f491e-162">API qui signalent la version du produit et non de la version du fichier</span><span class="sxs-lookup"><span data-stu-id="f491e-162">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="f491e-163">3.0</span><span class="sxs-lookup"><span data-stu-id="f491e-163">3.0</span></span> |
| [<span data-ttu-id="f491e-164">Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive</span><span class="sxs-lookup"><span data-stu-id="f491e-164">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="f491e-165">3.0</span><span class="sxs-lookup"><span data-stu-id="f491e-165">3.0</span></span> |
| [<span data-ttu-id="f491e-166">Modifications du comportement de l’analyse et de la mise en forme à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="f491e-166">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="f491e-167">3.0</span><span class="sxs-lookup"><span data-stu-id="f491e-167">3.0</span></span> |
| [<span data-ttu-id="f491e-168">Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException</span><span class="sxs-lookup"><span data-stu-id="f491e-168">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="f491e-169">3.0</span><span class="sxs-lookup"><span data-stu-id="f491e-169">3.0</span></span> |
| [<span data-ttu-id="f491e-170">InvalidAsynchronousStateException déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="f491e-170">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="f491e-171">3.0</span><span class="sxs-lookup"><span data-stu-id="f491e-171">3.0</span></span> |
| [<span data-ttu-id="f491e-172">Le remplacement des séquences d’octets UTF-8 incorrectes suit les instructions Unicode</span><span class="sxs-lookup"><span data-stu-id="f491e-172">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="f491e-173">3.0</span><span class="sxs-lookup"><span data-stu-id="f491e-173">3.0</span></span> |
| [<span data-ttu-id="f491e-174">TypeDescriptionProviderAttribute déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="f491e-174">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="f491e-175">3.0</span><span class="sxs-lookup"><span data-stu-id="f491e-175">3.0</span></span> |
| [<span data-ttu-id="f491e-176">ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes</span><span class="sxs-lookup"><span data-stu-id="f491e-176">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="f491e-177">3.0</span><span class="sxs-lookup"><span data-stu-id="f491e-177">3.0</span></span> |
| [<span data-ttu-id="f491e-178">FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule</span><span class="sxs-lookup"><span data-stu-id="f491e-178">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="f491e-179">3.0</span><span class="sxs-lookup"><span data-stu-id="f491e-179">3.0</span></span> |
| [<span data-ttu-id="f491e-180">Champs privés ajoutés aux types struct intégrés</span><span class="sxs-lookup"><span data-stu-id="f491e-180">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="f491e-181">2.1</span><span class="sxs-lookup"><span data-stu-id="f491e-181">2.1</span></span> |
| [<span data-ttu-id="f491e-182">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="f491e-182">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="f491e-183">2.1</span><span class="sxs-lookup"><span data-stu-id="f491e-183">2.1</span></span> |
| [<span data-ttu-id="f491e-184">Versions OpenSSL sur macOS</span><span class="sxs-lookup"><span data-stu-id="f491e-184">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="f491e-185">2.1</span><span class="sxs-lookup"><span data-stu-id="f491e-185">2.1</span></span> |
| [<span data-ttu-id="f491e-186">UnauthorizedAccessException levée par FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="f491e-186">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="f491e-187">1.0</span><span class="sxs-lookup"><span data-stu-id="f491e-187">1.0</span></span> |
| [<span data-ttu-id="f491e-188">La gestion des exceptions d’état de processus endommagées n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="f491e-188">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="f491e-189">1.0</span><span class="sxs-lookup"><span data-stu-id="f491e-189">1.0</span></span> |
| [<span data-ttu-id="f491e-190">Les propriétés UriBuilder n’ajoutent plus de caractères de début</span><span class="sxs-lookup"><span data-stu-id="f491e-190">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="f491e-191">1.0</span><span class="sxs-lookup"><span data-stu-id="f491e-191">1.0</span></span> |
| [<span data-ttu-id="f491e-192">Process. StartInfo lève une exception InvalidOperationException pour les processus que vous n’avez pas démarrés</span><span class="sxs-lookup"><span data-stu-id="f491e-192">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="f491e-193">1.0</span><span class="sxs-lookup"><span data-stu-id="f491e-193">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="f491e-194">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f491e-194">.NET 5.0</span></span>

[!INCLUDE [remoting-apis-obsolete](../../../includes/core-changes/corefx/5.0/remoting-apis-obsolete.md)]

***

[!INCLUDE [globalassemblycache-property-obsolete](../../../includes/core-changes/corefx/5.0/global-assembly-cache-apis-obsolete.md)]

<span data-ttu-id="f491e-195">\*\*_</span><span class="sxs-lookup"><span data-stu-id="f491e-195">\*\*_</span></span>

[!INCLUDE [code-access-security-apis-obsolete](../../../includes/core-changes/corefx/5.0/code-access-security-apis-obsolete.md)]

_*_

[!INCLUDE [obsolete-apis-with-custom-diagnostics](../../../includes/core-changes/corefx/5.0/obsolete-apis-with-custom-diagnostics.md)]

_*_

[!INCLUDE [frameworkdescription-returns-net-not-net-core](../../../includes/core-changes/corefx/5.0/frameworkdescription-returns-net-not-net-core.md)]

_*_

[!INCLUDE [assembly-api-behavior-changes-for-single-file-publish](../../../includes/core-changes/corefx/5.0/assembly-api-behavior-changes-for-single-file-publish.md)]

_*_

[!INCLUDE [reverse-order-of-tags-in-activity-property](../../../includes/core-changes/corefx/5.0/reverse-order-of-tags-in-activity-property.md)]

_*_

[!INCLUDE [reference-assembly-parameter-names-rc1](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names-rc1.md)]

_*_

[!INCLUDE [os-platform-attributes-renamed](../../../includes/core-changes/corefx/5.0/os-platform-attributes-renamed.md)]

_*_

[!INCLUDE [thread-abort-obsolete](../../../includes/core-changes/corefx/5.0/thread-abort-obsolete.md)]

_*_

[!INCLUDE [obsolete-consoleloggeroptions-properties](../../../includes/core-changes/corefx/5.0/obsolete-consoleloggeroptions-properties.md)]

_*_

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

_*_

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

_*_

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

_*_

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

_*_

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

_*_

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

_*_

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

_*_

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

_*_

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

_*_

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

_*_

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

_*_

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

_*_

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

_*_

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

_*_

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

_*_

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="f491e-196">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f491e-196">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

_*_

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

_*_

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

_*_

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

_*_

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

_*_

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

_*_

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

_*_

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

_*_

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

_*_

## <a name="net-core-21"></a><span data-ttu-id="f491e-197">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f491e-197">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="f491e-198">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f491e-198">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="f491e-199">_\*\*</span><span class="sxs-lookup"><span data-stu-id="f491e-199">_\*\*</span></span>
