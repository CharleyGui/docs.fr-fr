---
title: Modifications importantes de la bibliothèque de classes de base
description: Répertorie les modifications avec rupture dans les bibliothèques .NET de base.
ms.date: 09/20/2019
ms.openlocfilehash: ca50123b842c256607d47010dbef9b216ece4661
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420425"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="cb8ce-103">Modifications importantes des bibliothèques .NET principales</span><span class="sxs-lookup"><span data-stu-id="cb8ce-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="cb8ce-104">Les bibliothèques .NET de base fournissent les primitives et d’autres types généraux utilisés par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb8ce-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="cb8ce-105">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="cb8ce-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="cb8ce-106">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="cb8ce-106">Breaking change</span></span> | <span data-ttu-id="cb8ce-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="cb8ce-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="cb8ce-108">Les méthodes SSE et SSE2 CompareGreaterThan gèrent correctement les entrées NaN</span><span class="sxs-lookup"><span data-stu-id="cb8ce-108">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="cb8ce-109">5.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-109">5.0</span></span> |
| [<span data-ttu-id="cb8ce-110">API qui signalent la version du produit et non de la version du fichier</span><span class="sxs-lookup"><span data-stu-id="cb8ce-110">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="cb8ce-111">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-111">3.0</span></span> |
| [<span data-ttu-id="cb8ce-112">Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive</span><span class="sxs-lookup"><span data-stu-id="cb8ce-112">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="cb8ce-113">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-113">3.0</span></span> |
| [<span data-ttu-id="cb8ce-114">Modifications du comportement de l’analyse et de la mise en forme à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="cb8ce-114">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="cb8ce-115">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-115">3.0</span></span> |
| [<span data-ttu-id="cb8ce-116">Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException</span><span class="sxs-lookup"><span data-stu-id="cb8ce-116">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="cb8ce-117">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-117">3.0</span></span> |
| [<span data-ttu-id="cb8ce-118">InvalidAsynchronousStateException déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="cb8ce-118">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="cb8ce-119">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-119">3.0</span></span> |
| [<span data-ttu-id="cb8ce-120">Le remplacement des séquences d’octets UTF-8 incorrectes suit les instructions Unicode</span><span class="sxs-lookup"><span data-stu-id="cb8ce-120">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="cb8ce-121">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-121">3.0</span></span> |
| [<span data-ttu-id="cb8ce-122">TypeDescriptionProviderAttribute déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="cb8ce-122">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="cb8ce-123">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-123">3.0</span></span> |
| [<span data-ttu-id="cb8ce-124">ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes</span><span class="sxs-lookup"><span data-stu-id="cb8ce-124">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="cb8ce-125">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-125">3.0</span></span> |
| [<span data-ttu-id="cb8ce-126">Le type d’exception du sérialiseur JSON est passé de JsonException à NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="cb8ce-126">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="cb8ce-127">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-127">3.0</span></span> |
| [<span data-ttu-id="cb8ce-128">Modification de la sémantique de (String) NULL dans Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="cb8ce-128">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="cb8ce-129">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-129">3.0</span></span> |
| [<span data-ttu-id="cb8ce-130">Les méthodes JsonEncodedText. Encode ont un argument JavaScriptEncoder supplémentaire</span><span class="sxs-lookup"><span data-stu-id="cb8ce-130">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="cb8ce-131">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-131">3.0</span></span> |
| [<span data-ttu-id="cb8ce-132">Signature de JsonFactoryConverter. CreateConverter modifiée</span><span class="sxs-lookup"><span data-stu-id="cb8ce-132">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="cb8ce-133">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-133">3.0</span></span> |
| [<span data-ttu-id="cb8ce-134">Modifications de l’API JsonElement</span><span class="sxs-lookup"><span data-stu-id="cb8ce-134">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="cb8ce-135">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-135">3.0</span></span> |
| [<span data-ttu-id="cb8ce-136">FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule</span><span class="sxs-lookup"><span data-stu-id="cb8ce-136">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="cb8ce-137">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-137">3.0</span></span> |
| [<span data-ttu-id="cb8ce-138">Champs privés ajoutés aux types struct intégrés</span><span class="sxs-lookup"><span data-stu-id="cb8ce-138">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="cb8ce-139">2.1</span><span class="sxs-lookup"><span data-stu-id="cb8ce-139">2.1</span></span> |
| [<span data-ttu-id="cb8ce-140">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="cb8ce-140">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="cb8ce-141">2.1</span><span class="sxs-lookup"><span data-stu-id="cb8ce-141">2.1</span></span> |
| [<span data-ttu-id="cb8ce-142">Versions OpenSSL sur macOS</span><span class="sxs-lookup"><span data-stu-id="cb8ce-142">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="cb8ce-143">2.1</span><span class="sxs-lookup"><span data-stu-id="cb8ce-143">2.1</span></span> |
| [<span data-ttu-id="cb8ce-144">UnauthorizedAccessException levée par FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="cb8ce-144">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="cb8ce-145">1.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-145">1.0</span></span> |
| [<span data-ttu-id="cb8ce-146">La gestion des exceptions d’état de processus endommagées n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="cb8ce-146">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="cb8ce-147">1.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-147">1.0</span></span> |
| [<span data-ttu-id="cb8ce-148">Les propriétés UriBuilder n’ajoutent plus de caractères de début</span><span class="sxs-lookup"><span data-stu-id="cb8ce-148">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="cb8ce-149">1.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-149">1.0</span></span> |
| [<span data-ttu-id="cb8ce-150">Process. StartInfo lève une exception InvalidOperationException pour les processus que vous n’avez pas démarrés</span><span class="sxs-lookup"><span data-stu-id="cb8ce-150">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="cb8ce-151">1.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-151">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="cb8ce-152">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-152">.NET 5.0</span></span>

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="cb8ce-153">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-153">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="cb8ce-154">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cb8ce-154">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="cb8ce-155">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="cb8ce-155">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
