---
title: + (Ajouter)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: b86d273658362c3bb204d5220ff5e9db1f8de9fe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198052"
---
# <a name="-add"></a>+ (Ajouter)

Additionne deux nombres.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a>Arguments  

 `expression`  
 Toute expression valide de l'un des types de données numériques.  
  
## <a name="result-types"></a>Types des résultats  

 Type de données qui résulte de la promotion de type implicite de deux arguments. Pour plus d’informations sur la promotion de type implicite, consultez [système de type](type-system-entity-sql.md).  
  
## <a name="remarks"></a>Notes  

 Pour les types EDM.String, l'addition est une concaténation.  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous utilise l'opérateur arithmétique + pour additionner deux nombres. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Types de modèles conceptuels (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
