---
title: Création d'un DataTable à partir d'une requête (LINQ to DataSet)
description: Apprenez à utiliser la méthode CopyToDataTable pour prendre les résultats d’une requête et copier les données dans un DataTable, qui peut ensuite être utilisé pour la liaison de données.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 0a7c8f005b90484ef2f9c7e48218bda40533696a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287010"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Création d'un DataTable à partir d'une requête (LINQ to DataSet)
La liaison de données est une utilisation courante de l’objet <xref:System.Data.DataTable>. La méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> prend les résultats d'une requête et copie les données dans un objet <xref:System.Data.DataTable> qui peut ensuite être utilisé pour la liaison de données. Une fois les opérations de données effectuées, le nouveau <xref:System.Data.DataTable> est refusionné dans le <xref:System.Data.DataTable> source.  
  
 La méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> utilise le processus suivant pour créer un <xref:System.Data.DataTable> à partir d'une requête :  
  
1. La méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> clone une <xref:System.Data.DataTable> de la table source (un objet <xref:System.Data.DataTable> qui implémente l'interface <xref:System.Linq.IQueryable%601>). La <xref:System.Collections.IEnumerable> source provient généralement d’une expression LINQ to DataSet ou d’une requête de méthode.  
  
2. Le schéma de la <xref:System.Data.DataTable> clonée est créé à partir des colonnes du premier objet <xref:System.Data.DataRow> énuméré dans la table source et le nom de la table clonée est celui de la table source auquel le mot « query » est accolé.  
  
3. Pour chaque ligne de la table source, le contenu de la ligne est copié dans un nouvel objet <xref:System.Data.DataRow> qui est ensuite inséré dans la table clonée. Les propriétés <xref:System.Data.DataRow.RowState%2A> et <xref:System.Data.DataRow.RowError%2A> sont conservées dans toute l'opération de copie. Une <xref:System.ArgumentException> est levée si les objets <xref:System.Data.DataRow> dans la source proviennent de différentes tables.  
  
4. Le <xref:System.Data.DataTable> cloné est retourné une fois que tous les objets <xref:System.Data.DataRow> de la table d'entrée interrogeable ont été copiés. Si la séquence source ne contient aucun objet <xref:System.Data.DataRow>, la méthode retourne un <xref:System.Data.DataTable> vide.  
  
L’appel de la <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> méthode entraîne l’exécution de la requête liée à la table source.  
  
 Lorsque la méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> rencontre une référence Null ou un type valeur Nullable dans une ligne de la table source, elle remplace la valeur par <xref:System.DBNull.Value>. De cette manière, les valeurs Null sont gérées correctement dans le <xref:System.Data.DataTable> retourné.  
  
 Remarque : la méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> accepte en entrée une requête qui peut retourner des lignes de plusieurs objets <xref:System.Data.DataTable> ou <xref:System.Data.DataSet>. La méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> copie les données mais pas les propriétés à partir des objets <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> sources vers le <xref:System.Data.DataTable> retourné. Vous devrez définir explicitement les propriétés sur le <xref:System.Data.DataTable> retourné, tel que <xref:System.Data.DataTable.Locale%2A> et <xref:System.Data.DataTable.TableName%2A>.  
  
 L'exemple ci-dessous interroge la table SalesOrderHeader pour obtenir les commandes postérieures au 8 août 2001 et utilise la méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> pour créer un <xref:System.Data.DataTable> à partir de cette requête. Le <xref:System.Data.DataTable> est ensuite lié à une <xref:System.Windows.Forms.BindingSource> qui agit en tant que proxy pour une <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Création d’une méthode CopyToDataTable personnalisée \<T>  
 Les méthodes <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> existantes ne fonctionneront que sur une source <xref:System.Collections.Generic.IEnumerable%601> où le paramètre générique `T` est de type <xref:System.Data.DataRow>. Bien qu'utile, cela ne permet pas de créer des tables à partir d'une séquence de types scalaires, de requêtes qui retournent des types anonymes ou de requêtes qui effectuent des jointures de tables. Pour obtenir un exemple d’implémentation de deux méthodes personnalisées `CopyToDataTable` qui chargent une table à partir d’une séquence de types scalaires ou anonymes, consultez Guide pratique [pour implémenter CopyToDataTable \<T> où le type générique T n’est pas un DataRow](implement-copytodatatable-where-type-not-a-datarow.md).  
  
 Les exemples de cette section utilisent les types personnalisés suivants :  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Exemple  
 Cet exemple effectue une jointure sur les tables `SalesOrderHeader` et `SalesOrderDetail` pour obtenir les commandes en ligne du mois d'août et crée une table à partir d'une requête.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Exemple  
 L’exemple suivant interroge une collection d’articles dont le prix est supérieur à 9,99 $ et crée une table à partir des résultats de la requête.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Exemple  
 L’exemple suivant interroge une collection d’articles dont le prix est supérieur à 9,99 $ et projette les résultats. La séquence de types anonymes retournée est chargée dans une table existante.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Exemple  
 L’exemple suivant interroge une collection d’articles dont le prix est supérieur à 9,99 $ et projette les résultats. La séquence de types anonymes retournée est chargée dans une table existante. Le schéma de la table est automatiquement développé car les types `Book` et `Movies` sont dérivés du type `Item`.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Exemple  
 L’exemple suivant interroge une collection d’articles dont le prix est supérieur à 9,99 $ et retourne une séquence d’objets <xref:System.Double>, laquelle est chargée dans une nouvelle table.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation](programming-guide-linq-to-dataset.md)
- [Méthodes génériques Field et SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
- [Exemples LINQ to DataSet](linq-to-dataset-examples.md)
