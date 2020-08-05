---
title: Modifications importantes de la bibliothèque de classes de base
description: Répertorie les modifications avec rupture dans les bibliothèques .NET de base.
ms.date: 07/27/2020
ms.openlocfilehash: d474d5547245e57206d669531b74b5be31c98ca0
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556325"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="27112-103">Modifications importantes des bibliothèques .NET principales</span><span class="sxs-lookup"><span data-stu-id="27112-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="27112-104">Les bibliothèques .NET de base fournissent les primitives et d’autres types généraux utilisés par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="27112-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="27112-105">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="27112-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="27112-106">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="27112-106">Breaking change</span></span> | <span data-ttu-id="27112-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="27112-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="27112-108">PrincipalPermissionAttribute est obsolète en tant qu’erreur</span><span class="sxs-lookup"><span data-stu-id="27112-108">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="27112-109">5.0</span><span class="sxs-lookup"><span data-stu-id="27112-109">5.0</span></span> |
| [<span data-ttu-id="27112-110">Les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET</span><span class="sxs-lookup"><span data-stu-id="27112-110">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="27112-111">5.0</span><span class="sxs-lookup"><span data-stu-id="27112-111">5.0</span></span> |
| [<span data-ttu-id="27112-112">Les chemins d’accès de code UTF-7 sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="27112-112">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="27112-113">5.0</span><span class="sxs-lookup"><span data-stu-id="27112-113">5.0</span></span> |
| [<span data-ttu-id="27112-114">Vector \<T> lève toujours l’exception NotSupportedException pour les types non pris en charge</span><span class="sxs-lookup"><span data-stu-id="27112-114">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="27112-115">5.0</span><span class="sxs-lookup"><span data-stu-id="27112-115">5.0</span></span> |
| [<span data-ttu-id="27112-116">Le ActivityIdFormat par défaut est W3C</span><span class="sxs-lookup"><span data-stu-id="27112-116">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="27112-117">5.0</span><span class="sxs-lookup"><span data-stu-id="27112-117">5.0</span></span> |
| [<span data-ttu-id="27112-118">Changement de comportement pour Vector2. Lerp et Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="27112-118">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="27112-119">5.0</span><span class="sxs-lookup"><span data-stu-id="27112-119">5.0</span></span> |
| [<span data-ttu-id="27112-120">Les méthodes SSE et SSE2 CompareGreaterThan gèrent correctement les entrées NaN</span><span class="sxs-lookup"><span data-stu-id="27112-120">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="27112-121">5.0</span><span class="sxs-lookup"><span data-stu-id="27112-121">5.0</span></span> |
| [<span data-ttu-id="27112-122">CounterSet. CreateCounterSetInstance lève désormais une exception InvalidOperationException si l’instance existe déjà</span><span class="sxs-lookup"><span data-stu-id="27112-122">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="27112-123">5.0</span><span class="sxs-lookup"><span data-stu-id="27112-123">5.0</span></span> |
| [<span data-ttu-id="27112-124">Package Microsoft. DotNet. PlatformAbstractions supprimé</span><span class="sxs-lookup"><span data-stu-id="27112-124">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="27112-125">5.0</span><span class="sxs-lookup"><span data-stu-id="27112-125">5.0</span></span> |
| [<span data-ttu-id="27112-126">API qui signalent la version du produit et non de la version du fichier</span><span class="sxs-lookup"><span data-stu-id="27112-126">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="27112-127">3.0</span><span class="sxs-lookup"><span data-stu-id="27112-127">3.0</span></span> |
| [<span data-ttu-id="27112-128">Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive</span><span class="sxs-lookup"><span data-stu-id="27112-128">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="27112-129">3.0</span><span class="sxs-lookup"><span data-stu-id="27112-129">3.0</span></span> |
| [<span data-ttu-id="27112-130">Modifications du comportement de l’analyse et de la mise en forme à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="27112-130">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="27112-131">3.0</span><span class="sxs-lookup"><span data-stu-id="27112-131">3.0</span></span> |
| [<span data-ttu-id="27112-132">Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException</span><span class="sxs-lookup"><span data-stu-id="27112-132">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="27112-133">3.0</span><span class="sxs-lookup"><span data-stu-id="27112-133">3.0</span></span> |
| [<span data-ttu-id="27112-134">InvalidAsynchronousStateException déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="27112-134">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="27112-135">3.0</span><span class="sxs-lookup"><span data-stu-id="27112-135">3.0</span></span> |
| [<span data-ttu-id="27112-136">Le remplacement des séquences d’octets UTF-8 incorrectes suit les instructions Unicode</span><span class="sxs-lookup"><span data-stu-id="27112-136">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="27112-137">3.0</span><span class="sxs-lookup"><span data-stu-id="27112-137">3.0</span></span> |
| [<span data-ttu-id="27112-138">TypeDescriptionProviderAttribute déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="27112-138">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="27112-139">3.0</span><span class="sxs-lookup"><span data-stu-id="27112-139">3.0</span></span> |
| [<span data-ttu-id="27112-140">ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes</span><span class="sxs-lookup"><span data-stu-id="27112-140">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="27112-141">3.0</span><span class="sxs-lookup"><span data-stu-id="27112-141">3.0</span></span> |
| [<span data-ttu-id="27112-142">FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule</span><span class="sxs-lookup"><span data-stu-id="27112-142">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="27112-143">3.0</span><span class="sxs-lookup"><span data-stu-id="27112-143">3.0</span></span> |
| [<span data-ttu-id="27112-144">Champs privés ajoutés aux types struct intégrés</span><span class="sxs-lookup"><span data-stu-id="27112-144">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="27112-145">2.1</span><span class="sxs-lookup"><span data-stu-id="27112-145">2.1</span></span> |
| [<span data-ttu-id="27112-146">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="27112-146">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="27112-147">2.1</span><span class="sxs-lookup"><span data-stu-id="27112-147">2.1</span></span> |
| [<span data-ttu-id="27112-148">Versions OpenSSL sur macOS</span><span class="sxs-lookup"><span data-stu-id="27112-148">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="27112-149">2.1</span><span class="sxs-lookup"><span data-stu-id="27112-149">2.1</span></span> |
| [<span data-ttu-id="27112-150">UnauthorizedAccessException levée par FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="27112-150">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="27112-151">1.0</span><span class="sxs-lookup"><span data-stu-id="27112-151">1.0</span></span> |
| [<span data-ttu-id="27112-152">La gestion des exceptions d’état de processus endommagées n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="27112-152">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="27112-153">1.0</span><span class="sxs-lookup"><span data-stu-id="27112-153">1.0</span></span> |
| [<span data-ttu-id="27112-154">Les propriétés UriBuilder n’ajoutent plus de caractères de début</span><span class="sxs-lookup"><span data-stu-id="27112-154">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="27112-155">1.0</span><span class="sxs-lookup"><span data-stu-id="27112-155">1.0</span></span> |
| [<span data-ttu-id="27112-156">Process. StartInfo lève une exception InvalidOperationException pour les processus que vous n’avez pas démarrés</span><span class="sxs-lookup"><span data-stu-id="27112-156">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="27112-157">1.0</span><span class="sxs-lookup"><span data-stu-id="27112-157">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="27112-158">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="27112-158">.NET 5.0</span></span>

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

## <a name="net-core-30"></a><span data-ttu-id="27112-159">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="27112-159">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="27112-160">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="27112-160">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="27112-161">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="27112-161">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
