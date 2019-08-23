---
title: Création d'un DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: b56d2f8cd46f3184f1001c8bd6a70dbfc4968968
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937028"
---
# <a name="creating-a-datatable"></a>Création d'un DataTable
Un objet <xref:System.Data.DataTable>, qui représente une table de données relationnelles en mémoire, peut être créé et utilisé de façon indépendante. Il peut également être utilisé par d'autres objets .NET Framework, la plupart du temps comme membre d'un objet <xref:System.Data.DataSet>.  
  
 Vous pouvez créer un objet **DataTable** à l’aide du constructeur **DataTable** approprié. Vous pouvez l’ajouter au **DataSet** à l’aide de la méthode **Add** pour l’ajouter à la collection **tables** de l’objet **DataTable** .  
  
 Vous pouvez également créer des objets **DataTable** dans un **DataSet** à l’aide des méthodes **Fill** ou **FillSchema** de l’objet **DataAdapter** , ou à partir d’un schéma XML prédéfini ou inféré à l’aide de **ReadXml**, **ReadXmlSchema** , ou les méthodes **InferXmlSchema** du **DataSet**. Notez qu’une fois que vous avez ajouté un **DataTable** comme membre de la collection **tables** d’un **DataSet**, vous ne pouvez pas l’ajouter à la collection de tables d’un autre **DataSet**.  
  
 Quand vous créez un **DataTable**pour la première fois, il n’a pas de schéma (c’est-à-dire une structure). Pour définir le schéma de la table, vous devez créer et ajouter <xref:System.Data.DataColumn> des objets à la collection **Columns** de la table. Vous pouvez également définir une colonne de clé primaire pour la table et créer et ajouter des objets de **contrainte** à la collection Constraints de la table. Après avoir défini le schéma d’un **DataTable**, vous pouvez ajouter des lignes de données à la table en ajoutant des objets **DataRow** à la collection **Rows** de la table.  
  
 Vous n’êtes pas obligé de fournir une valeur pour <xref:System.Data.DataTable.TableName%2A> la propriété lorsque vous créez un **DataTable**; vous pouvez spécifier la propriété à un autre moment, ou la conserver vide. Toutefois, lorsque vous ajoutez une table sans valeur **TableName** à un **jeu de données**, la table reçoit un nom incrémentiel par défaut de table*N*, commençant par «table» pour Table0.  
  
> [!NOTE]
> Nous vous recommandons d’éviter la Convention d’affectation de noms «table*N*» lorsque vous fournissez une valeur **TableName** , car le nom que vous fournissez peut être en conflit avec un nom de table par défaut existant dans le **jeu de données**. Si le nom fourni existe déjà, une exception est levée.  
  
 L’exemple suivant crée une instance d’un objet **DataTable** et lui attribue le nom «Customers».  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 L’exemple suivant crée une instance d’un **DataTable** en l’ajoutant à la collection **tables** d’un **DataSet**.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [Remplissage d’un DataSet à partir d’un DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [Chargement d’un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Chargement des informations de schéma de DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
