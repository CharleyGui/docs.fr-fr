---
ms.openlocfilehash: 1329a86db4227f75dfba7c50bbbdc2fc23099528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619998"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>SqlBulkCopy utilise l’encodage de la colonne de destination pour les chaînes

#### <a name="details"></a>Détails

Lors de l'insertion de données dans une colonne, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> utilise l'encodage de la colonne de destination plutôt que l'encodage par défaut pour les types <code>VARCHAR</code> et <code>CHAR</code>. Cette modification élimine la possibilité d'altération de données provoquée par l'utilisation de l'encodage par défaut lorsque la colonne de destination n'utilise pas l'encodage par défaut. Dans de rares cas, une application existante peut lever une exception SqlException si la modification de l’encodage produit des données qui sont trop volumineuses pour s’insérer dans la colonne de destination.

#### <a name="suggestion"></a>Suggestion

Attendez-vous à ce que <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> n’endommage plus les données en raison des différences d’encodage. Si des chaînes près de la limite de taille de la colonne de destination sont copiées, il peut être nécessaire d’encoder au préalable les données (à copier pour vérifier que les données contiennent dans la colonne de destination) ou d’intercepter les <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)></li></ul>|
