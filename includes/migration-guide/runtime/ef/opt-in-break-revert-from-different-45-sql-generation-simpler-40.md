---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803260"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="35661-101">Rupture d’adhésion pour rétrograder de la génération 4.5 de SQL à la génération 4.0 de SQL plus simple</span><span class="sxs-lookup"><span data-stu-id="35661-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="35661-102">Détails</span><span class="sxs-lookup"><span data-stu-id="35661-102">Details</span></span>|<span data-ttu-id="35661-103">Les requêtes, qui produisent des instructions JOIN et contiennent un appel à une opération de limitation sans préalablement utiliser OrderBy, produisent à présent un langage SQL plus simple.</span><span class="sxs-lookup"><span data-stu-id="35661-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="35661-104">Après la mise à niveau vers .NET Framework 4.5, ces requêtes produisaient un langage SQL plus compliqué que les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="35661-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>|
|<span data-ttu-id="35661-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="35661-105">Suggestion</span></span>|<span data-ttu-id="35661-106">Cette fonctionnalité est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="35661-106">This feature is disabled by default.</span></span> <span data-ttu-id="35661-107">Si Entity Framework génère des instructions JOIN supplémentaires qui entraînent une dégradation des performances, vous pouvez activer cette fonctionnalité en ajoutant l’entrée suivante à la section <code>&lt;appSettings&gt;</code> du fichier de configuration de l’application (app.config) :</span><span class="sxs-lookup"><span data-stu-id="35661-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="35661-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="35661-108">Scope</span></span>|<span data-ttu-id="35661-109">Transparent</span><span class="sxs-lookup"><span data-stu-id="35661-109">Transparent</span></span>|
|<span data-ttu-id="35661-110">Version</span><span class="sxs-lookup"><span data-stu-id="35661-110">Version</span></span>|<span data-ttu-id="35661-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="35661-111">4.5.2</span></span>|
|<span data-ttu-id="35661-112">Type</span><span class="sxs-lookup"><span data-stu-id="35661-112">Type</span></span>|<span data-ttu-id="35661-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="35661-113">Runtime</span></span>|
