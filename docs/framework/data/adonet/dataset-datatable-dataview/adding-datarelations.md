---
title: Ajout de DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 5fe2bd45e0abada1f9ec7071e3863da853479b51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202381"
---
# <a name="adding-datarelations"></a>Ajout de DataRelations

Dans un objet <xref:System.Data.DataSet> contenant plusieurs objets <xref:System.Data.DataTable>, vous pouvez utiliser des objets <xref:System.Data.DataRelation> pour associer une table à une autre, pour vous déplacer dans les tables et pour retourner les lignes enfants ou parentes d'une table associée.  
  
 Les arguments requis pour créer un **DataRelation** sont un nom pour le **DataRelation** créé et un tableau d’une ou plusieurs <xref:System.Data.DataColumn> références aux colonnes qui servent de colonnes parent et enfant dans la relation. Une fois que vous avez créé un **DataRelation**, vous pouvez l’utiliser pour naviguer entre les tables et récupérer des valeurs.  
  
 L’ajout d’un **DataRelation** à un <xref:System.Data.DataSet> ajoute, par défaut, <xref:System.Data.UniqueConstraint> à la table parente et <xref:System.Data.ForeignKeyConstraint> à la table enfant. Pour plus d’informations sur ces contraintes par défaut, consultez [contraintes de DataTable](datatable-constraints.md).  
  
 L’exemple de code suivant crée un **DataRelation** à l’aide <xref:System.Data.DataTable> de deux objets dans un <xref:System.Data.DataSet> . Chaque <xref:System.Data.DataTable> contient une colonne nommée **CustID**, qui sert de lien entre les deux <xref:System.Data.DataTable> objets. L’exemple ajoute un seul **DataRelation** à la collection **relations** de <xref:System.Data.DataSet> . Le premier argument de l’exemple spécifie le nom du **DataRelation** en cours de création. Le deuxième argument définit le **DataColumn** parent et le troisième argument définit le **DataColumn**enfant.  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 Un **DataRelation** a également une propriété **imbriquée** qui, lorsqu’elle est définie sur **true**, fait en sorte que les lignes de la table enfant soient imbriquées dans la ligne associée de la table parente lorsqu’elles sont écrites en tant qu’éléments XML à l’aide de <xref:System.Data.DataSet.WriteXml%2A> . Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Voir aussi

- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
