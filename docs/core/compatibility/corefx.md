---
title: Changement de rupture de bibliothèque de classe de base
description: Répertorie les changements de rupture dans les bibliothèques de base .NET.
ms.date: 09/20/2019
ms.openlocfilehash: 8cf90ca2bc8736101c1cb8d327a93d100148937b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021829"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="8175a-103">Core .NET bibliothèques briser les changements</span><span class="sxs-lookup"><span data-stu-id="8175a-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="8175a-104">Les bibliothèques de base .NET fournissent les primitifs et autres types généraux utilisés par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8175a-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="8175a-105">Les modifications de rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="8175a-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="8175a-106">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="8175a-106">Breaking change</span></span> | <span data-ttu-id="8175a-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="8175a-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="8175a-108">API qui signalent la version signalent maintenant le produit et ne fichier pas la version</span><span class="sxs-lookup"><span data-stu-id="8175a-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="8175a-109">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-109">3.0</span></span> |
| [<span data-ttu-id="8175a-110">Custom EncoderFallbackBuffer instances ne peuvent pas se replier de façon récursive</span><span class="sxs-lookup"><span data-stu-id="8175a-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="8175a-111">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-111">3.0</span></span> |
| [<span data-ttu-id="8175a-112">Modifications de comportement de formatage et d’analyse des points flottants</span><span class="sxs-lookup"><span data-stu-id="8175a-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="8175a-113">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-113">3.0</span></span> |
| [<span data-ttu-id="8175a-114">Les opérations d’analyse des points flottants ne échouent plus ou ne jettent plus de OverflowException</span><span class="sxs-lookup"><span data-stu-id="8175a-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="8175a-115">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-115">3.0</span></span> |
| [<span data-ttu-id="8175a-116">InvalidAsynchroneStateException a déménagé à une autre assemblée</span><span class="sxs-lookup"><span data-stu-id="8175a-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="8175a-117">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-117">3.0</span></span> |
| [<span data-ttu-id="8175a-118">NET Core 3.0 suit les meilleures pratiques d’Unicode lors du remplacement des séquences de byte UTF-8 mal formées</span><span class="sxs-lookup"><span data-stu-id="8175a-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="8175a-119">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-119">3.0</span></span> |
| [<span data-ttu-id="8175a-120">TypeDescriptionProviderAttribute a déménagé à un autre assemblage</span><span class="sxs-lookup"><span data-stu-id="8175a-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="8175a-121">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-121">3.0</span></span> |
| [<span data-ttu-id="8175a-122">ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes</span><span class="sxs-lookup"><span data-stu-id="8175a-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="8175a-123">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-123">3.0</span></span> |
| [<span data-ttu-id="8175a-124">JSON serializer type d’exception changé de JsonException à NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="8175a-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="8175a-125">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-125">3.0</span></span> |
| [<span data-ttu-id="8175a-126">Changement de sémantique de (corde)null dans Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="8175a-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="8175a-127">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-127">3.0</span></span> |
| [<span data-ttu-id="8175a-128">Les méthodes JsonEncodedText.Encode ont un argument JavaScriptEncoder supplémentaire</span><span class="sxs-lookup"><span data-stu-id="8175a-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="8175a-129">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-129">3.0</span></span> |
| [<span data-ttu-id="8175a-130">JsonFactoryConverter.CreateConverter signature changé</span><span class="sxs-lookup"><span data-stu-id="8175a-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="8175a-131">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-131">3.0</span></span> |
| [<span data-ttu-id="8175a-132">Modifications de l’API JsonElement</span><span class="sxs-lookup"><span data-stu-id="8175a-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="8175a-133">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-133">3.0</span></span> |
| [<span data-ttu-id="8175a-134">FieldInfo.SetValue jette l’exception pour les champs statiques et init-seulement</span><span class="sxs-lookup"><span data-stu-id="8175a-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="8175a-135">3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-135">3.0</span></span> |
| [<span data-ttu-id="8175a-136">Champs privés ajoutés aux types de struct intégrés</span><span class="sxs-lookup"><span data-stu-id="8175a-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="8175a-137">2.1</span><span class="sxs-lookup"><span data-stu-id="8175a-137">2.1</span></span> |
| [<span data-ttu-id="8175a-138">Variation de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="8175a-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="8175a-139">2.1</span><span class="sxs-lookup"><span data-stu-id="8175a-139">2.1</span></span> |
| [<span data-ttu-id="8175a-140">Versions OpenSSL sur macOS</span><span class="sxs-lookup"><span data-stu-id="8175a-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="8175a-141">2.1</span><span class="sxs-lookup"><span data-stu-id="8175a-141">2.1</span></span> |
| [<span data-ttu-id="8175a-142">UnauthorizedAccessException jeté par FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="8175a-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="8175a-143">1.0</span><span class="sxs-lookup"><span data-stu-id="8175a-143">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="8175a-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8175a-144">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="8175a-145">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8175a-145">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="8175a-146">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8175a-146">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
