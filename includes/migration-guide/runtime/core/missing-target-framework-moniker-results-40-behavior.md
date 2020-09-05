---
ms.openlocfilehash: 49740d3b1890d72935e6e329a4f4be836ed70b25
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496541"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a><span data-ttu-id="d02d0-101">Un moniker de framework cible manquant a pour effet de restaurer le comportement de la version 4.0</span><span class="sxs-lookup"><span data-stu-id="d02d0-101">Missing Target Framework Moniker results in 4.0 behavior</span></span>

#### <a name="details"></a><span data-ttu-id="d02d0-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d02d0-102">Details</span></span>

<span data-ttu-id="d02d0-103">Les applications dans lesquelles un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> n’est pas appliqué au niveau de l’assembly sont automatiquement exécutées à l’aide de la sémantique (Quirks) de .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="d02d0-103">Applications without a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> applied at the assembly level will automatically run using the semantics (quirks) of the .NET Framework 4.0.</span></span> <span data-ttu-id="d02d0-104">Pour garantir une haute qualité, il est recommandé d’attribuer explicitement à tous les fichiers binaires un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indiquant la version du .NET Framework avec laquelle ils ont été créés.</span><span class="sxs-lookup"><span data-stu-id="d02d0-104">To ensure high quality, it is recommended that all binaries be explicitly attributed with a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicating the version of the .NET Framework they were built with.</span></span> <span data-ttu-id="d02d0-105">Si vous utilisez un moniker de framework cible dans un fichier projet, MSBuild applique automatiquement un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d02d0-105">Note that using a target framework moniker in a project file will cause MSBuild to automatically apply a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d02d0-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d02d0-106">Suggestion</span></span>

<span data-ttu-id="d02d0-107">Un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> doit être fourni, soit en ajoutant directement l’attribut à l’assembly, soit en spécifiant une version cible de .Net Framework dans le [fichier projet ou par le biais de l’interface graphique utilisateur des propriétés du projet de Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span><span class="sxs-lookup"><span data-stu-id="d02d0-107">A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> should be supplied, either through adding the attribute directly to the assembly or by specifying a target framework in the [project file or through Visual Studio's project properties GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span></span>

| <span data-ttu-id="d02d0-108">Name</span><span class="sxs-lookup"><span data-stu-id="d02d0-108">Name</span></span>    | <span data-ttu-id="d02d0-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="d02d0-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d02d0-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="d02d0-110">Scope</span></span>   |<span data-ttu-id="d02d0-111">Majeure</span><span class="sxs-lookup"><span data-stu-id="d02d0-111">Major</span></span>|
|<span data-ttu-id="d02d0-112">Version</span><span class="sxs-lookup"><span data-stu-id="d02d0-112">Version</span></span>|<span data-ttu-id="d02d0-113">4,5</span><span class="sxs-lookup"><span data-stu-id="d02d0-113">4.5</span></span>|
|<span data-ttu-id="d02d0-114">Type</span><span class="sxs-lookup"><span data-stu-id="d02d0-114">Type</span></span>|<span data-ttu-id="d02d0-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="d02d0-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="d02d0-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="d02d0-116">Affected APIs</span></span>

<span data-ttu-id="d02d0-117">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="d02d0-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
