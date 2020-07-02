---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619985"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a><span data-ttu-id="b23b1-101">Un moniker de framework cible manquant a pour effet de restaurer le comportement de la version 4.0</span><span class="sxs-lookup"><span data-stu-id="b23b1-101">Missing Target Framework Moniker results in 4.0 behavior</span></span>

#### <a name="details"></a><span data-ttu-id="b23b1-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b23b1-102">Details</span></span>

<span data-ttu-id="b23b1-103">Les applications dans lesquelles un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> n’est pas appliqué au niveau de l’assembly sont automatiquement exécutées à l’aide de la sémantique (Quirks) de .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="b23b1-103">Applications without a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> applied at the assembly level will automatically run using the semantics (quirks) of the .NET Framework 4.0.</span></span> <span data-ttu-id="b23b1-104">Pour garantir une haute qualité, il est recommandé d’attribuer explicitement à tous les fichiers binaires un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indiquant la version du .NET Framework avec laquelle ils ont été créés.</span><span class="sxs-lookup"><span data-stu-id="b23b1-104">To ensure high quality, it is recommended that all binaries be explicitly attributed with a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicating the version of the .NET Framework they were built with.</span></span> <span data-ttu-id="b23b1-105">Si vous utilisez un moniker de framework cible dans un fichier projet, MSBuild applique automatiquement un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="b23b1-105">Note that using a target framework moniker in a project file will cause MSBuild to automatically apply a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b23b1-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b23b1-106">Suggestion</span></span>

<span data-ttu-id="b23b1-107">Un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> doit être fourni, soit en ajoutant directement l’attribut à l’assembly, soit en spécifiant une version cible de .Net Framework dans le [fichier projet ou par le biais de l’interface graphique utilisateur des propriétés du projet de Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span><span class="sxs-lookup"><span data-stu-id="b23b1-107">A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> should be supplied, either through adding the attribute directly to the assembly or by specifying a target framework in the [project file or through Visual Studio's project properties GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span></span>

| <span data-ttu-id="b23b1-108">Nom</span><span class="sxs-lookup"><span data-stu-id="b23b1-108">Name</span></span>    | <span data-ttu-id="b23b1-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="b23b1-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b23b1-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="b23b1-110">Scope</span></span>   |<span data-ttu-id="b23b1-111">Majeure</span><span class="sxs-lookup"><span data-stu-id="b23b1-111">Major</span></span>|
|<span data-ttu-id="b23b1-112">Version</span><span class="sxs-lookup"><span data-stu-id="b23b1-112">Version</span></span>|<span data-ttu-id="b23b1-113">4,5</span><span class="sxs-lookup"><span data-stu-id="b23b1-113">4.5</span></span>|
|<span data-ttu-id="b23b1-114">Type</span><span class="sxs-lookup"><span data-stu-id="b23b1-114">Type</span></span>|<span data-ttu-id="b23b1-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="b23b1-115">Runtime</span></span>|
