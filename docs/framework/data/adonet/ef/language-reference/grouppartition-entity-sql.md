---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 11abebeac682fed9e3a007986bb2f5c7bdb80f16
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204474"
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (Entity SQL)

Retourne une collection de valeurs d'argument projetées en dehors de la partition de groupe actuelle à laquelle l'agrégat est associé. L'agrégat `GroupPartition` est un agrégat basé sur les groupes et n'a aucune forme basée sur les collections.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Arguments  

 `expression`  
 Toute expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="remarks"></a>Notes  

 La requête suivante produit une liste de produits et une collection de quantités de ligne de commande pour chaque produit :  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 Les deux requêtes suivantes sont sémantiquement égales :  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 L'opérateur `GROUPPARTITION` peut être utilisé conjointement à des fonctions d'agrégation définies par l'utilisateur.  
  
`GROUPPARTITION` est un opérateur d'agrégation spécial qui maintient une référence au jeu de données d'entrée groupé. Cette référence peut être utilisée n'importe où dans la requête où GROUP BY est dans la portée. Par exemple :
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 Avec un régulier `GROUP BY` , les résultats du regroupement sont masqués. Vous pouvez utiliser les résultats uniquement dans une fonction d'agrégation. Pour voir les résultats du regroupement, vous devez mettre en corrélation les résultats du regroupement et le jeu de données d'entrée à l'aide d'une sous-requête. Les deux requêtes suivantes sont équivalentes :  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 Comme le montre l'exemple, l'opérateur d'agrégation GROUPPARTITION simplifie l'obtention d'une référence au jeu de données d'entrée après le regroupement.  
  
 L'opérateur GROUPPARTITION peut spécifier toute expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dans l'entrée de l'opérateur lorsque vous utilisez le paramètre `expression` .  
  
 Par exemple, toutes les expressions d'entrée suivantes de la partition de groupe sont valides :  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a>Exemple  

 L'exemple ci-dessous montre comment utiliser la clause GROUPPARTITION avec la clause GROUP BY. La clause GROUP BY regroupe les entités `SalesOrderHeader` par leur élément `Contact`. La clause GROUPPARTITION projette alors la propriété `TotalDue` pour chaque groupe, ce qui génère une collection de valeurs décimales.  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
