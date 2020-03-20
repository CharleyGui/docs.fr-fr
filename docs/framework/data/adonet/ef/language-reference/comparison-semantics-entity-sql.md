---
title: Sémantique de comparaison (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150452"
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
  
|**Type**|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **Distinctes**|**Union**<br /><br /> **Intersect**<br /><br /> **Sauf**<br /><br /> **Ensemble**<br /><br /> **Chevauchements**|**Dans**|**< <**<br /><br /> **> >**|**COMMANDE PAR**|**EST NUL**<br /><br /> **N’EST PAS NUL**|  
|-|-|-|-|-|-|-|-|  
|Type d'entité|Réf<sup>1</sup>|Toutes les propriétés<sup>2</sup>|Toutes les propriétés<sup>2</sup>|Toutes les propriétés<sup>2</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Réf<sup>1</sup>|  
|Type complexe|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|  
|Ligne|Toutes les propriétés<sup>4</sup>|Toutes les propriétés<sup>4</sup>|Toutes les propriétés<sup>4</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Toutes les propriétés<sup>4</sup>|Lancer<sup>3</sup>|  
|Type primitif|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|  
|Multiset|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|  
|Ref|Oui<sup>5</sup>|Oui<sup>5</sup>|Oui<sup>5</sup>|Oui<sup>5</sup>|Throw|Throw|Oui<sup>5</sup>|  
|Association<br /><br /> type|Lancer<sup>3</sup>|Throw|Throw|Throw|Lancer<sup>3</sup>|Lancer<sup>3</sup>|Lancer<sup>3</sup>|  
  
 <sup>1</sup> Les références des instances de type entité donnée sont implicitement comparées, comme le montre l’exemple suivant :  
  
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
  
 <sup>2</sup> Les propriétés de types complexes sont aplaties avant d’être envoyées au magasin, de sorte qu’elles deviennent comparables (tant que toutes leurs propriétés sont comparables). Voir aussi <sup>4.</sup>  
  
 <sup>3</sup> Le temps d’exécution du Cadre d’entité détecte le boîtier non pris en charge et fait une exception significative sans engager le fournisseur/magasin.  
  
 <sup>4</sup> Une tentative est faite pour comparer toutes les propriétés. Si une propriété est d'un type non comparable, tel que text, ntext ou image, une exception de serveur peut être levée.  
  
 <sup>5</sup> Tous les éléments individuels des références sont comparés (cela inclut le nom d’entité et toutes les propriétés clés du type d’entité).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
