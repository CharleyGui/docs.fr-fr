---
title: Filtrage avec DataView (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: 9b4c8e9730dde7d19df9e6a11052ae4591465ea7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177460"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>Filtrage avec DataView (LINQ to DataSet)

La possibilité de filtrer des données en utilisant des critères spécifiques, puis de les présenter à un client à travers un contrôle d’interface utilisateur, est un important aspect de la liaison de données. <xref:System.Data.DataView> propose plusieurs manières de filtrer les données et de retourner des sous-ensembles de lignes de données correspondant à des critères de filtre spécifiques. Outre les fonctions de filtrage basé sur chaîne, <xref:System.Data.DataView> offre également la possibilité d’utiliser des expressions LINQ pour les critères de filtrage. Les expressions LINQ permettent des opérations de filtrage bien plus complexes et puissantes que le filtrage basé sur une chaîne.  
  
 Il existe deux façons de filtrer des données à l'aide d'un <xref:System.Data.DataView> :  
  
- Créez un <xref:System.Data.DataView> à partir d’une requête de LINQ to DataSet avec une clause WHERE.  
  
- Utiliser les fonctionnalités de filtrage basé sur chaîne existantes de <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Création d'un DataView à partir d'une requête avec informations de filtrage  

 Un <xref:System.Data.DataView> objet peut être créé à partir d’une requête de LINQ to DataSet. Si cette requête contient une clause `Where`, le <xref:System.Data.DataView> est créé avec les informations de filtrage de la requête. L'expression dans la clause `Where` sert à déterminer quelles lignes de données seront incluses dans le <xref:System.Data.DataView>, et est la base du filtre.  
  
 Les filtres basés sur une expression offrent une filtrage plus puissant et plus complexe que les filtres basés sur chaîne. Les filtres basés sur chaîne et sur une expression s'excluent mutuellement. Lorsque le <xref:System.Data.DataView.RowFilter%2A> basé sur chaîne est défini après la création d'un <xref:System.Data.DataView> à partir d'une requête, le filtre basé sur une expression déduit de la requête est supprimé.  
  
> [!NOTE]
> Dans la plupart des cas, les expressions utilisées pour le filtrage ne doivent pas avoir d'effets secondaires et doivent être déterministes. De plus, les expressions ne doivent pas contenir de logique dépendant d'un nombre défini d'exécutions, parce que les opérations de filtrage doivent pouvoir être exécutées de façon illimitée.  
  
### <a name="example"></a>Exemple  

 L'exemple suivant interroge la table SalesOrderDetail pour extraire les commandes de quantité supérieure à 2 et inférieure à 6 ; crée un <xref:System.Data.DataView> à partir de cette requête, et lie le <xref:System.Data.DataView> à une <xref:System.Windows.Forms.BindingSource> :  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Exemple  

 L'exemple suivant crée un <xref:System.Data.DataView> à partir d'une requête correspondant aux commandes passées après le 6 juin 2001 :  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Exemple  

 Le filtrage peut également être combiné avec le tri. L'exemple suivant crée un <xref:System.Data.DataView> à partir d'une requête pour les contacts dont le nom commence par la lettre « S » et trié par nom, puis par prénom :  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Exemple  

 L'exemple suivant utilise l'algorithme SoundEx pour rechercher des contacts dont le nom est semblable à « Zhu ». L'algorithme SoundEx est implémenté dans la méthode SoundEx.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx est un algorithme phonétique qui sert à indexer les nom par son, tels qu'ils sont prononcés en anglais, qui a été développé à l'origine par le Bureau du recensement des États-Unis. La méthode SoundEx retourne un code à quatre caractères pour un nom comprenant une lettre alphabétique suivie de trois chiffres. La lettre est la première du nom et les chiffres encodent les consonnes restantes du nom. Les noms de consonance similaire ont le même code SoundEx. L'implémentation SoundEx utilisée dans la méthode SoundEx de l'exemple précédent est illustrée ici :  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>Utilisation de la propriété RowFilter  

 La fonctionnalité de filtrage basé sur chaîne existante de <xref:System.Data.DataView> fonctionne toujours dans le contexte de LINQ to DataSet. Pour plus d’informations sur le filtrage basé sur chaîne <xref:System.Data.DataView.RowFilter%2A> , consultez [Tri et filtrage des données](./dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 L'exemple suivant crée une table <xref:System.Data.DataView> à partir de la table Contact, puis définit la propriété <xref:System.Data.DataView.RowFilter%2A> pour retourner les lignes où le nom du contact est « Zhu » :  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Une fois qu’un <xref:System.Data.DataView> a été créé à partir d’une <xref:System.Data.DataTable> requête ou LINQ to DataSet, vous pouvez utiliser la <xref:System.Data.DataView.RowFilter%2A> propriété pour spécifier des sous-ensembles de lignes en fonction de leurs valeurs de colonne. Les filtres basés sur chaîne et sur une expression s'excluent mutuellement. La définition de la <xref:System.Data.DataView.RowFilter%2A> propriété efface l’expression de filtre déduite de la requête LINQ to DataSet, et l’expression de filtre ne peut pas être réinitialisée.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Si vous souhaitez retourner les résultats d'une requête particulière exécutée sur les données, vous pouvez, au lieu de fournir une vue dynamique d'un sous-ensemble des données, utiliser l'une des méthodes <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> du <xref:System.Data.DataView>, plutôt que de définir la propriété <xref:System.Data.DataView.RowFilter%2A>. L'utilisation de la propriété <xref:System.Data.DataView.RowFilter%2A> est optimale dans une application de liaison de données où un contrôle lié affiche des résultats filtrés. Le paramétrage de la propriété <xref:System.Data.DataView.RowFilter%2A> entraîne une nouvelle génération de l'index des données, ce qui accroît la charge sur votre application et, par voie de conséquence, fait baisser les performances. Les méthodes <xref:System.Data.DataView.Find%2A> et <xref:System.Data.DataView.FindRows%2A> utilisent l'index en cours sans qu'il soit nécessaire de le reconstruire. Si vous ne souhaitez appeler <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> qu'une seule fois, il est préférable d'utiliser le <xref:System.Data.DataView> existant. Si vous souhaitez appeler <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> plusieurs fois, vous devez créer un nouveau <xref:System.Data.DataView> pour reconstruire l'index sur la colonne où vous voulez effectuer la recherche, pour appeler la méthode <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A>. Pour plus d’informations sur <xref:System.Data.DataView.Find%2A> les <xref:System.Data.DataView.FindRows%2A> méthodes et, consultez [recherche de lignes](./dataset-datatable-dataview/finding-rows.md) et performances de [DataView](dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Suppression du filtre  

 Le filtre d'un <xref:System.Data.DataView> peut être supprimé une fois le filtrage défini à l'aide de la propriété <xref:System.Data.DataView.RowFilter%2A>. Le filtre sur un <xref:System.Data.DataView> peut être supprimé de deux manières différentes :  
  
- Affectez à la propriété <xref:System.Data.DataView.RowFilter%2A> la valeur `null`.  
  
- Définissez la propriété <xref:System.Data.DataView.RowFilter%2A> en tant que chaîne vide.  
  
### <a name="example"></a>Exemple  

 L'exemple suivant crée un <xref:System.Data.DataView> à partir d'une requête, puis supprime le filtre en définissant la propriété <xref:System.Data.DataView.RowFilter%2A> sur `null` :  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Exemple  

 L'exemple suivant crée un <xref:System.Data.DataView> à partir d'une table, définit la propriété <xref:System.Data.DataView.RowFilter%2A>, puis supprime le filtre en définissant la propriété <xref:System.Data.DataView.RowFilter%2A> en tant que chaîne vide :  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Voir aussi

- [Liaison de données et LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [Tri avec DataView](sorting-with-dataview-linq-to-dataset.md)
