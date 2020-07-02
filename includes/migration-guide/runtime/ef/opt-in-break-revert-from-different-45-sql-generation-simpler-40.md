---
ms.openlocfilehash: 22b5abbe769733e8d5ca3e78dd9e6e13b2363737
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620016"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="62160-101">Rupture d’adhésion pour rétrograder de la génération 4.5 de SQL à la génération 4.0 de SQL plus simple</span><span class="sxs-lookup"><span data-stu-id="62160-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

#### <a name="details"></a><span data-ttu-id="62160-102">Détails</span><span class="sxs-lookup"><span data-stu-id="62160-102">Details</span></span>

<span data-ttu-id="62160-103">Les requêtes, qui produisent des instructions JOIN et contiennent un appel à une opération de limitation sans préalablement utiliser OrderBy, produisent à présent un langage SQL plus simple.</span><span class="sxs-lookup"><span data-stu-id="62160-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="62160-104">Après la mise à niveau vers .NET Framework 4.5, ces requêtes produisaient un langage SQL plus compliqué que les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="62160-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="62160-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="62160-105">Suggestion</span></span>

<span data-ttu-id="62160-106">Cette fonctionnalité est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="62160-106">This feature is disabled by default.</span></span> <span data-ttu-id="62160-107">Si Entity Framework génère des instructions JOIN supplémentaires qui entraînent une dégradation des performances, vous pouvez activer cette fonctionnalité en ajoutant l’entrée suivante à la section <code>&lt;appSettings&gt;</code> du fichier de configuration de l’application (app.config) :</span><span class="sxs-lookup"><span data-stu-id="62160-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="62160-108">Nom</span><span class="sxs-lookup"><span data-stu-id="62160-108">Name</span></span>    | <span data-ttu-id="62160-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="62160-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="62160-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="62160-110">Scope</span></span>   |<span data-ttu-id="62160-111">Mode transparent</span><span class="sxs-lookup"><span data-stu-id="62160-111">Transparent</span></span>|
|<span data-ttu-id="62160-112">Version</span><span class="sxs-lookup"><span data-stu-id="62160-112">Version</span></span>|<span data-ttu-id="62160-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="62160-113">4.5.2</span></span>|
|<span data-ttu-id="62160-114">Type</span><span class="sxs-lookup"><span data-stu-id="62160-114">Type</span></span>|<span data-ttu-id="62160-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="62160-115">Runtime</span></span>|
