---
title: Comparaison entre le chargement différé et le chargement immédiat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
ms.openlocfilehash: 4e2cb7c90eb703985cbb1b8673522a9e253564d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164296"
---
# <a name="deferred-versus-immediate-loading"></a>Comparaison entre le chargement différé et le chargement immédiat

Lorsque vous recherchez un objet, vous récupérez en réalité uniquement l'objet que vous avez demandé. Les objets *connexes* ne sont pas automatiquement extraits en même temps. (Pour plus d’informations, consultez [interrogation des relations](querying-across-relationships.md).) Vous ne pouvez pas voir le fait que les objets connexes ne sont pas déjà chargés, car une tentative d’accès produit une demande qui les récupère.  
  
 Par exemple, vous souhaiterez peut-être interroger un ensemble spécifique de commandes, puis envoyer occasionnellement une notification par courrier électronique à des clients particuliers. Vous n'auriez pas nécessairement besoin de récupérer au début toutes les données des clients pour chaque commande. Vous pouvez utiliser le chargement différé pour différer la récupération d'informations supplémentaires jusqu'au moment où cela devient indispensable. Prenons l’exemple suivant :  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 Le contraire peut être également vrai. Supposons que vous avez une application qui nécessite d'afficher en même temps les données sur les clients et les commandes. Vous savez que vous avez besoin de ces deux groupes de données. Vous savez également que votre application a besoin des informations relatives aux commandes pour chaque client dès que vous obtenez les résultats. Vous ne voulez pas exécuter des requêtes individuelles pour les commandes de chaque client et vous souhaitez principalement récupérer les données sur les commandes avec les clients.  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 Vous pouvez également associer les clients et les commandes dans une requête à l'aide du produit croisé et en récupérant tous les bits relatifs des données sous forme d'une grande projection. Toutefois, ces résultats ne sont pas des entités. (Pour plus d’informations, consultez [le modèle objet LINQ to SQL](the-linq-to-sql-object-model.md)). Les entités sont des objets qui ont une identité et que vous pouvez modifier, alors que ces résultats seraient des projections qui ne peuvent pas être modifiées et rendues persistantes. Dans le pire des cas, vous récupéreriez beaucoup de données redondantes, étant donné que chaque client est répété pour chaque commande dans les résultats de la jointure à deux dimensions.  
  
 Vous avez principalement besoin d'une méthode pour récupérer simultanément un ensemble d'objets connexes. Cet ensemble est une section délimitée d'un graphique pour que vous ne récupériez jamais plus ou moins de données nécessaires que prévu pour votre utilisation. À cet effet, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit le <xref:System.Data.Linq.DataLoadOptions> chargement immédiat d’une région de votre modèle objet. Méthodes incluses :  
  
- Méthode <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> pour charger immédiatement des données en rapport avec la cible principale.  
  
- Méthode <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> pour filtrer des objets récupérés pour une relation particulière.  
  
## <a name="see-also"></a>Voir aussi

- [Concepts relatifs aux requêtes](query-concepts.md)
