---
title: Constructeur de type nommé (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: c673b58ee5811e3d3b74b3744d3f5291888e2253
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197779"
---
# <a name="named-type-constructor-entity-sql"></a>Constructeur de type nommé (Entity SQL)

Permet de créer des instances des types nominaux de modèle conceptuel, tels que les types d'entités ou complexes.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>Arguments  

 `identifier`  
 Valeur correspondant à un identificateur simple ou entre guillemets. Pour plus d’informations, consultez [identificateurs](identifiers-entity-sql.md)  
  
 `expression`  
 Attributs du type supposés se trouver dans le même ordre d'apparition que dans la déclaration du type.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Instances de types complexes et de types d'entités nommés.  
  
## <a name="remarks"></a>Notes  

 Les exemples suivants montrent comment construire des types nominaux et des types complexes :  
  
 L'expression ci-dessous crée une instance de type `Person` :  
  
 `Person("abc", 12)`  
  
 L'expression ci-dessous crée une instance d'un type complexe :  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 L'expression ci-dessous crée une instance d'un type complexe imbriqué :  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 L'expression ci-dessous crée une instance d'une entité avec un type complexe imbriqué :  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 L'exemple suivant montre comment initialiser une propriété d'un type complexe en valeur null :`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous utilise le constructeur de type nommé pour créer une instance d'un type de modèle conceptuel. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#NAMED_TYPE_CONSTRUCTOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#named_type_constructor)]  
  
## <a name="see-also"></a>Voir aussi

- [Construction de types](constructing-types-entity-sql.md)
- [Référence Entity SQL](entity-sql-reference.md)
