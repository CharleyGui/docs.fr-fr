---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620004"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="c41e2-101">Les données Sql_variant utilisent le classement sql_variant plutôt que le classement de la base de données</span><span class="sxs-lookup"><span data-stu-id="c41e2-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="c41e2-102">Détails</span><span class="sxs-lookup"><span data-stu-id="c41e2-102">Details</span></span>

<span data-ttu-id="c41e2-103">Les données <code>sql_variant</code> utilisent le classement <code>sql_variant</code> plutôt que le classement de la base de données.</span><span class="sxs-lookup"><span data-stu-id="c41e2-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c41e2-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="c41e2-104">Suggestion</span></span>

<span data-ttu-id="c41e2-105">Cette modification permet de répondre à une éventuelle altération de données si le classement de la base de données est différent du classement <code>sql_variant</code>.</span><span class="sxs-lookup"><span data-stu-id="c41e2-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="c41e2-106">Les applications qui s'appuient sur les données endommagées peuvent éventuellement échouer.</span><span class="sxs-lookup"><span data-stu-id="c41e2-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="c41e2-107">Nom</span><span class="sxs-lookup"><span data-stu-id="c41e2-107">Name</span></span>    | <span data-ttu-id="c41e2-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="c41e2-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c41e2-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="c41e2-109">Scope</span></span>   |<span data-ttu-id="c41e2-110">Mode transparent</span><span class="sxs-lookup"><span data-stu-id="c41e2-110">Transparent</span></span>|
|<span data-ttu-id="c41e2-111">Version</span><span class="sxs-lookup"><span data-stu-id="c41e2-111">Version</span></span>|<span data-ttu-id="c41e2-112">4,5</span><span class="sxs-lookup"><span data-stu-id="c41e2-112">4.5</span></span>|
|<span data-ttu-id="c41e2-113">Type</span><span class="sxs-lookup"><span data-stu-id="c41e2-113">Type</span></span>|<span data-ttu-id="c41e2-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="c41e2-114">Runtime</span></span>|
