---
title: Ajout de colonnes à un DataTable
description: Un DataTable contient des objets DataColumn référencés par la propriété Columns de la table. Utilisez cet exemple de code pour ajouter des colonnes à une table dans ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 9d6d21696acd7a6b63cfd6d2ea7e906ec2acd7c9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286945"
---
# <a name="adding-columns-to-a-datatable"></a>Ajout de colonnes à un DataTable
Un <xref:System.Data.DataTable> objet contient une collection d' <xref:System.Data.DataColumn> objets référencés par la propriété **Columns** de la table. Cette collection de colonnes, ainsi que toute contrainte, définit le schéma, ou structure, de la table.  
  
 Vous créez des objets **DataColumn** dans une table en utilisant le constructeur **DataColumn** ou en appelant la méthode **Add** de la propriété **Columns** de la table, qui est un <xref:System.Data.DataColumnCollection> . La méthode **Add** accepte les arguments facultatifs **ColumnName**, **DataType**et **expression** et crée un nouveau **DataColumn** en tant que membre de la collection. Il accepte également un objet **DataColumn** existant, l’ajoute à la collection et retourne une référence au **DataColumn** ajouté, le cas échéant. Étant donné que les objets **DataTable** ne sont pas spécifiques à une source de données, les types .NET Framework sont utilisés lors de la spécification du type de données d’un **DataColumn**.  
  
 L’exemple suivant ajoute quatre colonnes à un **DataTable**.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 Dans l’exemple, remarquez que les propriétés de la colonne **CustID** sont définies de façon à ne pas autoriser les valeurs **DBNull** et à contraindre les valeurs à être uniques. Toutefois, si vous définissez la colonne **CustID** comme colonne de clé primaire de la table, la propriété **AllowDBNull** prend automatiquement la valeur **false** et la propriété **unique** prend automatiquement la valeur **true**. Pour plus d’informations, consultez [définition des clés primaires](defining-primary-keys.md).  
  
> [!CAUTION]
> Si un nom de colonne n’est pas fourni pour une colonne, la colonne reçoit un nom incrémentiel par défaut de colonne*N,* commençant par « Column1 », lorsqu’il est ajouté au **DataColumnCollection**. Nous vous recommandons d’éviter la Convention d’affectation de noms « column*N*» lorsque vous fournissez un nom de colonne, car le nom que vous fournissez peut être en conflit avec un nom de colonne par défaut existant dans le **DataColumnCollection**. Si le nom fourni existe déjà, une exception est levée.  
  
 Si vous utilisez <xref:System.Xml.Linq.XElement> en tant que <xref:System.Data.DataColumn.DataType%2A> d'un <xref:System.Data.DataColumn> dans <xref:System.Data.DataTable>, la sérialisation XML ne fonctionnera pas lors de la lecture dans les données. Par exemple, si vous écrivez un <xref:System.Xml.XmlDocument> à l'aide de la méthode `DataTable.WriteXml`, lors de la sérialisation vers XML, un nœud parent supplémentaire est ajouté dans le <xref:System.Xml.Linq.XElement>. Pour contourner ce problème, utilisez le type <xref:System.Data.SqlTypes.SqlXml> à la place de <xref:System.Xml.Linq.XElement>. `ReadXml` et `WriteXml` fonctionnent correctement avec <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [Définition de schéma de DataTable](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
