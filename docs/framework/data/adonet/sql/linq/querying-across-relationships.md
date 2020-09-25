---
title: Interrogation de relations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: 24ab13a1d67eac39c7b3d7be8cb1c16ec7265d5e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184878"
---
# <a name="querying-across-relationships"></a>Interrogation de relations

Les références à d’autres objets ou collections d’autres objets dans vos définitions de classe correspondent directement à des relations de clé étrangère dans la base de données. Vous pouvez utiliser ces relations lorsque vous effectuez une interrogation avec la notation par point pour accéder aux propriétés de relation et naviguer entre les objets. Ces opérations d'accès sont traduites en jointures complexes ou en sous-requêtes corrélées plus complexes dans le SQL équivalent.  
  
 Par exemple, la requête suivante navigue des commandes aux clients afin de limiter les résultats aux commandes des clients localisés à Londres.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 Si les propriétés de relation n’existaient pas, vous devez les écrire manuellement en tant que *jointures*, comme vous le feriez dans une requête SQL, comme dans le code suivant :  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 Vous pouvez utiliser la propriété *Relationship* pour définir une relation particulière une seule fois. Vous pouvez ensuite utiliser la syntaxe à point qui est plus pratique. Toutefois, les propriétés de relation sont plus importantes en raison du fait que les modèles objet spécifiques au domaine sont généralement définis comme des hiérarchies ou des graphiques. Les objets par rapport auxquels vous effectuez la programmation ont des références à d'autres objets. C'est une simple coïncidence que les relations entre objets correspondent aux relations de clé étrangère dans les bases de données. L'accès aux propriétés permet ensuite d'écrire facilement des jointures.  
  
 À cet égard, les propriétés de relation sont plus importantes du point de vue des résultats d'une requête que de la requête elle-même. Une fois que la requête a récupéré des données concernant un client spécifique, la définition de classe indique que les clients ont des commandes. En d'autres termes, la propriété `Orders` d'un client spécifique doit être une collection comportant toutes les commandes de ce client. Il s'agit en fait du contrat que vous avez déclaré en définissant les classes de cette manière. Vous vous attendez à voir apparaître les commandes même si la requête ne les a pas demandées. Vous souhaitez que votre modèle objet continue de donner l'impression qu'il s'agit d'une extension en mémoire de la base de données avec les objets connexes immédiatement disponibles.  
  
 Maintenant que vous disposez de relations, vous pouvez écrire des requêtes en faisant référence aux propriétés de relation définies dans vos classes. Ces références de relation correspondent aux relations de clé étrangère dans la base de données. Les opérations qui utilisent ces relations sont traduites en jointures plus complexes dans le SQL équivalent. À partir du moment où vous avez défini une relation (à l'aide de l'attribut <xref:System.Data.Linq.Mapping.AssociationAttribute>), il n'est pas nécessaire de coder une jointure explicite dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Pour aider à maintenir cette illusion, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implémente une technique appelée *chargement différé*. Pour plus d’informations, consultez [différé et chargement immédiat](deferred-versus-immediate-loading.md).  
  
 Considérez la requête SQL suivante pour projeter une liste de `CustomerID` - `OrderID` paires :  
  
```sql
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Pour obtenir les mêmes résultats avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vous utilisez la référence de propriété `Orders` qui existe déjà dans la classe `Customer`. La `Orders` référence fournit les informations nécessaires pour exécuter la requête et projeter les `CustomerID` - `OrderID` paires, comme dans le code suivant :  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Vous pouvez également effectuer l'opération inverse. Vous pouvez en effet interroger `Orders` et utiliser sa référence de relation `Customer` pour accéder aux informations sur l'objet `Customer` associé. Le code suivant projette les mêmes `CustomerID` - `OrderID` paires qu’auparavant, mais cette fois-ci en interrogeant `Orders` au lieu de `Customers` .  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts relatifs aux requêtes](query-concepts.md)
