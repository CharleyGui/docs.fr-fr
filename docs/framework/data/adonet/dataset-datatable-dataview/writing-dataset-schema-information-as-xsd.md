---
title: Écriture des informations de schéma de DataSet comme XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 7634dfc8415b6f73fc60f2ebe59c92a0c31f83a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173729"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Écriture des informations de schéma de DataSet comme XSD

Vous pouvez écrire le schéma d'un objet <xref:System.Data.DataSet> sous la forme d'un schéma en langage XSD (XML Schema Definition), de façon à pouvoir le transporter, avec ou sans les données connexes, dans un document XML. Le schéma XML peut être écrit dans un fichier, un flux, un <xref:System.Xml.XmlWriter> ou une chaîne ; il est utile pour générer un **DataSet**fortement typé. Pour plus d’informations sur les objets **DataSet** fortement typés, consultez [DataSets typés](typed-datasets.md).  
  
 Vous pouvez spécifier la façon dont une colonne d’une table est représentée dans le schéma XML à l’aide de la propriété **ColumnMapping** de l' <xref:System.Data.DataColumn> objet. Pour plus d’informations, consultez « mappage de colonnes à des éléments, des attributs et du texte XML » dans écriture du contenu d’un [DataSet en tant que données XML](writing-dataset-contents-as-xml-data.md).  
  
 Pour écrire le schéma d’un **DataSet** sous forme de schéma XML, dans un fichier, un flux ou un **XmlWriter**, utilisez la méthode **WriteXmlSchema** du **DataSet**. **WriteXmlSchema** accepte un paramètre qui spécifie la destination du schéma XML résultant. Les exemples de code suivants montrent comment écrire le schéma XML d’un **DataSet** dans un fichier en passant une chaîne contenant un nom de fichier et un <xref:System.IO.StreamWriter> objet.  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 Pour obtenir le schéma d’un **DataSet** et l’écrire sous la forme d’une chaîne de schéma XML, utilisez la méthode **GetXmlSchema** , comme indiqué dans l’exemple suivant.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [Écriture du contenu d'un DataSet comme données XML](writing-dataset-contents-as-xml-data.md)
- [Datasets typés](typed-datasets.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
