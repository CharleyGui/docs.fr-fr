---
title: Écriture du contenu d'un DataSet comme données XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: c8a5c747e4ec60fcb97edf631aa3a0ae184ffec5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173716"
---
# <a name="writing-dataset-contents-as-xml-data"></a>Écriture du contenu d'un DataSet comme données XML

Dans ADO.NET, vous pouvez écrire une représentation XML d'un objet<xref:System.Data.DataSet>, avec ou sans son schéma. Si les informations de schéma sont incluses inline avec le XML, elles sont écrites à l'aide du langage XSD (XML Schema Definition). Le schéma contient les définitions des tables de l'objet <xref:System.Data.DataSet>, ainsi que les définitions des relations et des contraintes.  
  
 Lorsqu'un objet <xref:System.Data.DataSet> est écrit sous forme de données XML, les lignes de l'objet <xref:System.Data.DataSet> sont écrites dans leur version actuelle. Toutefois, l'objet <xref:System.Data.DataSet> peut aussi être écrit sous la forme d'un DiffGram pour que les valeurs actuelles comme les valeurs d'origine des lignes soient incluses.  
  
 La représentation XML du <xref:System.Data.DataSet> peut être écrite dans un fichier, un flux, un **XmlWriter**ou une chaîne. Ces différentes possibilités offrent une grande souplesse pour le transport de la représentation XML de l'objet <xref:System.Data.DataSet>. Pour obtenir la représentation XML de <xref:System.Data.DataSet> sous forme de chaîne, utilisez la méthode **GetXml** comme indiqué dans l’exemple suivant.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml** retourne la représentation XML du <xref:System.Data.DataSet> sans informations de schéma. Pour écrire les informations de schéma à partir du <xref:System.Data.DataSet> (comme schéma XML) dans une chaîne, utilisez **GetXmlSchema**.  
  
 Pour écrire <xref:System.Data.DataSet> dans un fichier, un flux ou un **XmlWriter**, utilisez la méthode **WriteXml** . Le premier paramètre que vous transmettez à **WriteXml** est la destination de la sortie XML. Par exemple, transmettez une chaîne contenant un nom de fichier, un objet **System. IO. TextWriter** , et ainsi de suite. Vous pouvez passer un deuxième paramètre facultatif d’un **XmlWriteMode** pour spécifier le mode d’écriture de la sortie XML.  
  
 Le tableau suivant présente les options de **XmlWriteMode**.  
  
|Option XmlWriteMode|Description|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Écrit le contenu actuel de l'objet <xref:System.Data.DataSet> sous forme de données XML, sans schéma XML. Il s’agit de la valeur par défaut.|  
|**WriteSchema**|Écrit le contenu actuel de l'objet <xref:System.Data.DataSet> en tant que données XML, avec la structure relationnelle comme schéma XML inline.|  
|**DiffGram**|Écrit l'ensemble de l'objet <xref:System.Data.DataSet> en tant que DiffGram, y compris les valeurs d'origine et actuelle. Pour plus d’informations, consultez [DiffGrams](diffgrams.md).|  
  
 Lors de l’écriture d’une représentation XML d’un <xref:System.Data.DataSet> qui contient des objets **DataRelation** , vous souhaiterez probablement que le XML obtenu ait les lignes enfants de chaque relation imbriquées dans leurs éléments parents associés. Pour ce faire, affectez la **valeur true** à la propriété **Nested** du **DataRelation** lorsque vous ajoutez le **DataRelation** à <xref:System.Data.DataSet> . Pour plus d’informations, consultez [imbrication de DataRelations](nesting-datarelations.md).  
  
 Voici deux exemples d’écriture de la représentation XML d’un <xref:System.Data.DataSet> dans un fichier. Le premier exemple passe le nom de fichier pour le XML résultant en tant que chaîne à **WriteXml**. Le deuxième exemple passe un objet **System. IO. StreamWriter** .
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>Mappage de colonnes à des éléments, des attributs et du texte XML  

 Vous pouvez spécifier la façon dont une colonne d’une table est représentée en XML à l’aide de la propriété **ColumnMapping** de l’objet **DataColumn** . Le tableau suivant présente les différentes valeurs de **MappingType** pour la propriété **ColumnMapping** d’une colonne de table, ainsi que les données XML résultantes.  
  
|Valeur MappingType|Description|  
|-----------------------|-----------------|  
|**Element**|Il s’agit de la valeur par défaut. La colonne est écrite sous la forme d'un élément XML, où ColumnName représente le nom de l'élément et le contenu de la colonne est écrit en tant que texte de l'élément. Par exemple :<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Attribut**|La colonne est écrite sous la forme d'un attribut XML de l'élément XML de la ligne actuelle, où ColumnName représente le nom de l'attribut et le contenu de la colonne est écrit en tant que valeur de l'attribut. Par exemple :<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|Le contenu de la colonne est écrit sous forme de texte dans l'élément XML de la ligne actuelle. Par exemple :<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Notez que **simpleContent** ne peut pas être défini pour une colonne d’une table qui contient des colonnes d' **éléments** ou des relations imbriquées.|  
|**Hidden**|La colonne n'est pas écrite dans la sortie XML.|  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [Imbrication de DataRelations](nesting-datarelations.md)
- [Écriture des informations de schéma de DataSet comme XSD](writing-dataset-schema-information-as-xsd.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
