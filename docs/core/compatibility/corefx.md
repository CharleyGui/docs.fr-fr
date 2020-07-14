---
title: Modifications importantes de la bibliothèque de classes de base
description: Répertorie les modifications avec rupture dans les bibliothèques .NET de base.
ms.date: 09/20/2019
ms.openlocfilehash: 64510809a1cf69ea0e4c4816eb2df54233e8eceb
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281298"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="95dea-103">Modifications importantes des bibliothèques .NET principales</span><span class="sxs-lookup"><span data-stu-id="95dea-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="95dea-104">Les bibliothèques .NET de base fournissent les primitives et d’autres types généraux utilisés par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95dea-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="95dea-105">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="95dea-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="95dea-106">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="95dea-106">Breaking change</span></span> | <span data-ttu-id="95dea-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="95dea-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="95dea-108">Le ActivityIdFormat par défaut est W3C</span><span class="sxs-lookup"><span data-stu-id="95dea-108">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="95dea-109">5.0</span><span class="sxs-lookup"><span data-stu-id="95dea-109">5.0</span></span> |
| [<span data-ttu-id="95dea-110">Changement de comportement pour Vector2. Lerp et Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="95dea-110">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="95dea-111">5.0</span><span class="sxs-lookup"><span data-stu-id="95dea-111">5.0</span></span> |
| [<span data-ttu-id="95dea-112">Les méthodes SSE et SSE2 CompareGreaterThan gèrent correctement les entrées NaN</span><span class="sxs-lookup"><span data-stu-id="95dea-112">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="95dea-113">5.0</span><span class="sxs-lookup"><span data-stu-id="95dea-113">5.0</span></span> |
| [<span data-ttu-id="95dea-114">CounterSet. CreateCounterSetInstance lève désormais une exception InvalidOperationException si l’instance existe déjà</span><span class="sxs-lookup"><span data-stu-id="95dea-114">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="95dea-115">5.0</span><span class="sxs-lookup"><span data-stu-id="95dea-115">5.0</span></span> |
| [<span data-ttu-id="95dea-116">Package Microsoft. DotNet. PlatformAbstractions supprimé</span><span class="sxs-lookup"><span data-stu-id="95dea-116">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="95dea-117">5.0</span><span class="sxs-lookup"><span data-stu-id="95dea-117">5.0</span></span> |
| [<span data-ttu-id="95dea-118">API qui signalent la version du produit et non de la version du fichier</span><span class="sxs-lookup"><span data-stu-id="95dea-118">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="95dea-119">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-119">3.0</span></span> |
| [<span data-ttu-id="95dea-120">Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive</span><span class="sxs-lookup"><span data-stu-id="95dea-120">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="95dea-121">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-121">3.0</span></span> |
| [<span data-ttu-id="95dea-122">Modifications du comportement de l’analyse et de la mise en forme à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="95dea-122">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="95dea-123">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-123">3.0</span></span> |
| [<span data-ttu-id="95dea-124">Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException</span><span class="sxs-lookup"><span data-stu-id="95dea-124">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="95dea-125">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-125">3.0</span></span> |
| [<span data-ttu-id="95dea-126">InvalidAsynchronousStateException déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="95dea-126">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="95dea-127">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-127">3.0</span></span> |
| [<span data-ttu-id="95dea-128">Le remplacement des séquences d’octets UTF-8 incorrectes suit les instructions Unicode</span><span class="sxs-lookup"><span data-stu-id="95dea-128">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="95dea-129">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-129">3.0</span></span> |
| [<span data-ttu-id="95dea-130">TypeDescriptionProviderAttribute déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="95dea-130">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="95dea-131">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-131">3.0</span></span> |
| [<span data-ttu-id="95dea-132">ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes</span><span class="sxs-lookup"><span data-stu-id="95dea-132">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="95dea-133">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-133">3.0</span></span> |
| [<span data-ttu-id="95dea-134">Le type d’exception du sérialiseur JSON est passé de JsonException à NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="95dea-134">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="95dea-135">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-135">3.0</span></span> |
| [<span data-ttu-id="95dea-136">Modification de la sémantique de (String) NULL dans Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="95dea-136">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="95dea-137">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-137">3.0</span></span> |
| [<span data-ttu-id="95dea-138">Les méthodes JsonEncodedText. Encode ont un argument JavaScriptEncoder supplémentaire</span><span class="sxs-lookup"><span data-stu-id="95dea-138">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="95dea-139">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-139">3.0</span></span> |
| [<span data-ttu-id="95dea-140">Signature de JsonFactoryConverter. CreateConverter modifiée</span><span class="sxs-lookup"><span data-stu-id="95dea-140">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="95dea-141">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-141">3.0</span></span> |
| [<span data-ttu-id="95dea-142">Modifications de l’API JsonElement</span><span class="sxs-lookup"><span data-stu-id="95dea-142">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="95dea-143">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-143">3.0</span></span> |
| [<span data-ttu-id="95dea-144">FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule</span><span class="sxs-lookup"><span data-stu-id="95dea-144">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="95dea-145">3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-145">3.0</span></span> |
| [<span data-ttu-id="95dea-146">Champs privés ajoutés aux types struct intégrés</span><span class="sxs-lookup"><span data-stu-id="95dea-146">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="95dea-147">2.1</span><span class="sxs-lookup"><span data-stu-id="95dea-147">2.1</span></span> |
| [<span data-ttu-id="95dea-148">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="95dea-148">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="95dea-149">2.1</span><span class="sxs-lookup"><span data-stu-id="95dea-149">2.1</span></span> |
| [<span data-ttu-id="95dea-150">Versions OpenSSL sur macOS</span><span class="sxs-lookup"><span data-stu-id="95dea-150">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="95dea-151">2.1</span><span class="sxs-lookup"><span data-stu-id="95dea-151">2.1</span></span> |
| [<span data-ttu-id="95dea-152">UnauthorizedAccessException levée par FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="95dea-152">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="95dea-153">1.0</span><span class="sxs-lookup"><span data-stu-id="95dea-153">1.0</span></span> |
| [<span data-ttu-id="95dea-154">La gestion des exceptions d’état de processus endommagées n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="95dea-154">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="95dea-155">1.0</span><span class="sxs-lookup"><span data-stu-id="95dea-155">1.0</span></span> |
| [<span data-ttu-id="95dea-156">Les propriétés UriBuilder n’ajoutent plus de caractères de début</span><span class="sxs-lookup"><span data-stu-id="95dea-156">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="95dea-157">1.0</span><span class="sxs-lookup"><span data-stu-id="95dea-157">1.0</span></span> |
| [<span data-ttu-id="95dea-158">Process. StartInfo lève une exception InvalidOperationException pour les processus que vous n’avez pas démarrés</span><span class="sxs-lookup"><span data-stu-id="95dea-158">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="95dea-159">1.0</span><span class="sxs-lookup"><span data-stu-id="95dea-159">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="95dea-160">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="95dea-160">.NET 5.0</span></span>

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

## <a name="net-core-30"></a><span data-ttu-id="95dea-161">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="95dea-161">.NET Core 3.0</span></span>

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

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="95dea-162">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="95dea-162">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="95dea-163">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="95dea-163">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
