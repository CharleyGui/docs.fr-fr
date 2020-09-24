---
title: Que faire avec LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: a2e65cb558eec3cec21ea0efbcc66bb8c56ec7b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163919"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>Que faire avec LINQ to SQL

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge toutes les fonctions clés que recherchent les développeurs SQL. Vous pouvez demander des informations et insérer, mettre à jour et supprimer des informations dans des tables.  
  
## <a name="selecting"></a>Sélectionnez  

 Pour cela*projection*, il suffit d’écrire une requête LINQ dans votre propre langage de programmation, puis d’exécuter cette requête pour récupérer les résultats. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit lui-même toutes les opérations requises dans les opérations SQL nécessaires que vous connaissez. Pour plus d’informations, consultez [LINQ to SQL](index.md).  
  
 Dans l'exemple suivant, les noms de société des clients de Londres sont récupérés et affichés dans la fenêtre de console.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Insertion  

 Pour exécuter une `Insert`SQL, il vous suffit d'ajouter des objets au modèle objet que vous avez créé et d'appeler <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext>.  
  
 Dans l'exemple suivant, un nouveau client et des informations le concernant sont ajoutés à la table `Customers` à l'aide de <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Mise à jour  

 Pour `Update` une entrée d'une base de données, récupérez d'abord l'élément et modifiez-le directement dans le modèle objet. Après avoir modifié l'objet, appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext> pour mettre la base de données à jour.  
  
 Dans l'exemple suivant, tous les clients de Londres sont récupérés. Le nom de ville "London" est ensuite remplacé par "London - Metro". Enfin, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelée pour envoyer les modifications à la base de données.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Suppression  

 Pour `Delete` un élément, supprimez-le de la collection à laquelle il appartient, puis appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext> pour valider la modification.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne reconnaît les opérations de suppression en cascade. Si vous souhaitez supprimer une ligne d’une table qui contient des contraintes, consultez [procédure : supprimer des lignes de la base de données](how-to-delete-rows-from-the-database.md).  
  
 Dans l'exemple suivant, le client dont le `CustomerID` est `98128` est extrait de la base de données. Ensuite, après confirmation de la récupération de la ligne client, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> est appelé pour supprimer cet objet de la collection. Enfin, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé pour envoyer la suppression à la base de données.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation](programming-guide.md)
- [Modèle objet LINQ to SQL](the-linq-to-sql-object-model.md)
- [Prise en main](getting-started.md)
