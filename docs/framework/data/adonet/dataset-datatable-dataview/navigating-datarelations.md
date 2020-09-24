---
title: Parcours des DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 5eb2ee16712be5ccd5e9aa0af4dde22dcaaeea09
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148384"
---
# <a name="navigating-datarelations"></a>Parcours des DataRelations

L'une des principales fonctions d'un objet <xref:System.Data.DataRelation> est de permettre de passer d'un objet <xref:System.Data.DataTable> à un autre à l'intérieur d'un objet <xref:System.Data.DataSet>. Cela vous permet de récupérer tous les <xref:System.Data.DataRow> objets connexes dans un **DataTable** lorsqu’un **DataRow** unique est donné à partir d’un **DataTable**associé. Par exemple, après avoir établi un **DataRelation** entre une table de clients et une table de commandes, vous pouvez récupérer toutes les lignes de commande pour une ligne de client particulière à l’aide de **GetChildRows**.  
  
 L’exemple de code suivant crée un **DataRelation** entre la table **Customers** et la table **Orders** d’un **DataSet** et retourne toutes les commandes pour chaque client.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 L'exemple suivant s'appuie sur le précédent, en créant des relations entre quatre tables et en explorant ces relations. Comme dans l’exemple précédent, **CustomerID** lie la table **Customers** à la table **Orders** . Pour chaque client de la table **Customers** , toutes les lignes enfants de la table **Orders** sont déterminées, afin de retourner le nombre de commandes d’un client particulier et leurs valeurs **OrderID** .  
  
 L’exemple développé retourne également les valeurs des tables **OrderDetails** et **Products** . La table **Orders** est associée à la table **OrderDetails** avec **OrderID** pour déterminer, pour chaque commande client, les produits et quantités commandés. Étant donné que la table **OrderDetails** contient uniquement le **ProductID** d’un produit commandé, **OrderDetails** est lié à **Products** à l’aide de **ProductID** afin de retourner le **ProductName**. Dans cette relation, la table **Products** est le parent et la table **Order Details** est l’enfant. Par conséquent, lors de l’itération au sein de la table **OrderDetails** , **GetParentRow** est appelé pour extraire la valeur **ProductName** associée.  
  
 Notez que lorsque le **DataRelation** est créé pour les tables **Customers** et **Orders** , aucune valeur n’est spécifiée pour l’indicateur **createConstraints** (la valeur par défaut est **true**). Cela suppose que toutes les lignes de la table **Orders** ont une valeur **CustomerID** qui existe dans la table **Customers** parent. Si un **CustomerID** existe dans la table **Orders** et qu’il n’existe pas dans la table **Customers** , une <xref:System.Data.ForeignKeyConstraint> exception est levée.  
  
 Lorsque la colonne enfant peut contenir des valeurs qui ne sont pas contenues dans la colonne parente, affectez la valeur **false** à l’indicateur **createConstraints** lors de l’ajout du **DataRelation**. Dans l’exemple, l’indicateur **createConstraints** est défini sur **false** pour le **DataRelation** entre la table **Orders** et la table **OrderDetails** . Cela permet à l’application de retourner tous les enregistrements de la table **OrderDetails** et uniquement un sous-ensemble d’enregistrements de la table **Orders** sans générer d’exception Runtime. La sortie de l’exemple développé se présente comme suit.  
  
```output  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 L’exemple de code suivant est un exemple développé où les valeurs des tables **OrderDetails** et **Products** sont retournées, avec seulement un sous-ensemble des enregistrements de la table **Orders** en cours de retour.  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
