---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: 375fe9ce52ae290c175e42276b6b526766f6699c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547510"
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)
Retourne une collection d'objets à partir d'une expression de requête d'un type spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression de requête valide qui retourne une collection d'objets.  
  
 `test_type`  
 Type en fonction duquel tester chaque objet retourné par `expression` . Le type doit être qualifié par un espace de noms.  
  
## <a name="return-value"></a>Valeur de retour  
 Collection d'objets du type `test_type`ou d'un type de base ou dérivé de `test_type`. Si ONLY est spécifié, seules les instances de `test_type` ou une collection vide seront retournées.  
  
## <a name="remarks"></a>Notes  
 Une expression `OFTYPE` spécifie une expression de type émise pour effectuer un test de type sur chaque élément d'une collection.  L'expression `OFTYPE` produit une nouvelle collection du type spécifié ne contenant que les éléments qui étaient équivalents à ce type ou à l'un de ses sous-types.  
  
 Une expression `OFTYPE` est l'abréviation de l'expression de requête suivante :  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Un Manager étant un sous-type d'Employee, l'expression suivante produit à partir d'une collection d'employés (employee) une collection composée uniquement de responsables (manager) :  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 Il est également possible d'effectuer un upcast sur une collection à l'aide du filtre de type :  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 Puisque tous les cadres (executives) sont des responsables, la collection obtenue contient toujours tous les cadres d'origine, même si elle est désormais typée en tant que collection de responsables.  
  
 Le tableau suivant montre le comportement de l'opérateur `OFTYPE` sur certains modèles. Toutes les exceptions sont levées du côté client avant que le fournisseur ne soit appelé :  
  
|Modèle|Comportement|  
|-------------|--------------|  
|OFTYPE(Collection(EntityType), EntityType)|Collection(EntityType)|  
|OFTYPE(Collection(ComplexType), ComplexType)|Exception|  
|OFTYPE(Collection(RowType), RowType)|Exception|  
  
## <a name="example"></a> Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivante utilise l'opérateur OFTYPE pour retourner une collection d'objets OnsiteCourse à partir d'une collection d'objets Course. Cette requête est basée sur le modèle [School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
