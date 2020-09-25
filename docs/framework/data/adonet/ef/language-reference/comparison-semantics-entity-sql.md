---
title: Sémantique de comparaison (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 9a36fcc4476c25d64fed670e857f339fb20043d8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197831"
---
# <a name="comparison-semantics-entity-sql"></a>Sémantique de comparaison (Entity SQL)

L'exécution des opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivants implique une comparaison d'instances de type :  
  
## <a name="explicit-comparison"></a>Comparaison explicite  

 Opérations d'égalité :  
  
- =  
  
- !=  
  
 Opérations de classement :  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 Opérations relatives à la possibilité de valeurs NULL :  
  
- IS NULL  
  
- IS NOT NULL  
  
## <a name="explicit-distinction"></a>Distinction explicite  

 Distinction d'égalité :  
  
- DISTINCT  
  
- GROUP BY  
  
 Distinction de classement :  
  
- ORDER BY  
  
## <a name="implicit-distinction"></a>Distinction implicite  

 Opérations et prédicats de définition (égalité) :  
  
- UNION  
  
- INTERSECT  
  
- EXCEPT  
  
- SET  
  
- OVERLAPS  
  
 Prédicats d'élément (égalité) :  
  
- IN  
  
## <a name="supported-combinations"></a>Combinaisons prises en charge  

 Le tableau suivant répertorie toutes les combinaisons prises en charge des opérateurs de comparaison pour chaque type :  
  
|**Type**|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **DISTINCT**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDER BY**|**IS NULL**<br /><br /> **N’EST PAS NULL**|  
|-|-|-|-|-|-|-|-|  
|Type d'entité|Réf.<sup>1</sup>|Toutes les propriétés<sup>2</sup>|Toutes les propriétés<sup>2</sup>|Toutes les propriétés<sup>2</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|Réf.<sup>1</sup>|  
|Type complexe|Lever<sup>3</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|  
|Ligne|Toutes les propriétés<sup>4</sup>|Toutes les propriétés<sup>4</sup>|Toutes les propriétés<sup>4</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|Toutes les propriétés<sup>4</sup>|Lever<sup>3</sup>|  
|Type primitif|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|  
|Multiset|Lever<sup>3</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|  
|Ref|Oui<sup>5</sup>|Oui<sup>5</sup>|Oui<sup>5</sup>|Oui<sup>5</sup>|Throw|Throw|Oui<sup>5</sup>|  
|Association<br /><br /> type|Lever<sup>3</sup>|Throw|Throw|Throw|Lever<sup>3</sup>|Lever<sup>3</sup>|Lever<sup>3</sup>|  
  
 <sup>1</sup> Les références des instances de type d’entité données sont comparées implicitement, comme illustré dans l’exemple suivant :  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Une instance d'entité ne peut pas être comparée à une référence explicite. Lors d'une telle tentative, une exception est levée. Par exemple, la requête suivante lève une exception :  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup> Les propriétés des types complexes sont aplaties avant d’être envoyées au magasin. elles deviennent donc comparables (à condition que toutes leurs propriétés soient comparables). Consultez également <sup>4.</sup>  
  
 <sup>3</sup> Le runtime Entity Framework détecte le cas non pris en charge et lève une exception significative sans engager le fournisseur/magasin.  
  
 <sup>4</sup> Une tentative est effectuée pour comparer toutes les propriétés. Si une propriété est d'un type non comparable, tel que text, ntext ou image, une exception de serveur peut être levée.  
  
 <sup>5</sup> Tous les éléments individuels des références sont comparés (cela comprend le nom du jeu d’entités et toutes les propriétés de clé du type d’entité).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
