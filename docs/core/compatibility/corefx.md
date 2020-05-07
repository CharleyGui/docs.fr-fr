---
title: Modifications importantes de la bibliothèque de classes de base
description: Répertorie les modifications avec rupture dans les bibliothèques .NET de base.
ms.date: 09/20/2019
ms.openlocfilehash: a2eb4be89d78f50d201272f3449374bc27d8c785
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859931"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="81b5e-103">Modifications importantes des bibliothèques .NET principales</span><span class="sxs-lookup"><span data-stu-id="81b5e-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="81b5e-104">Les bibliothèques .NET de base fournissent les primitives et d’autres types généraux utilisés par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="81b5e-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="81b5e-105">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="81b5e-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="81b5e-106">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="81b5e-106">Breaking change</span></span> | <span data-ttu-id="81b5e-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="81b5e-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="81b5e-108">Les méthodes SSE et SSE2 CompareGreaterThan gèrent correctement les entrées NaN</span><span class="sxs-lookup"><span data-stu-id="81b5e-108">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="81b5e-109">5.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-109">5.0</span></span> |
| [<span data-ttu-id="81b5e-110">API qui signalent la version du produit et non de la version du fichier</span><span class="sxs-lookup"><span data-stu-id="81b5e-110">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="81b5e-111">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-111">3.0</span></span> |
| [<span data-ttu-id="81b5e-112">Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive</span><span class="sxs-lookup"><span data-stu-id="81b5e-112">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="81b5e-113">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-113">3.0</span></span> |
| [<span data-ttu-id="81b5e-114">Modifications du comportement de l’analyse et de la mise en forme à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="81b5e-114">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="81b5e-115">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-115">3.0</span></span> |
| [<span data-ttu-id="81b5e-116">Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException</span><span class="sxs-lookup"><span data-stu-id="81b5e-116">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="81b5e-117">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-117">3.0</span></span> |
| [<span data-ttu-id="81b5e-118">InvalidAsynchronousStateException déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="81b5e-118">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="81b5e-119">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-119">3.0</span></span> |
| [<span data-ttu-id="81b5e-120">Le remplacement des séquences d’octets UTF-8 incorrectes suit les instructions Unicode</span><span class="sxs-lookup"><span data-stu-id="81b5e-120">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="81b5e-121">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-121">3.0</span></span> |
| [<span data-ttu-id="81b5e-122">TypeDescriptionProviderAttribute déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="81b5e-122">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="81b5e-123">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-123">3.0</span></span> |
| [<span data-ttu-id="81b5e-124">ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes</span><span class="sxs-lookup"><span data-stu-id="81b5e-124">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="81b5e-125">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-125">3.0</span></span> |
| [<span data-ttu-id="81b5e-126">Le type d’exception du sérialiseur JSON est passé de JsonException à NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="81b5e-126">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="81b5e-127">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-127">3.0</span></span> |
| [<span data-ttu-id="81b5e-128">Modification de la sémantique de (String) NULL dans Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="81b5e-128">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="81b5e-129">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-129">3.0</span></span> |
| [<span data-ttu-id="81b5e-130">Les méthodes JsonEncodedText. Encode ont un argument JavaScriptEncoder supplémentaire</span><span class="sxs-lookup"><span data-stu-id="81b5e-130">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="81b5e-131">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-131">3.0</span></span> |
| [<span data-ttu-id="81b5e-132">Signature de JsonFactoryConverter. CreateConverter modifiée</span><span class="sxs-lookup"><span data-stu-id="81b5e-132">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="81b5e-133">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-133">3.0</span></span> |
| [<span data-ttu-id="81b5e-134">Modifications de l’API JsonElement</span><span class="sxs-lookup"><span data-stu-id="81b5e-134">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="81b5e-135">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-135">3.0</span></span> |
| [<span data-ttu-id="81b5e-136">FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule</span><span class="sxs-lookup"><span data-stu-id="81b5e-136">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="81b5e-137">3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-137">3.0</span></span> |
| [<span data-ttu-id="81b5e-138">Champs privés ajoutés aux types struct intégrés</span><span class="sxs-lookup"><span data-stu-id="81b5e-138">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="81b5e-139">2.1</span><span class="sxs-lookup"><span data-stu-id="81b5e-139">2.1</span></span> |
| [<span data-ttu-id="81b5e-140">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="81b5e-140">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="81b5e-141">2.1</span><span class="sxs-lookup"><span data-stu-id="81b5e-141">2.1</span></span> |
| [<span data-ttu-id="81b5e-142">Versions OpenSSL sur macOS</span><span class="sxs-lookup"><span data-stu-id="81b5e-142">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="81b5e-143">2.1</span><span class="sxs-lookup"><span data-stu-id="81b5e-143">2.1</span></span> |
| [<span data-ttu-id="81b5e-144">UnauthorizedAccessException levée par FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="81b5e-144">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="81b5e-145">1.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-145">1.0</span></span> |
| [<span data-ttu-id="81b5e-146">La gestion des exceptions d’état de processus endommagées n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="81b5e-146">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="81b5e-147">1.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-147">1.0</span></span> |
| [<span data-ttu-id="81b5e-148">Les propriétés UriBuilder n’ajoutent plus de caractères de début</span><span class="sxs-lookup"><span data-stu-id="81b5e-148">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="81b5e-149">1.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-149">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="81b5e-150">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="81b5e-150">.NET 5.0</span></span>

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="81b5e-151">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-151">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="81b5e-152">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="81b5e-152">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="81b5e-153">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="81b5e-153">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***
