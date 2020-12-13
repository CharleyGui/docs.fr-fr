---
title: Modifications importantes de la bibliothèque .NET
description: Répertorie les dernières modifications dans les bibliothèques .NET principales pour .NET Core versions 1.0 à 3.0.
ms.date: 07/27/2020
ms.openlocfilehash: 092ff36a5e07c9e226fe2a67d5e7cfd391e9d16b
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366871"
---
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a>Principales modifications importantes des bibliothèques .NET dans .NET Core 1.0-3.0

Les bibliothèques .NET de base fournissent les primitives et d’autres types généraux utilisés par .NET Core.

Les modifications avec rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | :-: |
| [Passer GroupCollection à des méthodes d’extension en acceptant IEnumerable \<T> requiert une ambiguïté](#passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation) | 3.0 |
| [API qui signalent la version du produit et non de la version du fichier](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [Modifications du comportement de l’analyse et de la mise en forme à virgule flottante](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [InvalidAsynchronousStateException déplacé vers un autre assembly](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [Le remplacement des séquences d’octets UTF-8 incorrectes suit les instructions Unicode](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | 3.0 |
| [TypeDescriptionProviderAttribute déplacé vers un autre assembly](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [Champs privés ajoutés aux types struct intégrés](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [Modification de la valeur par défaut de UseShellExecute](#change-in-default-value-of-useshellexecute) | 2.1 |
| [Versions OpenSSL sur macOS](#openssl-versions-on-macos) | 2.1 |
| [UnauthorizedAccessException levée par FileSystemInfo. Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |
| [La gestion des exceptions d’état de processus endommagées n’est pas prise en charge](#handling-corrupted-state-exceptions-is-not-supported) | 1.0 |
| [Les propriétés UriBuilder n’ajoutent plus de caractères de début](#uribuilder-properties-no-longer-prepend-leading-characters) | 1.0 |
| [Process. StartInfo lève une exception InvalidOperationException pour les processus que vous n’avez pas démarrés](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | 1.0 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE [disambiguate-generic-type-for-groupcollection](../../../includes/core-changes/corefx/3.0/disambiguate-generic-type-for-groupcollection.md)]

***

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

**_

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

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

_**
