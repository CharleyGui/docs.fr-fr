---
ms.openlocfilehash: fb339fb35cdcbba4f1c860fae9c17162c4cff596
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497665"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="57208-101">Les données Sql_variant utilisent le classement sql_variant plutôt que le classement de la base de données</span><span class="sxs-lookup"><span data-stu-id="57208-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="57208-102">Détails</span><span class="sxs-lookup"><span data-stu-id="57208-102">Details</span></span>

<span data-ttu-id="57208-103">Les données <code>sql_variant</code> utilisent le classement <code>sql_variant</code> plutôt que le classement de la base de données.</span><span class="sxs-lookup"><span data-stu-id="57208-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="57208-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="57208-104">Suggestion</span></span>

<span data-ttu-id="57208-105">Cette modification permet de répondre à une éventuelle altération de données si le classement de la base de données est différent du classement <code>sql_variant</code>.</span><span class="sxs-lookup"><span data-stu-id="57208-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="57208-106">Les applications qui s'appuient sur les données endommagées peuvent éventuellement échouer.</span><span class="sxs-lookup"><span data-stu-id="57208-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="57208-107">Name</span><span class="sxs-lookup"><span data-stu-id="57208-107">Name</span></span>    | <span data-ttu-id="57208-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="57208-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="57208-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="57208-109">Scope</span></span>   |<span data-ttu-id="57208-110">Mode transparent</span><span class="sxs-lookup"><span data-stu-id="57208-110">Transparent</span></span>|
|<span data-ttu-id="57208-111">Version</span><span class="sxs-lookup"><span data-stu-id="57208-111">Version</span></span>|<span data-ttu-id="57208-112">4,5</span><span class="sxs-lookup"><span data-stu-id="57208-112">4.5</span></span>|
|<span data-ttu-id="57208-113">Type</span><span class="sxs-lookup"><span data-stu-id="57208-113">Type</span></span>|<span data-ttu-id="57208-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="57208-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="57208-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="57208-115">Affected APIs</span></span>

<span data-ttu-id="57208-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="57208-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
