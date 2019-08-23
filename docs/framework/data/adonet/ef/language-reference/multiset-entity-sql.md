---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: eb676feeb168e1fb184f3869a18e138bff34211b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929341"
---
# <a name="multiset-entity-sql"></a>MULTISET (Entity SQL)
Crée une instance d'un multiensemble à partir d'une liste de valeurs. Toutes les valeurs du constructeur MULTISET doivent être d'un type `T`compatible. Les constructeurs de multiensemble vides ne sont pas autorisés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute liste de valeurs valide.  
  
## <a name="return-value"></a>Valeur de retour  
 Collection de type\<multiensemble T >.  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] propose trois types de constructeurs : constructeurs de ligne, constructeurs d'objets et constructeurs de multiensemble (ou de collection). Pour plus d’informations, consultez [construction de types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
 Le constructeur de multiensemble crée une instance d'un multiensemble à partir d'une liste de valeurs. Toutes les valeurs du constructeur doivent être d'un type compatible.  
  
 Par exemple, l'expression suivante crée un multiensemble d'entiers.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> Les littéraux de multiensemble imbriqués sont pris en charge uniquement lorsqu’un multiensemble d’encapsulation a un seul élément de multiensemble; par exemple, `{{1, 2, 3}}`. Lorsqu'un multiensemble d'encapsulation a plusieurs éléments de multiensemble (par exemple, `{{1, 2}, {3, 4}}`), ils ne sont pas pris en charge.  
  
## <a name="example"></a>Exemples  
 La requête Entity SQL suivante utilise l'opérateur MULTISET pour créer une instance d'un multiensemble à partir d'une liste de valeurs. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite [dans la rubrique Procédure: Exécutez une requête qui retourne les résultats](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>Voir aussi

- [Construction de types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
