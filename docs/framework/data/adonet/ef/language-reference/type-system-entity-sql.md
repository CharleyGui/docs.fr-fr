---
title: System, type (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: b8b721aff5b7886fdb897ecaa3dcc163ec94ae79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149829"
---
# <a name="type-system-entity-sql"></a>System, type (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]prend en charge un certain nombre de types :  
  
- Les types primitifs (simples), tels que `Int32` et `String.`  
  
- Les types nominaux qui sont définis dans le schéma, tels que <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType> et <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
- Les types anonymes qui ne sont pas définis explicitement dans le schéma : <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType> et <xref:System.Data.Metadata.Edm.RefType>.  
  
 Cette section traite des types anonymes qui ne sont pas définis explicitement dans le schéma, mais qui sont appuyés par l’entité SQL. Pour plus d’informations sur les types primitifs et nominaux, voir [Les types de modèles conceptuels (CSDL).](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)  
  
## <a name="rows"></a>Lignes  
 La structure d'une ligne dépend de la séquence de membres typés et nommés que la ligne contient. Un type de ligne n'a aucune identité et ne peut pas faire l'objet d'un héritage. Les instances du même type de ligne sont équivalentes si les membres sont respectivement équivalents. Les lignes n'ont aucun comportement au-delà de leur équivalence structurelle et n'ont aucun équivalent dans le Common Language Runtime. Les requêtes peuvent donner des structures qui contiennent des lignes ou des collections de lignes. La liaison d’API entre les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] et le langage hôte définit la façon dont les lignes sont réalisées dans la requête qui a produit le résultat. Pour plus d’informations sur la façon de construire une ligne d’instance, voir [Construire des types](constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Collections  
 Les types de collections représentent zéro instance ou plus d’autres objets. Pour plus d’informations sur la façon de construire la collecte, voir [Construire des types](constructing-types-entity-sql.md).  
  
## <a name="references"></a>References  
 Une référence est un pointeur logique vers une entité spécifique dans un jeu d'entités spécifique.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge les opérateurs suivants pour construire, déconstruire et explorer les références :  
  
- [Ref](ref-entity-sql.md)  
  
- [CREATEREF](createref-entity-sql.md)  
  
- [Clé](key-entity-sql.md)  
  
- [DEREF](deref-entity-sql.md)  
  
 Vous pouvez explorer une référence en utilisant l'opérateur `.` (point) d'accès au membre. L'extrait de code suivant extrait la propriété ID (de Order) en explorant la propriété r (référence).  
  
```sql  
select o2.r.Id
from (select ref(o) as r from LOB.Orders as o) as o2
```  
  
 Si la valeur de la référence est Null, si la cible de la référence n'existe pas, le résultat est null.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
- [Référence Entity SQL](entity-sql-reference.md)
- [CAST](cast-entity-sql.md)
- [Spécifications CSDL, SSDL et MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
