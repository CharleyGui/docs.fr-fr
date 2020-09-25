---
title: -- (Commentaire) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 9ad6e38726d0802c3bc2090a4e6f11f008828ee5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197896"
---
# <a name="---comment-entity-sql"></a>-- (Commentaire) (Entity SQL)

Les requêtes[!INCLUDE[esql](../../../../../../includes/esql-md.md)] peuvent contenir des commentaires. Deux tirets (`--`) marquent le début d'une ligne de commentaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Arguments  

 `text_of_comment`  
 Chaîne de caractères contenant le texte du commentaire.  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous montre comment utiliser les commentaires. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
- [Référence Entity SQL](entity-sql-reference.md)
