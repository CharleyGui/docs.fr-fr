---
ms.openlocfilehash: 8c739d8f355ffa6a6e09cbe4c531b188acede5bd
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720299"
---
### <a name="osplatform-attributes-renamed-or-removed"></a><span data-ttu-id="74ad3-101">Attributs OSPlatform renommés ou supprimés</span><span class="sxs-lookup"><span data-stu-id="74ad3-101">OSPlatform attributes renamed or removed</span></span>

<span data-ttu-id="74ad3-102">Les attributs suivants qui ont été introduits dans .NET 5,0 Preview 8 ont été supprimés ou renommés : `MinimumOSPlatformAttribute` , `RemovedInOSPlatformAttribute` et `ObsoletedInOSPlatformAttribute` .</span><span class="sxs-lookup"><span data-stu-id="74ad3-102">The following attributes that were introduced in .NET 5.0 Preview 8 have been removed or renamed: `MinimumOSPlatformAttribute`, `RemovedInOSPlatformAttribute`, and `ObsoletedInOSPlatformAttribute`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="74ad3-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="74ad3-103">Change description</span></span>

<span data-ttu-id="74ad3-104">.NET 5,0 Preview 8 a introduit les attributs suivants dans l' <xref:System.Runtime.Versioning> espace de noms :</span><span class="sxs-lookup"><span data-stu-id="74ad3-104">.NET 5.0 Preview 8 introduced the following attributes in the <xref:System.Runtime.Versioning> namespace:</span></span>

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

<span data-ttu-id="74ad3-105">Dans .NET 5,0 Preview 8, lorsqu’un projet cible une version spécifique du système d’exploitation de .NET 5 à l’aide d’un [moniker de Framework cible](../../../../docs/standard/frameworks.md) tel que `net5.0-windows` , la génération ajoute un attribut de niveau assembly `System.Runtime.Versioning.MinimumOSPlatformAttribute` .</span><span class="sxs-lookup"><span data-stu-id="74ad3-105">In .NET 5.0 Preview 8, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../docs/standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level `System.Runtime.Versioning.MinimumOSPlatformAttribute` attribute.</span></span>

<span data-ttu-id="74ad3-106">Dans .NET 5,0 RC1, `ObsoletedInOSPlatformAttribute` a été supprimé et `MinimumOSPlatformAttribute` et et `RemovedInOSPlatformAttribute` ont été renommés comme suit :</span><span class="sxs-lookup"><span data-stu-id="74ad3-106">In .NET 5.0 RC1, the `ObsoletedInOSPlatformAttribute` has been removed, and `MinimumOSPlatformAttribute` and `RemovedInOSPlatformAttribute` have been renamed as follows:</span></span>

| <span data-ttu-id="74ad3-107">Nom de l’aperçu 8</span><span class="sxs-lookup"><span data-stu-id="74ad3-107">Preview 8 name</span></span> | <span data-ttu-id="74ad3-108">RC1 et nom ultérieur</span><span class="sxs-lookup"><span data-stu-id="74ad3-108">RC1 and later name</span></span> |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

<span data-ttu-id="74ad3-109">Dans .NET 5,0 RC1 et versions ultérieures, quand un projet cible une version spécifique du système d’exploitation de .NET 5 à l’aide d’un [moniker de Framework cible](../../../../docs/standard/frameworks.md) tel que `net5.0-windows` , la génération ajoute un attribut de niveau assembly <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> .</span><span class="sxs-lookup"><span data-stu-id="74ad3-109">In .NET 5.0 RC1 and later, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../docs/standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> attribute.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="74ad3-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="74ad3-110">Reason for change</span></span>

<span data-ttu-id="74ad3-111">.NET 5,0 Preview 8 a introduit des attributs dans <xref:System.Runtime.Versioning> pour spécifier les plateformes prises en charge pour les API.</span><span class="sxs-lookup"><span data-stu-id="74ad3-111">.NET 5.0 Preview 8 introduced attributes in <xref:System.Runtime.Versioning> to specify supported platforms for APIs.</span></span> <span data-ttu-id="74ad3-112">Les attributs sont consommés par l' [Analyseur de compatibilité](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) de la plateforme pour produire des avertissements de génération lorsque des API spécifiques à la plateforme sont consommées sur des plateformes qui ne sont pas prises en charge par ces API.</span><span class="sxs-lookup"><span data-stu-id="74ad3-112">The attributes are consumed by the [Platform compatibility analyzer](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) to produce build warnings when platform-specific APIs are consumed on platforms that don't supported those APIs.</span></span>

<span data-ttu-id="74ad3-113">Pour .NET 5,0 RC1, une fonctionnalité supplémentaire a été ajoutée à l’analyseur de compatibilité de plateforme pour l’exclusion de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="74ad3-113">For .NET 5.0 RC1, an additional feature was added to the platform compatibility analyzer for platform exclusion.</span></span> <span data-ttu-id="74ad3-114">Cette fonctionnalité permet aux API d’être marquées comme étant entièrement non prises en charge sur les plateformes de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="74ad3-114">The feature allows APIs to be marked as entirely unsupported on OS platforms.</span></span> <span data-ttu-id="74ad3-115">Cette fonctionnalité vous invite à modifier les attributs, notamment en utilisant des noms plus appropriés.</span><span class="sxs-lookup"><span data-stu-id="74ad3-115">That feature prompted changes to the attributes, including using more suitable names.</span></span> <span data-ttu-id="74ad3-116">`ObsoletedInOSPlatformAttribute`A été supprimé, car il n’était plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="74ad3-116">The `ObsoletedInOSPlatformAttribute` was removed because it was no longer needed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="74ad3-117">Version introduite</span><span class="sxs-lookup"><span data-stu-id="74ad3-117">Version introduced</span></span>

<span data-ttu-id="74ad3-118">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="74ad3-118">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="74ad3-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="74ad3-119">Recommended action</span></span>

<span data-ttu-id="74ad3-120">Lorsque vous reciblez votre projet de .NET 5,0 Preview 8 vers .NET 5,0 RC1, vous pouvez rencontrer des erreurs de build ou d’exécution en raison de ces modifications.</span><span class="sxs-lookup"><span data-stu-id="74ad3-120">When you retarget your project from .NET 5.0 Preview 8 to .NET 5.0 RC1, you might encounter build or run-time errors due to these changes.</span></span> <span data-ttu-id="74ad3-121">Par exemple, le changement de nom de `MinimumOSPlatformAttribute` est susceptible de générer des erreurs, car l’attribut est appliqué aux assemblys spécifiques à la plateforme au moment de la génération, et les anciens artefacts de build feront toujours référence à l’ancien nom de l’API.</span><span class="sxs-lookup"><span data-stu-id="74ad3-121">For example, the renaming of `MinimumOSPlatformAttribute` is likely to produce errors, because the attribute is applied to platform-specific assemblies at build time, and old build artifacts will still reference the old API name.</span></span>

<span data-ttu-id="74ad3-122">Exemples d’erreurs de génération :</span><span class="sxs-lookup"><span data-stu-id="74ad3-122">Example build-time errors:</span></span>

- <span data-ttu-id="74ad3-123">**erreur CS0246 : le nom du type ou de l’espace de noms’MinimumOSPlatformAttribute’est introuvable (une directive using ou une référence d’assembly est-elle manquante ?)**</span><span class="sxs-lookup"><span data-stu-id="74ad3-123">**error CS0246: The type or namespace name 'MinimumOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="74ad3-124">**erreur CS0246 : le nom du type ou de l’espace de noms’RemovedInOSPlatformAttribute’est introuvable (une directive using ou une référence d’assembly est-elle manquante ?)**</span><span class="sxs-lookup"><span data-stu-id="74ad3-124">**error CS0246: The type or namespace name 'RemovedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="74ad3-125">**erreur CS0246 : le nom du type ou de l’espace de noms’ObsoletedInOSPlatformAttribute’est introuvable (une directive using ou une référence d’assembly est-elle manquante ?)**</span><span class="sxs-lookup"><span data-stu-id="74ad3-125">**error CS0246: The type or namespace name 'ObsoletedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="74ad3-126">Exemple d’erreur au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="74ad3-126">Example run-time error:</span></span>

<span data-ttu-id="74ad3-127">**Exception non gérée. System. TypeLoadException : impossible de charger le type’System. Runtime. Versioning. MinimumOSPlatformAttribute’à partir de l’assembly’System. Runtime, version = 5.0.0.0, culture = neutral, PublicKeyToken = b03f5f7f11d50a3a'.**</span><span class="sxs-lookup"><span data-stu-id="74ad3-127">**Unhandled exception. System.TypeLoadException: Could not load type 'System.Runtime.Versioning.MinimumOSPlatformAttribute' from assembly 'System.Runtime, Version=5.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'.**</span></span>

<span data-ttu-id="74ad3-128">Pour résoudre ces erreurs :</span><span class="sxs-lookup"><span data-stu-id="74ad3-128">To resolve these errors:</span></span>

- <span data-ttu-id="74ad3-129">Met à jour toutes les références de `MinimumOSPlatformAttribute` à <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> .</span><span class="sxs-lookup"><span data-stu-id="74ad3-129">Update any references of `MinimumOSPlatformAttribute` to <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="74ad3-130">Met à jour toutes les références de `RemovedInOSPlatformAttribute` à <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> .</span><span class="sxs-lookup"><span data-stu-id="74ad3-130">Update any references of `RemovedInOSPlatformAttribute` to <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="74ad3-131">Supprimez toutes les références à `ObsoletedInOSPlatformAttribute` .</span><span class="sxs-lookup"><span data-stu-id="74ad3-131">Remove any references to `ObsoletedInOSPlatformAttribute`.</span></span>
- <span data-ttu-id="74ad3-132">Régénérez votre projet (ou effectuez une génération + Build) pour supprimer les anciens artefacts de Build.</span><span class="sxs-lookup"><span data-stu-id="74ad3-132">Rebuild your project (or perform clean + build) to delete old build artifacts.</span></span>

#### <a name="category"></a><span data-ttu-id="74ad3-133">Category</span><span class="sxs-lookup"><span data-stu-id="74ad3-133">Category</span></span>

<span data-ttu-id="74ad3-134">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="74ad3-134">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="74ad3-135">API affectées</span><span class="sxs-lookup"><span data-stu-id="74ad3-135">Affected APIs</span></span>

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

#### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
