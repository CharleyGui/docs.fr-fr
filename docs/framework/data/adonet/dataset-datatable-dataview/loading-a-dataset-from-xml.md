---
title: Chargement d'un DataSet à partir de XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151063"
---
# <a name="loading-a-dataset-from-xml"></a>Chargement d'un DataSet à partir de XML
Le contenu d'un objet <xref:System.Data.DataSet> ADO.NET peut être recréé à partir d'un flux ou d'un document XML. En outre, le .NET Framework vous offre une grande souplesse en ce qui concerne les informations qui seront chargées à partir de XML et le mode de création du schéma ou de la structure relationnelle de l'objet <xref:System.Data.DataSet>.  
  
 Pour remplir <xref:System.Data.DataSet> un avec des données de XML, <xref:System.Data.DataSet> utilisez la méthode **ReadXml** de l’objet. La méthode **ReadXml** se lit à partir d’un fichier, un flux, ou un **XmlReader**, et prend comme arguments la source de la XML plus un argument **optionnel XmlReadMode.** Pour plus d’informations sur le **XmlReader**, voir [Lecture XML Données avec XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)). La méthode **ReadXml** lit le contenu du flux ou <xref:System.Data.DataSet> du document XML et charge les données. Il créera également le schéma <xref:System.Data.DataSet> relationnel de la selon le **XmlReadMode** spécifié et si oui ou non un schéma relationnel existe déjà.  
  
 Le tableau suivant décrit les options pour l’argument **XmlReadMode.**  
  
|Option|Description|  
|------------|-----------------|  
|**Automatique**|Il s’agit de la valeur par défaut. Examine le XML et choisit l'option la mieux appropriée, dans l'ordre suivant :<br /><br /> - Si le XML est un DiffGram, **DiffGram** est utilisé.<br />- Si <xref:System.Data.DataSet> le contient un schéma ou le XML contient un schéma inline, **ReadSchema** est utilisé.<br />- Si <xref:System.Data.DataSet> le ne contient pas un schéma et le XML ne contient pas un schéma inline, **InferSchema** est utilisé.<br /><br /> Si vous connaissez le format de la XML en cours de lecture, pour la meilleure performance, il est recommandé que vous définissez un **XmlReadMode**explicite , plutôt que d’accepter le défaut **Auto.**|  
|**ReadSchema**|Lit les schémas inline et charge les données et les schémas.<br /><br /> Si l'objet <xref:System.Data.DataSet> contient déjà un schéma, les nouvelles tables sont ajoutées du schéma inline au schéma existant dans l'objet <xref:System.Data.DataSet>. Si des tables du schéma inline existent déjà dans l'objet <xref:System.Data.DataSet>, une exception est levée. Vous ne serez pas en mesure de modifier le schéma d’une table existante à l’aide de **XmlReadMode.ReadSchema**.<br /><br /> Si l'objet <xref:System.Data.DataSet> ne contient pas de schéma et qu'il n'existe pas de schéma inline, les données ne sont pas lues.<br /><br /> Un schéma inline peut être défini à l'aide d'un schéma en langage XSD (XML Schema Definition). Pour plus de détails sur l’écriture schéma inline comme XML Schema, voir [Deriving DataSet Relational Structure de XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignore les schémas inline et charge les données dans le schéma existant de l'objet <xref:System.Data.DataSet>. Toute donnée ne correspondant pas au schéma existant est ignorée. S'il n'existe pas de schéma dans l'objet <xref:System.Data.DataSet>, aucune donnée n'est chargée.<br /><br /> Si les données sont un DiffGram, **IgnoreSchema** a la même fonctionnalité que **DiffGram** *.*|  
|**InferSchema**|Ignore tout schéma inline et déduit le schéma de la structure des données XML, puis charge les données.<br /><br /> Si le <xref:System.Data.DataSet> contient déjà un schéma, le schéma en cours est étendu par l'ajout de colonnes dans les tables existantes. Des tables supplémentaires ne seront pas ajoutées s'il n'existe pas de tables. Une exception est levée si une table déduite existe déjà avec un autre espace de noms, ou en cas de conflit entre des colonnes inférées et des colonnes existantes.<br /><br /> Pour plus de détails sur la façon dont **ReadXmlSchema** déduit un schéma d’un document XML, voir [Inferring DataSet Relational Structure de XML](inferring-dataset-relational-structure-from-xml.md).|  
|**Diffgram**|Lit un DiffGram et ajoute les données au schéma en cours. **DiffGram** fusionne de nouvelles lignes avec des lignes existantes où les valeurs d’identification uniques correspondent. Voir « Fusion de données provenant de XML » à la fin de cette rubrique. Pour plus d’informations sur DiffGrams, voir [DiffGrams](diffgrams.md).|  
|**Fragment**|Poursuit la lecture de plusieurs fragments XML jusqu'à ce que la fin du flux soit atteinte. Les fragments qui correspondent au schéma de l'objet <xref:System.Data.DataSet> sont ajoutés aux tables appropriées. Les fragments qui ne correspondent pas au schéma <xref:System.Data.DataSet> sont écartés.|  
  
> [!NOTE]
> Si vous passez un **XmlReader** à **ReadXml** qui est positionné une partie du chemin dans un document XML, **ReadXml** sera lu au nœud élément suivant et traitera que comme l’élément racine, la lecture jusqu’à la fin du nœud élément seulement. Cela ne s’applique pas si vous spécifiez **XmlReadMode.Fragment**.  
  
## <a name="dtd-entities"></a>Entités DTD  
 Si votre XML contient des entités définies dans un schéma de définition de type document <xref:System.Data.DataSet> (DTD), une exception sera lancée si vous tentez de charger un en passant un nom de fichier, un flux ou une **XmlReader** non validant à **ReadXml**. Au lieu de cela, vous devez créer un **XmlValidatingReader**, avec **EntityHandling** ensemble à **EntityHandling.ExpandEntities**, et passer votre **XmlValidatingReader** à **ReadXml**. Le **XmlValidatingReader** élargira les entités avant <xref:System.Data.DataSet>d’être lu par le .  
  
 Les exemples de code suivants montrent comment charger un objet <xref:System.Data.DataSet> à partir d'un flux XML. Le premier exemple montre un nom de fichier transmis à la méthode **ReadXml.** Le second illustre le cas d'une chaîne contenant le XML chargé à l'aide d'un objet <xref:System.IO.StringReader>.  
  
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
> Si vous appelez **ReadXml** pour charger un fichier très volumineux, vous pouvez rencontrer des performances lentes. Pour assurer les meilleures performances pour **ReadXml** <xref:System.Data.DataTable.BeginLoadData%2A> , sur un <xref:System.Data.DataSet>grand fichier, appelez la méthode pour chaque table dans le , puis appelez **ReadXml**. Enfin, appelez <xref:System.Data.DataTable.EndLoadData%2A> pour chaque table de l'objet <xref:System.Data.DataSet>, comme le montre l'exemple suivant.  
  
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
> Si le schéma XSD <xref:System.Data.DataSet> pour votre inclut un **targetNamespace**, les données peuvent ne pas être <xref:System.Data.DataSet> lues, et vous pouvez rencontrer des exceptions, lorsque vous appelez **ReadXml** pour charger le XML qui contient des éléments sans namespace de qualification. Pour lire des éléments non qualifiés dans ce cas, définissez **l’élémentFormDefault** égal à "qualifié" dans votre schéma XSD. Par exemple :  
  
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
 Si l'objet <xref:System.Data.DataSet> contient déjà des données, les nouvelles données provenant de XML sont ajoutées aux données déjà présentes dans l'objet <xref:System.Data.DataSet>. **ReadXml** ne fusionne pas de <xref:System.Data.DataSet> la XML dans les informations de ligne avec des touches primaires correspondantes. Pour remplacer les informations existantes en ligne avec de nouvelles informations <xref:System.Data.DataSet>de <xref:System.Data.DataSet.Merge%2A> XML, utilisez <xref:System.Data.DataSet> **ReadXml** pour créer un nouveau , puis le nouveau <xref:System.Data.DataSet> dans l’existant . Notez que le chargement d’un DiffGram à l’aide de **ReadXML** avec un **XmlReadMode** de **DiffGram** fusionnera les lignes qui ont le même identifiant unique.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Déduction de la structure relationnelle des DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md)
- [Chargement des informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
