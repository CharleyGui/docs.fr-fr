---
title: Modifications importantes de la bibliothèque de classes de base
description: Répertorie les modifications avec rupture dans les bibliothèques .NET de base.
ms.date: 07/27/2020
ms.openlocfilehash: 8b8fb9b88edf4f1e5f83ef7c21f1712af40479fd
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359132"
---
# <a name="core-net-libraries-breaking-changes"></a>Modifications importantes des bibliothèques .NET principales

Les bibliothèques .NET de base fournissent les primitives et d’autres types généraux utilisés par .NET Core.

Les modifications avec rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | :-: |
| [Les contrôles de IsSupported intrinsèques matériels peuvent être différents pour les types imbriqués](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | 5.0 |
| [Noms de paramètres modifiés dans les assemblys de référence](#parameter-names-changed-in-reference-assemblies) | 5.0 |
| [Les chemins d’accès URI avec des caractères non-ASCII sont analysés correctement sur UNIX](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | 5.0 |
| [Reconnaissance d’URI de chemins d’accès UNC sur UNIX](#uri-recognition-of-unc-paths-on-unix) | 5.0 |
| [Environment. OSVersion retourne la version appropriée du système d’exploitation](#environmentosversion-returns-the-correct-operating-system-version) | 5.0 |
| [Complexité de LINQ OrderBy. la première {OrDefault} a augmenté](#complexity-of-linq-orderbyfirstordefault-increased) | 5.0 |
| [IntPtr et UIntPtr implémentent IFormattable](#intptr-and-uintptr-implement-iformattable) | 5.0 |
| [PrincipalPermissionAttribute est obsolète en tant qu’erreur](#principalpermissionattribute-is-obsolete-as-error) | 5.0 |
| [Les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | 5.0 |
| [Les chemins d’accès de code UTF-7 sont obsolètes](#utf-7-code-paths-are-obsolete) | 5.0 |
| [Vector \<T> lève toujours l’exception NotSupportedException pour les types non pris en charge](#vectort-always-throws-notsupportedexception-for-unsupported-types) | 5.0 |
| [Le ActivityIdFormat par défaut est W3C](#default-activityidformat-is-w3c) | 5.0 |
| [Changement de comportement pour Vector2. Lerp et Vector4. Lerp](#behavior-change-for-vector2lerp-and-vector4lerp) | 5.0 |
| [Les méthodes SSE et SSE2 CompareGreaterThan gèrent correctement les entrées NaN](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | 5.0 |
| [CounterSet. CreateCounterSetInstance lève désormais une exception InvalidOperationException si l’instance existe déjà](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | 5.0 |
| [Package Microsoft. DotNet. PlatformAbstractions supprimé](#microsoftdotnetplatformabstractions-package-removed) | 5.0 |
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

## <a name="net-50"></a>.NET 5,0

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

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
