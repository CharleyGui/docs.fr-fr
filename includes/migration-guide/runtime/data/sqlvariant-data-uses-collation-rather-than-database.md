---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620004"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a>Les données Sql_variant utilisent le classement sql_variant plutôt que le classement de la base de données

#### <a name="details"></a>Détails

Les données <code>sql_variant</code> utilisent le classement <code>sql_variant</code> plutôt que le classement de la base de données.

#### <a name="suggestion"></a>Suggestion

Cette modification permet de répondre à une éventuelle altération de données si le classement de la base de données est différent du classement <code>sql_variant</code>. Les applications qui s'appuient sur les données endommagées peuvent éventuellement échouer.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Mode transparent|
|Version|4,5|
|Type|Runtime|
