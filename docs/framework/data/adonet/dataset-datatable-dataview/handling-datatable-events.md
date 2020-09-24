---
title: Gestion des événements de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: c00e5e42508160a210d16f058c46afbf62ae0ee0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164725"
---
# <a name="handling-datatable-events"></a>Gestion des événements de DataTable

L'objet <xref:System.Data.DataTable> fournit une série d'événements pouvant être traités par une application. Le tableau ci-dessous décrit les événements `DataTable`.  
  
|Événement|Description|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Se produit après que la méthode <xref:System.Data.DataTable.EndInit%2A> d'un `DataTable` a été appelée. Cet événement est destiné principalement à prendre en charge les scénarios au moment du design.|  
|<xref:System.Data.DataTable.ColumnChanged>|Se produit après qu'une valeur a été modifiée avec succès dans un <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|Se produit quand une valeur a été proposée pour un `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|Se produit après qu'une valeur `DataColumn` ou le <xref:System.Data.DataRow.RowState%2A> d'un <xref:System.Data.DataRow> ont été modifiés avec succès dans le `DataTable`.|  
|<xref:System.Data.DataTable.RowChanging>|Se produit quand une modification a été proposée pour une valeur `DataColumn` ou le `RowState` d'un `DataRow` dans le `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Se produit après qu'un `DataRow` dans le `DataTable` a été marqué comme `Deleted`.|  
|<xref:System.Data.DataTable.RowDeleting>|Se produit avant qu'un `DataRow` dans le `DataTable` soit marqué comme `Deleted`.|  
|<xref:System.Data.DataTable.TableCleared>|Se produit après qu'un appel à la méthode <xref:System.Data.DataTable.Clear%2A> du `DataTable` a effacé avec succès chaque `DataRow`.|  
|<xref:System.Data.DataTable.TableClearing>|Se produit après que la méthode `Clear` a été appelée mais avant que l'opération `Clear` commence.|  
|<xref:System.Data.DataTable.TableNewRow>|Se produit après la création d'un nouveau `DataRow` par un appel à la méthode `NewRow` du `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Se produit lorsque le `DataTable` a la valeur `Disposed`. Hérité de <xref:System.ComponentModel.MarshalByValueComponent>.|  
  
> [!NOTE]
> La plupart des opérations qui ajoutent ou suppriment des lignes ne déclenchent pas les événements `ColumnChanged` et `ColumnChanging`. Toutefois, la méthode `ReadXml` déclenche les événements `ColumnChanged` et `ColumnChanging`, à moins que `XmlReadMode` ait la valeur `DiffGram` ou `Auto` lorsque le document XML lu est un `DiffGram`.  
  
> [!WARNING]
> Les données peuvent être endommagées si elles sont modifiées dans un `DataSet` à partir duquel l'événement `RowChanged` est déclenché. Aucune exception n'est levée en cas d'endommagement de ce type.  
  
## <a name="additional-related-events"></a>Autres événements liés  

 La propriété <xref:System.Data.DataTable.Constraints%2A> détient une instance <xref:System.Data.ConstraintCollection>. La classe <xref:System.Data.ConstraintCollection> expose un événement <xref:System.Data.ConstraintCollection.CollectionChanged>. Cet événement se déclenche lorsqu'une contrainte est ajoutée, modifiée ou supprimée dans `ConstraintCollection`.  
  
 La propriété <xref:System.Data.DataTable.Columns%2A> détient une instance <xref:System.Data.DataColumnCollection>. La classe `DataColumnCollection` expose un événement <xref:System.Data.DataColumnCollection.CollectionChanged>. Cet événement se déclenche lorsqu'un `DataColumn` est ajouté, modifié ou supprimé dans `DataColumnCollection`. Les modifications à l'origine du déclenchement de l'événement incluent des modifications du nom, du type, de l'expression ou de la position ordinale d'une colonne.  
  
 La propriété <xref:System.Data.DataSet.Tables%2A> d'un <xref:System.Data.DataSet> détient une instance <xref:System.Data.DataTableCollection>. La classe `DataTableCollection` expose un événement `CollectionChanged` et un événement `CollectionChanging`. Ces événements se déclenchent lorsqu'un `DataTable` est ajouté ou supprimé dans le `DataSet`.  
  
 Les modifications apportées aux `DataRows` peuvent également déclencher des événements pour un <xref:System.Data.DataView> associé. La classe `DataView` expose un événement <xref:System.Data.DataView.ListChanged> qui se déclenche lorsqu'une valeur `DataColumn` change ou lorsque la composition ou l'ordre de tri de la vue changent. La classe <xref:System.Data.DataRowView> expose un événement <xref:System.Data.DataRowView.PropertyChanged> qui se déclenche lorsqu'une valeur `DataColumn` associée change.  
  
## <a name="sequence-of-operations"></a>Ordre des opérations  

 Voici l'ordre des opérations qui se produisent lorsqu'un `DataRow` est ajouté, modifié ou supprimé :  
  
1. Créez l'enregistrement proposé et appliquez les modifications éventuelles.  
  
2. Vérifiez les contraintes pour les colonnes autres que les colonnes d'expression.  
  
3. Déclenchez les événements `RowChanging` ou `RowDeleting` selon les besoins.  
  
4. Définissez l'enregistrement proposé comme enregistrement en cours.  
  
5. Mettez à jour les index associés éventuels.  
  
6. Déclenchez les événements `ListChanged` pour les objets `DataView` associés et les événements `PropertyChanged` pour les objets `DataRowView` associés.  
  
7. Évaluez toutes les colonnes d'expression, mais retardez la vérification des contraintes éventuelles sur ces colonnes.  
  
8. Déclenchez les événements `ListChanged` pour les objets `DataView` associés et les événements `PropertyChanged` pour les objets `DataRowView` associés affectés par les évaluations des colonnes d'expression.  
  
9. Déclenchez les événements `RowChanged` ou `RowDeleted` selon les besoins.  
  
10. Vérifiez les contraintes sur les colonnes d'expression.  
  
> [!NOTE]
> Des modifications apportées aux colonnes d'expression ne déclenchent jamais des événements `DataTable`. Des modifications apportées aux colonnes d'expression déclenchent uniquement des événements `DataView` et `DataRowView`. Les colonnes d'expression peuvent avoir des dépendances sur plusieurs autres colonnes et peuvent être évaluées plusieurs fois au cours d'une même opération `DataRow`. Chaque évaluation d'expression déclenche des événements et une opération `DataRow` individuelle peut déclencher plusieurs événements `ListChanged` et `PropertyChanged` lorsque des colonnes d'expression sont affectées, dont éventuellement plusieurs événements pour une même colonne d'expression.  
  
> [!WARNING]
> Ne levez pas de <xref:System.NullReferenceException> à l'intérieur du gestionnaire d'événements `RowChanged`. Si une <xref:System.NullReferenceException> est levée à l'intérieur de l'événement `RowChanged` d'une `DataTable`, `DataTable` sera corrompue.  
  
### <a name="example"></a>Exemple  

 L'exemple ci-dessous montre comment créer des gestionnaires d'événements pour les événements `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared` et `TableClearing`. Chaque gestionnaire d'événements affiche la sortie dans la fenêtre de console lorsqu'il est déclenché.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Manipulation des données dans un DataTable](manipulating-data-in-a-datatable.md)
- [Gestion des événements DataAdapter](../handling-dataadapter-events.md)
- [Gestion des événements de DataSet](handling-dataset-events.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
