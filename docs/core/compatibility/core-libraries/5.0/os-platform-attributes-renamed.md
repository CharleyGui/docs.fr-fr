---
title: 'Modification avec rupture : attributs OSPlatform renommés ou supprimés'
description: En savoir plus sur le changement critique .NET 5,0 dans les bibliothèques .NET de base où les attributs de plateforme de système d’exploitation qui ont été introduits dans une version préliminaire ont été supprimés ou renommés.
ms.date: 11/01/2020
ms.openlocfilehash: be2ddd4909bef70f531ca48246f091923d6435ec
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739488"
---
# <a name="osplatform-attributes-renamed-or-removed"></a><span data-ttu-id="6d5a3-103">Les attributs OSPlatform ont été renommés ou supprimés</span><span class="sxs-lookup"><span data-stu-id="6d5a3-103">OSPlatform attributes renamed or removed</span></span>

<span data-ttu-id="6d5a3-104">Les attributs suivants qui ont été introduits dans .NET 5,0 Preview 8 ont été supprimés ou renommés : `MinimumOSPlatformAttribute` , `RemovedInOSPlatformAttribute` et `ObsoletedInOSPlatformAttribute` .</span><span class="sxs-lookup"><span data-stu-id="6d5a3-104">The following attributes that were introduced in .NET 5.0 Preview 8 have been removed or renamed: `MinimumOSPlatformAttribute`, `RemovedInOSPlatformAttribute`, and `ObsoletedInOSPlatformAttribute`.</span></span>

## <a name="change-description"></a><span data-ttu-id="6d5a3-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="6d5a3-105">Change description</span></span>

<span data-ttu-id="6d5a3-106">.NET 5,0 Preview 8 a introduit les attributs suivants dans l' <xref:System.Runtime.Versioning> espace de noms :</span><span class="sxs-lookup"><span data-stu-id="6d5a3-106">.NET 5.0 Preview 8 introduced the following attributes in the <xref:System.Runtime.Versioning> namespace:</span></span>

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

<span data-ttu-id="6d5a3-107">Dans .NET 5,0 Preview 8, lorsqu’un projet cible une version spécifique du système d’exploitation de .NET 5 à l’aide d’un [moniker de Framework cible](../../../../standard/frameworks.md) tel que `net5.0-windows` , la génération ajoute un attribut de niveau assembly `System.Runtime.Versioning.MinimumOSPlatformAttribute` .</span><span class="sxs-lookup"><span data-stu-id="6d5a3-107">In .NET 5.0 Preview 8, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level `System.Runtime.Versioning.MinimumOSPlatformAttribute` attribute.</span></span>

<span data-ttu-id="6d5a3-108">Dans .NET 5,0 RC1, `ObsoletedInOSPlatformAttribute` a été supprimé et `MinimumOSPlatformAttribute` et et `RemovedInOSPlatformAttribute` ont été renommés comme suit :</span><span class="sxs-lookup"><span data-stu-id="6d5a3-108">In .NET 5.0 RC1, the `ObsoletedInOSPlatformAttribute` has been removed, and `MinimumOSPlatformAttribute` and `RemovedInOSPlatformAttribute` have been renamed as follows:</span></span>

| <span data-ttu-id="6d5a3-109">Nom de l’aperçu 8</span><span class="sxs-lookup"><span data-stu-id="6d5a3-109">Preview 8 name</span></span> | <span data-ttu-id="6d5a3-110">RC1 et nom ultérieur</span><span class="sxs-lookup"><span data-stu-id="6d5a3-110">RC1 and later name</span></span> |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

<span data-ttu-id="6d5a3-111">Dans .NET 5,0 RC1 et versions ultérieures, quand un projet cible une version spécifique du système d’exploitation de .NET 5 à l’aide d’un [moniker de Framework cible](../../../../standard/frameworks.md) tel que `net5.0-windows` , la génération ajoute un attribut de niveau assembly <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> .</span><span class="sxs-lookup"><span data-stu-id="6d5a3-111">In .NET 5.0 RC1 and later, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> attribute.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="6d5a3-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="6d5a3-112">Reason for change</span></span>

<span data-ttu-id="6d5a3-113">.NET 5,0 Preview 8 a introduit des attributs dans <xref:System.Runtime.Versioning> pour spécifier les plateformes prises en charge pour les API.</span><span class="sxs-lookup"><span data-stu-id="6d5a3-113">.NET 5.0 Preview 8 introduced attributes in <xref:System.Runtime.Versioning> to specify supported platforms for APIs.</span></span> <span data-ttu-id="6d5a3-114">Les attributs sont consommés par l' [Analyseur de compatibilité](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) de la plateforme pour produire des avertissements de génération lorsque des API spécifiques à la plateforme sont consommées sur des plateformes qui ne prennent pas en charge ces API.</span><span class="sxs-lookup"><span data-stu-id="6d5a3-114">The attributes are consumed by the [Platform compatibility analyzer](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) to produce build warnings when platform-specific APIs are consumed on platforms that don't support those APIs.</span></span>

<span data-ttu-id="6d5a3-115">Pour .NET 5,0 RC1, une fonctionnalité supplémentaire a été ajoutée à l’analyseur de compatibilité de plateforme pour l’exclusion de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="6d5a3-115">For .NET 5.0 RC1, an additional feature was added to the platform compatibility analyzer for platform exclusion.</span></span> <span data-ttu-id="6d5a3-116">Cette fonctionnalité permet aux API d’être marquées comme étant entièrement non prises en charge sur les plateformes de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="6d5a3-116">The feature allows APIs to be marked as entirely unsupported on OS platforms.</span></span> <span data-ttu-id="6d5a3-117">Cette fonctionnalité vous invite à modifier les attributs, notamment en utilisant des noms plus appropriés.</span><span class="sxs-lookup"><span data-stu-id="6d5a3-117">That feature prompted changes to the attributes, including using more suitable names.</span></span> <span data-ttu-id="6d5a3-118">`ObsoletedInOSPlatformAttribute`A été supprimé, car il n’était plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6d5a3-118">The `ObsoletedInOSPlatformAttribute` was removed because it was no longer needed.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="6d5a3-119">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6d5a3-119">Version introduced</span></span>

<span data-ttu-id="6d5a3-120">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="6d5a3-120">5.0 RC1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="6d5a3-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6d5a3-121">Recommended action</span></span>

<span data-ttu-id="6d5a3-122">Lorsque vous reciblez votre projet de .NET 5,0 Preview 8 vers .NET 5,0 RC1, vous pouvez rencontrer des erreurs de build ou d’exécution en raison de ces modifications.</span><span class="sxs-lookup"><span data-stu-id="6d5a3-122">When you retarget your project from .NET 5.0 Preview 8 to .NET 5.0 RC1, you might encounter build or run-time errors due to these changes.</span></span> <span data-ttu-id="6d5a3-123">Par exemple, le changement de nom de `MinimumOSPlatformAttribute` est susceptible de générer des erreurs, car l’attribut est appliqué aux assemblys spécifiques à la plateforme au moment de la génération, et les anciens artefacts de build feront toujours référence à l’ancien nom de l’API.</span><span class="sxs-lookup"><span data-stu-id="6d5a3-123">For example, the renaming of `MinimumOSPlatformAttribute` is likely to produce errors, because the attribute is applied to platform-specific assemblies at build time, and old build artifacts will still reference the old API name.</span></span>

<span data-ttu-id="6d5a3-124">Exemples d’erreurs de génération :</span><span class="sxs-lookup"><span data-stu-id="6d5a3-124">Example build-time errors:</span></span>

- <span data-ttu-id="6d5a3-125">**erreur CS0246 : le nom du type ou de l’espace de noms’MinimumOSPlatformAttribute’est introuvable (une directive using ou une référence d’assembly est-elle manquante ?)**</span><span class="sxs-lookup"><span data-stu-id="6d5a3-125">**error CS0246: The type or namespace name 'MinimumOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="6d5a3-126">**erreur CS0246 : le nom du type ou de l’espace de noms’RemovedInOSPlatformAttribute’est introuvable (une directive using ou une référence d’assembly est-elle manquante ?)**</span><span class="sxs-lookup"><span data-stu-id="6d5a3-126">**error CS0246: The type or namespace name 'RemovedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="6d5a3-127">**erreur CS0246 : le nom du type ou de l’espace de noms’ObsoletedInOSPlatformAttribute’est introuvable (une directive using ou une référence d’assembly est-elle manquante ?)**</span><span class="sxs-lookup"><span data-stu-id="6d5a3-127">**error CS0246: The type or namespace name 'ObsoletedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="6d5a3-128">Exemple d’erreur au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="6d5a3-128">Example run-time error:</span></span>

<span data-ttu-id="6d5a3-129">**Exception non gérée. System. TypeLoadException : impossible de charger le type’System. Runtime. Versioning. MinimumOSPlatformAttribute’à partir de l’assembly’System. Runtime, version = 5.0.0.0, culture = neutral, PublicKeyToken = b03f5f7f11d50a3a'.**</span><span class="sxs-lookup"><span data-stu-id="6d5a3-129">**Unhandled exception. System.TypeLoadException: Could not load type 'System.Runtime.Versioning.MinimumOSPlatformAttribute' from assembly 'System.Runtime, Version=5.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'.**</span></span>

<span data-ttu-id="6d5a3-130">Pour résoudre ces erreurs :</span><span class="sxs-lookup"><span data-stu-id="6d5a3-130">To resolve these errors:</span></span>

- <span data-ttu-id="6d5a3-131">Met à jour toutes les références de `MinimumOSPlatformAttribute` à <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> .</span><span class="sxs-lookup"><span data-stu-id="6d5a3-131">Update any references of `MinimumOSPlatformAttribute` to <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="6d5a3-132">Met à jour toutes les références de `RemovedInOSPlatformAttribute` à <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> .</span><span class="sxs-lookup"><span data-stu-id="6d5a3-132">Update any references of `RemovedInOSPlatformAttribute` to <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="6d5a3-133">Supprimez toutes les références à `ObsoletedInOSPlatformAttribute` .</span><span class="sxs-lookup"><span data-stu-id="6d5a3-133">Remove any references to `ObsoletedInOSPlatformAttribute`.</span></span>
- <span data-ttu-id="6d5a3-134">Régénérez votre projet (ou effectuez une génération + Build) pour supprimer les anciens artefacts de Build.</span><span class="sxs-lookup"><span data-stu-id="6d5a3-134">Rebuild your project (or perform clean + build) to delete old build artifacts.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="6d5a3-135">API affectées</span><span class="sxs-lookup"><span data-stu-id="6d5a3-135">Affected APIs</span></span>

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
