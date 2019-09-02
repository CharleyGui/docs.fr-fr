---
title: Ajout de DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: fde1e2ace09e31234d199876ae7f063e01e7a7e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203970"
---
# <a name="adding-datarelations"></a>Ajout de DataRelations
Dans un objet <xref:System.Data.DataSet> contenant plusieurs objets <xref:System.Data.DataTable>, vous pouvez utiliser des objets <xref:System.Data.DataRelation> pour associer une table à une autre, pour vous déplacer dans les tables et pour retourner les lignes enfants ou parentes d'une table associée.  
  
 Les arguments requis pour créer un **DataRelation** sont un nom pour le **DataRelation** créé et un tableau d’une ou plusieurs <xref:System.Data.DataColumn> références aux colonnes qui servent de colonnes parent et enfant dans la relation. Une fois que vous avez créé un **DataRelation**, vous pouvez l’utiliser pour naviguer entre les tables et récupérer des valeurs.  
  
 L’ajout d’un DataRelation <xref:System.Data.DataSet> à un ajoute, <xref:System.Data.UniqueConstraint> par défaut, à la table parente <xref:System.Data.ForeignKeyConstraint> et à la table enfant. Pour plus d’informations sur ces contraintes par défaut, consultez [contraintes de DataTable](datatable-constraints.md).  
  
 L’exemple de code suivant crée un **DataRelation** à <xref:System.Data.DataTable> l’aide de <xref:System.Data.DataSet>deux objets dans un. Chaque <xref:System.Data.DataTable> contient une colonne nommée **CustID**, qui sert de lien entre les deux <xref:System.Data.DataTable> objets. L’exemple ajoute un seul **DataRelation** à la <xref:System.Data.DataSet>collection relations de. Le premier argument de l’exemple spécifie le nom du **DataRelation** en cours de création. Le deuxième argument définit le **DataColumn** parent et le troisième argument définit le **DataColumn**enfant.  
  
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
  
 Un **DataRelation** a également une propriété imbriquée qui, lorsqu’elle est définie sur **true**, fait en sorte que les lignes de la table enfant soient imbriquées dans la ligne associée de la table parente lorsqu' <xref:System.Data.DataSet.WriteXml%2A> elles sont écrites en tant qu’éléments XML à l’aide de. Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Voir aussi

- [DataSets, DataTables et DataViews](index.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
