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
# <a name="what-you-can-do-with-linq-to-sql"></a><span data-ttu-id="f39cb-102">Que faire avec LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f39cb-102">What You Can Do With LINQ to SQL</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f39cb-103">prend en charge toutes les fonctions clés que recherchent les développeurs SQL.</span><span class="sxs-lookup"><span data-stu-id="f39cb-103">supports all the key capabilities you would expect as a SQL developer.</span></span> <span data-ttu-id="f39cb-104">Vous pouvez demander des informations et insérer, mettre à jour et supprimer des informations dans des tables.</span><span class="sxs-lookup"><span data-stu-id="f39cb-104">You can query for information, and insert, update, and delete information from tables.</span></span>  
  
## <a name="selecting"></a><span data-ttu-id="f39cb-105">Sélectionnez</span><span class="sxs-lookup"><span data-stu-id="f39cb-105">Selecting</span></span>  

 <span data-ttu-id="f39cb-106">Pour cela*projection*, il suffit d’écrire une requête LINQ dans votre propre langage de programmation, puis d’exécuter cette requête pour récupérer les résultats.</span><span class="sxs-lookup"><span data-stu-id="f39cb-106">Selecting (*projection*) is achieved by just writing a LINQ query in your own programming language, and then executing that query to retrieve the results.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f39cb-107">traduit lui-même toutes les opérations requises dans les opérations SQL nécessaires que vous connaissez.</span><span class="sxs-lookup"><span data-stu-id="f39cb-107">itself translates all the necessary operations into the necessary SQL operations that you are familiar with.</span></span> <span data-ttu-id="f39cb-108">Pour plus d’informations, consultez [LINQ to SQL](index.md).</span><span class="sxs-lookup"><span data-stu-id="f39cb-108">For more information, see [LINQ to SQL](index.md).</span></span>  
  
 <span data-ttu-id="f39cb-109">Dans l'exemple suivant, les noms de société des clients de Londres sont récupérés et affichés dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="f39cb-109">In the following example, the company names of customers from London are retrieved and displayed in the console window.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a><span data-ttu-id="f39cb-110">Insertion</span><span class="sxs-lookup"><span data-stu-id="f39cb-110">Inserting</span></span>  

 <span data-ttu-id="f39cb-111">Pour exécuter une `Insert`SQL, il vous suffit d'ajouter des objets au modèle objet que vous avez créé et d'appeler <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="f39cb-111">To execute a SQL `Insert`, just add objects to the object model you have created, and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="f39cb-112">Dans l'exemple suivant, un nouveau client et des informations le concernant sont ajoutés à la table `Customers` à l'aide de <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span><span class="sxs-lookup"><span data-stu-id="f39cb-112">In the following example, a new customer and information about the customer is added to the `Customers` table by using <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a><span data-ttu-id="f39cb-113">Mise à jour</span><span class="sxs-lookup"><span data-stu-id="f39cb-113">Updating</span></span>  

 <span data-ttu-id="f39cb-114">Pour `Update` une entrée d'une base de données, récupérez d'abord l'élément et modifiez-le directement dans le modèle objet.</span><span class="sxs-lookup"><span data-stu-id="f39cb-114">To `Update` a database entry, first retrieve the item and edit it directly in the object model.</span></span> <span data-ttu-id="f39cb-115">Après avoir modifié l'objet, appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext> pour mettre la base de données à jour.</span><span class="sxs-lookup"><span data-stu-id="f39cb-115">After you have modified the object, call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to update the database.</span></span>  
  
 <span data-ttu-id="f39cb-116">Dans l'exemple suivant, tous les clients de Londres sont récupérés.</span><span class="sxs-lookup"><span data-stu-id="f39cb-116">In the following example, all customers who are from London are retrieved.</span></span> <span data-ttu-id="f39cb-117">Le nom de ville "London" est ensuite remplacé par "London - Metro".</span><span class="sxs-lookup"><span data-stu-id="f39cb-117">Then the name of the city is changed from "London" to "London - Metro".</span></span> <span data-ttu-id="f39cb-118">Enfin, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelée pour envoyer les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="f39cb-118">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to send the changes to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a><span data-ttu-id="f39cb-119">Suppression</span><span class="sxs-lookup"><span data-stu-id="f39cb-119">Deleting</span></span>  

 <span data-ttu-id="f39cb-120">Pour `Delete` un élément, supprimez-le de la collection à laquelle il appartient, puis appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext> pour valider la modification.</span><span class="sxs-lookup"><span data-stu-id="f39cb-120">To `Delete` an item, remove the item from the collection to which it belongs, and then call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to commit the change.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f39cb-121">ne reconnaît les opérations de suppression en cascade.</span><span class="sxs-lookup"><span data-stu-id="f39cb-121">does not recognize cascade-delete operations.</span></span> <span data-ttu-id="f39cb-122">Si vous souhaitez supprimer une ligne d’une table qui contient des contraintes, consultez [procédure : supprimer des lignes de la base de données](how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="f39cb-122">If you want to delete a row in a table that has constraints against it, see [How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="f39cb-123">Dans l'exemple suivant, le client dont le `CustomerID` est `98128` est extrait de la base de données.</span><span class="sxs-lookup"><span data-stu-id="f39cb-123">In the following example, the customer who has `CustomerID` of `98128` is retrieved from the database.</span></span> <span data-ttu-id="f39cb-124">Ensuite, après confirmation de la récupération de la ligne client, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> est appelé pour supprimer cet objet de la collection.</span><span class="sxs-lookup"><span data-stu-id="f39cb-124">Then, after confirming that the customer row was retrieved, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> is called to remove that object from the collection.</span></span> <span data-ttu-id="f39cb-125">Enfin, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé pour envoyer la suppression à la base de données.</span><span class="sxs-lookup"><span data-stu-id="f39cb-125">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to forward the deletion to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f39cb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f39cb-126">See also</span></span>

- [<span data-ttu-id="f39cb-127">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="f39cb-127">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="f39cb-128">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f39cb-128">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="f39cb-129">Prise en main</span><span class="sxs-lookup"><span data-stu-id="f39cb-129">Getting Started</span></span>](getting-started.md)
