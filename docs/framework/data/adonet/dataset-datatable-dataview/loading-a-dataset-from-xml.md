---
title: Chargement d'un DataSet à partir de XML
description: Découvrez comment ajouter du contenu à un jeu de données ADO.NET à partir de XML. Le .NET Framework offre la flexibilité nécessaire au chargement et à la structure du jeu de données.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 8c81e6e29678fe2e30af7c15d8d6e90f23dd0762
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286881"
---
# <a name="loading-a-dataset-from-xml"></a>Chargement d'un DataSet à partir de XML
Le contenu d'un objet <xref:System.Data.DataSet> ADO.NET peut être recréé à partir d'un flux ou d'un document XML. En outre, le .NET Framework vous offre une grande souplesse en ce qui concerne les informations qui seront chargées à partir de XML et le mode de création du schéma ou de la structure relationnelle de l'objet <xref:System.Data.DataSet>.  
  
 Pour remplir un <xref:System.Data.DataSet> avec des données de XML, utilisez la méthode **ReadXml** de l' <xref:System.Data.DataSet> objet. La méthode **ReadXml** lit à partir d’un fichier, d’un flux ou d’un **XmlReader**et prend comme arguments la source du code XML plus un argument **XmlReadMode** facultatif. Pour plus d’informations sur **XmlReader**, consultez [lecture de données XML avec XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)). La méthode **ReadXml** lit le contenu du flux ou du document XML et charge le <xref:System.Data.DataSet> avec des données. Elle crée également le schéma relationnel de <xref:System.Data.DataSet> en fonction du **XmlReadMode** spécifié et de la présence ou non d’un schéma relationnel.  
  
 Le tableau suivant décrit les options de l’argument **XmlReadMode** .  
  
|Option|Description|  
|------------|-----------------|  
|**Auto**|Il s'agit de la valeur par défaut. Examine le XML et choisit l'option la mieux appropriée, dans l'ordre suivant :<br /><br /> -Si le XML est un DiffGram, **DiffGram** est utilisé.<br />-Si <xref:System.Data.DataSet> contient un schéma ou si le code XML contient un schéma Inline, **ReadSchema** est utilisé.<br />-Si <xref:System.Data.DataSet> ne contient pas de schéma et que le XML ne contient pas de schéma Inline, **InferSchema** est utilisé.<br /><br /> Si vous connaissez le format du code XML lu, il est recommandé, pour des performances optimales, de définir un **XmlReadMode**explicite, plutôt que d’accepter la valeur par défaut **automatique** .|  
|**ReadSchema**|Lit les schémas inline et charge les données et les schémas.<br /><br /> Si l'objet <xref:System.Data.DataSet> contient déjà un schéma, les nouvelles tables sont ajoutées du schéma inline au schéma existant dans l'objet <xref:System.Data.DataSet>. Si des tables du schéma inline existent déjà dans l'objet <xref:System.Data.DataSet>, une exception est levée. Vous ne pouvez pas modifier le schéma d’une table existante à l’aide de **XmlReadMode. ReadSchema**.<br /><br /> Si l'objet <xref:System.Data.DataSet> ne contient pas de schéma et qu'il n'existe pas de schéma inline, les données ne sont pas lues.<br /><br /> Un schéma inline peut être défini à l'aide d'un schéma en langage XSD (XML Schema Definition). Pour plus d’informations sur l’écriture d’un schéma Inline en tant que schéma XML, consultez [dérivation de la structure relationnelle d’un DataSet à partir d’un schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignore les schémas inline et charge les données dans le schéma existant de l'objet <xref:System.Data.DataSet>. Toute donnée ne correspondant pas au schéma existant est ignorée. S'il n'existe pas de schéma dans l'objet <xref:System.Data.DataSet>, aucune donnée n'est chargée.<br /><br /> Si les données sont un DiffGram, **IgnoreSchema** a les mêmes fonctionnalités que **DiffGram** *.*|  
|**InferSchema**|Ignore tout schéma inline et déduit le schéma de la structure des données XML, puis charge les données.<br /><br /> Si le <xref:System.Data.DataSet> contient déjà un schéma, le schéma en cours est étendu par l'ajout de colonnes dans les tables existantes. Des tables supplémentaires ne seront pas ajoutées s'il n'existe pas de tables. Une exception est levée si une table déduite existe déjà avec un autre espace de noms, ou en cas de conflit entre des colonnes inférées et des colonnes existantes.<br /><br /> Pour plus d’informations sur la façon dont **ReadXmlSchema** déduit un schéma à partir d’un document XML, consultez [déduction de la structure relationnelle d’un jeu de données à partir de XML](inferring-dataset-relational-structure-from-xml.md).|  
|**DiffGram**|Lit un DiffGram et ajoute les données au schéma en cours. **DiffGram** fusionne les nouvelles lignes avec les lignes existantes où les valeurs d’identificateur uniques correspondent. Voir « Fusion de données provenant de XML » à la fin de cette rubrique. Pour plus d’informations sur les DiffGrams, consultez [DiffGrams](diffgrams.md).|  
|**Fragment**|Poursuit la lecture de plusieurs fragments XML jusqu'à ce que la fin du flux soit atteinte. Les fragments qui correspondent au schéma de l'objet <xref:System.Data.DataSet> sont ajoutés aux tables appropriées. Les fragments qui ne correspondent pas au schéma <xref:System.Data.DataSet> sont écartés.|  
  
> [!NOTE]
> Si vous transmettez un **XmlReader** à **ReadXml** qui est positionné dans un document XML, **ReadXml** lit le nœud d’élément suivant et le traite comme l’élément racine, en lisant jusqu’à la fin du nœud d’élément uniquement. Cela ne s’applique pas si vous spécifiez **XmlReadMode. fragment**.  
  
## <a name="dtd-entities"></a>Entités DTD  
 Si votre XML contient des entités définies dans un schéma de définition de type de document (DTD), une exception est levée si vous tentez de charger un <xref:System.Data.DataSet> en passant un nom de fichier, un flux ou un **XmlReader** non validant à **ReadXml**. Au lieu de cela, vous devez créer un **XmlValidatingReader**, avec **EntityHandling** défini sur **EntityHandling. ExpandEntities**, et passer votre **XmlValidatingReader** à **ReadXml**. Le **XmlValidatingReader** développera les entités avant la lecture par <xref:System.Data.DataSet> .  
  
 Les exemples de code suivants montrent comment charger un objet <xref:System.Data.DataSet> à partir d'un flux XML. Le premier exemple montre un nom de fichier passé à la méthode **ReadXml** . Le second illustre le cas d'une chaîne contenant le XML chargé à l'aide d'un objet <xref:System.IO.StringReader>.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
> Si vous appelez **ReadXml** pour charger un fichier très volumineux, vous risquez de rencontrer des problèmes de performances. Pour garantir des performances optimales pour **ReadXml**, sur un fichier volumineux, appelez la <xref:System.Data.DataTable.BeginLoadData%2A> méthode pour chaque table dans le <xref:System.Data.DataSet> , puis appelez **ReadXml**. Enfin, appelez <xref:System.Data.DataTable.EndLoadData%2A> pour chaque table de l'objet <xref:System.Data.DataSet>, comme le montre l'exemple suivant.  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
> Si le schéma XSD de votre <xref:System.Data.DataSet> inclut un **targetNamespace**, il est possible que les données ne soient pas lues et que vous rencontriez des exceptions lors de l’appel de **ReadXml** pour charger l' <xref:System.Data.DataSet> élément with XML qui contient des éléments sans espace de noms éligible. Pour lire des éléments non qualifiés dans ce cas, affectez à **elementFormDefault** la valeur « qualified » dans votre schéma XSD. Par exemple :  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>Fusion de données provenant de XML  
 Si l'objet <xref:System.Data.DataSet> contient déjà des données, les nouvelles données provenant de XML sont ajoutées aux données déjà présentes dans l'objet <xref:System.Data.DataSet>. **ReadXml** ne fusionne pas le XML avec les <xref:System.Data.DataSet> informations de ligne avec les clés primaires correspondantes. Pour remplacer les informations de ligne existantes par de nouvelles informations à partir de XML, utilisez **ReadXml** pour créer un nouveau <xref:System.Data.DataSet> , puis <xref:System.Data.DataSet.Merge%2A> le nouveau <xref:System.Data.DataSet> dans le existant <xref:System.Data.DataSet> . Notez que le chargement d’un DiffGram à l’aide de **ReadXml** avec un **XmlReadMode** de **DiffGram** fusionne les lignes qui ont le même identificateur unique.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Déduction de la structure relationnelle des DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md)
- [Chargement des informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
