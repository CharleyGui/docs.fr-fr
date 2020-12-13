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
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a><span data-ttu-id="bc176-103">Principales modifications importantes des bibliothèques .NET dans .NET Core 1.0-3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-103">Core .NET libraries breaking changes in .NET Core 1.0-3.0</span></span>

<span data-ttu-id="bc176-104">Les bibliothèques .NET de base fournissent les primitives et d’autres types généraux utilisés par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bc176-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="bc176-105">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="bc176-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="bc176-106">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="bc176-106">Breaking change</span></span> | <span data-ttu-id="bc176-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="bc176-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="bc176-108">Passer GroupCollection à des méthodes d’extension en acceptant IEnumerable \<T> requiert une ambiguïté</span><span class="sxs-lookup"><span data-stu-id="bc176-108">Passing GroupCollection to extension methods taking IEnumerable\<T> requires disambiguation</span></span>](#passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation) | <span data-ttu-id="bc176-109">3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-109">3.0</span></span> |
| [<span data-ttu-id="bc176-110">API qui signalent la version du produit et non de la version du fichier</span><span class="sxs-lookup"><span data-stu-id="bc176-110">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="bc176-111">3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-111">3.0</span></span> |
| [<span data-ttu-id="bc176-112">Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive</span><span class="sxs-lookup"><span data-stu-id="bc176-112">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="bc176-113">3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-113">3.0</span></span> |
| [<span data-ttu-id="bc176-114">Modifications du comportement de l’analyse et de la mise en forme à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="bc176-114">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="bc176-115">3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-115">3.0</span></span> |
| [<span data-ttu-id="bc176-116">Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException</span><span class="sxs-lookup"><span data-stu-id="bc176-116">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="bc176-117">3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-117">3.0</span></span> |
| [<span data-ttu-id="bc176-118">InvalidAsynchronousStateException déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="bc176-118">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="bc176-119">3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-119">3.0</span></span> |
| [<span data-ttu-id="bc176-120">Le remplacement des séquences d’octets UTF-8 incorrectes suit les instructions Unicode</span><span class="sxs-lookup"><span data-stu-id="bc176-120">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="bc176-121">3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-121">3.0</span></span> |
| [<span data-ttu-id="bc176-122">TypeDescriptionProviderAttribute déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="bc176-122">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="bc176-123">3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-123">3.0</span></span> |
| [<span data-ttu-id="bc176-124">ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes</span><span class="sxs-lookup"><span data-stu-id="bc176-124">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="bc176-125">3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-125">3.0</span></span> |
| [<span data-ttu-id="bc176-126">FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule</span><span class="sxs-lookup"><span data-stu-id="bc176-126">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="bc176-127">3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-127">3.0</span></span> |
| [<span data-ttu-id="bc176-128">Champs privés ajoutés aux types struct intégrés</span><span class="sxs-lookup"><span data-stu-id="bc176-128">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="bc176-129">2.1</span><span class="sxs-lookup"><span data-stu-id="bc176-129">2.1</span></span> |
| [<span data-ttu-id="bc176-130">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="bc176-130">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="bc176-131">2.1</span><span class="sxs-lookup"><span data-stu-id="bc176-131">2.1</span></span> |
| [<span data-ttu-id="bc176-132">Versions OpenSSL sur macOS</span><span class="sxs-lookup"><span data-stu-id="bc176-132">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="bc176-133">2.1</span><span class="sxs-lookup"><span data-stu-id="bc176-133">2.1</span></span> |
| [<span data-ttu-id="bc176-134">UnauthorizedAccessException levée par FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="bc176-134">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="bc176-135">1.0</span><span class="sxs-lookup"><span data-stu-id="bc176-135">1.0</span></span> |
| [<span data-ttu-id="bc176-136">La gestion des exceptions d’état de processus endommagées n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="bc176-136">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="bc176-137">1.0</span><span class="sxs-lookup"><span data-stu-id="bc176-137">1.0</span></span> |
| [<span data-ttu-id="bc176-138">Les propriétés UriBuilder n’ajoutent plus de caractères de début</span><span class="sxs-lookup"><span data-stu-id="bc176-138">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="bc176-139">1.0</span><span class="sxs-lookup"><span data-stu-id="bc176-139">1.0</span></span> |
| [<span data-ttu-id="bc176-140">Process. StartInfo lève une exception InvalidOperationException pour les processus que vous n’avez pas démarrés</span><span class="sxs-lookup"><span data-stu-id="bc176-140">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="bc176-141">1.0</span><span class="sxs-lookup"><span data-stu-id="bc176-141">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="bc176-142">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="bc176-142">.NET Core 3.0</span></span>

[!INCLUDE [disambiguate-generic-type-for-groupcollection](../../../includes/core-changes/corefx/3.0/disambiguate-generic-type-for-groupcollection.md)]

***

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

<span data-ttu-id="bc176-143">\*\*_</span><span class="sxs-lookup"><span data-stu-id="bc176-143">\*\*_</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="bc176-144">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bc176-144">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="bc176-145">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="bc176-145">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="bc176-146">_\*\*</span><span class="sxs-lookup"><span data-stu-id="bc176-146">_\*\*</span></span>
