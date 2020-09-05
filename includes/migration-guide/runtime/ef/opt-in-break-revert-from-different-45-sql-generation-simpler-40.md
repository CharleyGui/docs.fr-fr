---
ms.openlocfilehash: 346fb6ecd43f7f93529e45f169c79b7acacc9c1f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497360"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="7f620-101">Rupture d’adhésion pour rétrograder de la génération 4.5 de SQL à la génération 4.0 de SQL plus simple</span><span class="sxs-lookup"><span data-stu-id="7f620-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

#### <a name="details"></a><span data-ttu-id="7f620-102">Détails</span><span class="sxs-lookup"><span data-stu-id="7f620-102">Details</span></span>

<span data-ttu-id="7f620-103">Les requêtes, qui produisent des instructions JOIN et contiennent un appel à une opération de limitation sans préalablement utiliser OrderBy, produisent à présent un langage SQL plus simple.</span><span class="sxs-lookup"><span data-stu-id="7f620-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="7f620-104">Après la mise à niveau vers .NET Framework 4.5, ces requêtes produisaient un langage SQL plus compliqué que les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="7f620-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7f620-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="7f620-105">Suggestion</span></span>

<span data-ttu-id="7f620-106">Cette fonctionnalité est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="7f620-106">This feature is disabled by default.</span></span> <span data-ttu-id="7f620-107">Si Entity Framework génère des instructions JOIN supplémentaires qui entraînent une dégradation des performances, vous pouvez activer cette fonctionnalité en ajoutant l’entrée suivante à la section <code>&lt;appSettings&gt;</code> du fichier de configuration de l’application (app.config) :</span><span class="sxs-lookup"><span data-stu-id="7f620-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="7f620-108">Name</span><span class="sxs-lookup"><span data-stu-id="7f620-108">Name</span></span>    | <span data-ttu-id="7f620-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="7f620-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7f620-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="7f620-110">Scope</span></span>   |<span data-ttu-id="7f620-111">Mode transparent</span><span class="sxs-lookup"><span data-stu-id="7f620-111">Transparent</span></span>|
|<span data-ttu-id="7f620-112">Version</span><span class="sxs-lookup"><span data-stu-id="7f620-112">Version</span></span>|<span data-ttu-id="7f620-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="7f620-113">4.5.2</span></span>|
|<span data-ttu-id="7f620-114">Type</span><span class="sxs-lookup"><span data-stu-id="7f620-114">Type</span></span>|<span data-ttu-id="7f620-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="7f620-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7f620-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="7f620-116">Affected APIs</span></span>

<span data-ttu-id="7f620-117">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="7f620-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
