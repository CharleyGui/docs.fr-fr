---
title: Changement de rupture de bibliothèque de classe de base
description: Répertorie les changements de rupture dans .NET CoreFx, la bibliothèque de la classe de base.
ms.date: 09/20/2019
ms.openlocfilehash: 56a3cf4f4c00a79752d5a98bb086bb9f8c0614b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147573"
---
# <a name="corefx-breaking-changes"></a>CoreFx briser les changements

CoreFx fournit les primitifs et autres types généraux utilisés par .NET Core.

Les modifications de rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | :-: |
| [API qui signalent la version signalent maintenant le produit et ne fichier pas la version](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [Custom EncoderFallbackBuffer instances ne peuvent pas se replier de façon récursive](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [Modifications de comportement de formatage et d’analyse des points flottants](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [Les opérations d’analyse des points flottants ne échouent plus ou ne jettent plus de OverflowException](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [InvalidAsynchroneStateException a déménagé à une autre assemblée](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [NET Core 3.0 suit les meilleures pratiques d’Unicode lors du remplacement des séquences de byte UTF-8 mal formées](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | 3.0 |
| [TypeDescriptionProviderAttribute a déménagé à un autre assemblage](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [JSON serializer type d’exception changé de JsonException à NotSupportedException](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | 3.0 |
| [Changement de sémantique de (corde)null dans Utf8JsonWriter](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | 3.0 |
| [Les méthodes JsonEncodedText.Encode ont un argument JavaScriptEncoder supplémentaire](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | 3.0 |
| [JsonFactoryConverter.CreateConverter signature changé](#jsonfactoryconvertercreateconverter-signature-changed) | 3.0 |
| [Modifications de l’API JsonElement](#jsonelement-api-changes) | 3.0 |
| [FieldInfo.SetValue jette l’exception pour les champs statiques et init-seulement](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [Champs privés ajoutés aux types de struct intégrés](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [Variation de la valeur par défaut de UseShellExecute](#change-in-default-value-of-useshellexecute) | 2.1 |
| [Versions OpenSSL sur macOS](#openssl-versions-on-macos) | 2.1 |
| [UnauthorizedAccessException jeté par FileSystemInfo.Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |

## <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
