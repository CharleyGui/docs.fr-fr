---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: a81787da9ee1af084a903dcb50b024f3d26d18fc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175692"
---
# <a name="multiset-entity-sql"></a>MULTISET (Entity SQL)

Crée une instance d'un multiensemble à partir d'une liste de valeurs. Toutes les valeurs du constructeur MULTISET doivent être d'un type `T`compatible. Les constructeurs de multiensemble vides ne sont pas autorisés.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
MULTISET ( expression [{, expression }] )  
-- or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Arguments  

 `expression`  
 Toute liste de valeurs valide.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Collection de multiensemble de type \<T> .  
  
## <a name="remarks"></a>Notes  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] propose trois types de constructeurs : constructeurs de ligne, constructeurs d'objets et constructeurs de multiensemble (ou de collection). Pour plus d’informations, consultez [construction de types](constructing-types-entity-sql.md).  
  
 Le constructeur de multiensemble crée une instance d'un multiensemble à partir d'une liste de valeurs. Toutes les valeurs du constructeur doivent être d'un type compatible.  
  
 Par exemple, l'expression suivante crée un multiensemble d'entiers.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> Les littéraux de multiensemble imbriqués sont pris en charge uniquement lorsqu’un multiensemble d’encapsulation a un seul élément de multiensemble ; par exemple, `{{1, 2, 3}}` . Lorsqu'un multiensemble d'encapsulation a plusieurs éléments de multiensemble (par exemple, `{{1, 2}, {3, 4}}`), ils ne sont pas pris en charge.  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL suivante utilise l'opérateur MULTISET pour créer une instance d'un multiensemble à partir d'une liste de valeurs. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]  
  
## <a name="see-also"></a>Voir aussi

- [Construction de types](constructing-types-entity-sql.md)
- [Référence Entity SQL](entity-sql-reference.md)
