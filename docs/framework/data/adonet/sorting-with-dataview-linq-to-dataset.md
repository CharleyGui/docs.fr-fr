---
title: Tri avec DataView (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: dda7d4c376fd2cf447c676d77eae824d62144887
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649592"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>Tri avec DataView (LINQ to DataSet)
La possibilité de trier des données en utilisant des critères spécifiques, puis de les présenter à un client via un contrôle d’interface utilisateur, est un important aspect de la liaison de données. <xref:System.Data.DataView> propose plusieurs manières de trier les données et de retourner des sous-ensembles de lignes de données triés suivant des critères de tri spécifiques. En plus de sa chaîne-en fonction des fonctionnalités, de tri <xref:System.Data.DataView> vous permet également d’utiliser [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] expressions pour les critères de tri. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] les expressions permettent des opérations de tri beaucoup plus complexes et puissantes que le tri basé sur chaîne. Cette rubrique décrit les deux approches du tri à l'aide de <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Création d'un DataView à partir d'une requête avec des informations de tri  
 Un objet <xref:System.Data.DataView> peut être créé à partir d'une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Si cette requête contient un <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, ou <xref:System.Linq.Enumerable.ThenByDescending%2A> clause les expressions de ces clauses sont utilisées comme base pour trier les données dans le <xref:System.Data.DataView>. Par exemple, si la requête contient le `Order By…`et `Then By…` clauses, résultant <xref:System.Data.DataView> trie les données selon les deux colonnes spécifiées.  
  
 Le tri basé sur une expression offre un tri plus puissant et plus complexe que le tri basé sur chaîne. Notez que les tris basés sur chaîne et sur une expression s'excluent mutuellement. Si le <xref:System.Data.DataView.Sort%2A> basé sur chaîne après la création d'un <xref:System.Data.DataView> à partir d'une requête, le filtre basé sur une expression déduit de la requête est supprimé et ne peut pas être réinitialisé.  
  
 L'index d'un <xref:System.Data.DataView> est construit à la fois lors de la création du <xref:System.Data.DataView> et lorsque l'une des informations de tri ou de filtrage est modifiée. Vous obtenez des performances optimales en fournissant des critères de tri dans la requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] à partir de laquelle le <xref:System.Data.DataView> est créé et en ne modifiant pas ultérieurement les informations de tri. Pour plus d’informations, consultez [DataView performances](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
> [!NOTE]
>  Dans la plupart des cas, les expressions utilisées pour le tri ne doivent pas avoir d'effets secondaires et doivent être déterministes. De plus, les expressions ne doivent pas contenir de logique dépendant d'un nombre défini d'exécutions, parce que les opérations de tri doivent pouvoir être exécutées de façon illimitée.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant interroge la table SalesOrderHeader et trie les lignes retournées par date de commande ; crée un <xref:System.Data.DataView> à partir de cette requête, et lie le <xref:System.Data.DataView> à une <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Exemple  
 L'exemple suivant interroge la table SalesOrderHeader et trie la ligne retournée par montant total dû ; crée un <xref:System.Data.DataView> à partir de cette requête, et lie le <xref:System.Data.DataView> à une <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Exemple  
 L'exemple suivant interroge la table SalesOrderDetail et trie les lignes retournées par quantité commandée, puis par ID de commande ; crée un <xref:System.Data.DataView> à partir de cette requête, et lie le <xref:System.Data.DataView> à une <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Utilisation de la propriété de tri basé sur chaîne  
 La fonctionnalité de tri basé sur chaîne existante de <xref:System.Data.DataView> fonctionne toujours avec [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  Après qu'un <xref:System.Data.DataView> a été créé à partir d'une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], vous pouvez utiliser la propriété <xref:System.Data.DataView.Sort%2A> pour définir le tri du <xref:System.Data.DataView>.  
  
 Les fonctionnalités de tri basé sur chaîne et sur une expression s'excluent mutuellement. La définition de la propriété <xref:System.Data.DataView.Sort%2A> efface le tri basé sur des expressions hérité de la requête à partir de laquelle le <xref:System.Data.DataView> a été créé.  
  
 Pour plus d’informations sur basé sur chaîne <xref:System.Data.DataView.Sort%2A> filtrage, consultez [de tri et filtrage des données](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant crée un <xref:System.Data.DataView> à partir de la table Contact, puis trie les lignes par nom par ordre décroissant, puis les prénoms par ordre croissant :  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Exemple  
 L'exemple suivant interroge la table Contact pour extraire les noms commençant par la lettre « S ».  Un <xref:System.Data.DataView> est créé à partir de cette requête et lié à un objet <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Suppression du tri  
 Les informations de tri d'un <xref:System.Data.DataView> peuvent être supprimées une fois qu'il a été défini à l'aide de la propriété <xref:System.Data.DataView.Sort%2A>. Il existe deux façons de supprimer les informations de tri d'un <xref:System.Data.DataView> :  
  
- Affectez à la propriété <xref:System.Data.DataView.Sort%2A> la valeur `null`.  
  
- Définissez la propriété <xref:System.Data.DataView.Sort%2A> en tant que chaîne vide.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant crée un <xref:System.Data.DataView> à partir d'une requête, puis supprime le tri en définissant la propriété <xref:System.Data.DataView.Sort%2A> en tant que chaîne vide :  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Exemple  
 L'exemple suivant crée une table <xref:System.Data.DataView> à partir de la table Contact, puis définit la propriété <xref:System.Data.DataView.Sort%2A> pour effectuer un tri des noms par ordre décroissant : Les informations de tri sont ensuite effacées en définissant la propriété <xref:System.Data.DataView.Sort%2A> sur `null` :  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Voir aussi

- [Liaison de données et LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [Filtrage avec DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)
- [Tri des données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))
