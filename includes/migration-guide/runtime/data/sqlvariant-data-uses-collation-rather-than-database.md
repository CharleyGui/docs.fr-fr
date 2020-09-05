---
ms.openlocfilehash: fb339fb35cdcbba4f1c860fae9c17162c4cff596
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497665"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a>Les données Sql_variant utilisent le classement sql_variant plutôt que le classement de la base de données

#### <a name="details"></a>Détails

Les données <code>sql_variant</code> utilisent le classement <code>sql_variant</code> plutôt que le classement de la base de données.

#### <a name="suggestion"></a>Suggestion

Cette modification permet de répondre à une éventuelle altération de données si le classement de la base de données est différent du classement <code>sql_variant</code>. Les applications qui s'appuient sur les données endommagées peuvent éventuellement échouer.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Mode transparent|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
