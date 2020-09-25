---
title: Chargement des informations de schéma de DataSet à partir de XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: b084590d7158024227a9f12da759b56ae2031373
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201341"
---
# <a name="loading-dataset-schema-information-from-xml"></a>Chargement des informations de schéma de DataSet à partir de XML

Le schéma d’un <xref:System.Data.DataSet> (ses tables, colonnes, relations et contraintes) peut être défini par programme, créé par les méthodes **Fill** ou **FillSchema** d’un <xref:System.Data.Common.DataAdapter> ou chargé à partir d’un document XML. Pour charger les informations de schéma d’un **DataSet** à partir d’un document XML, vous pouvez utiliser la méthode **ReadXmlSchema** ou **InferXmlSchema** du **DataSet**. **ReadXmlSchema** vous permet de charger ou de déduire des informations de schéma de **DataSet** à partir du document contenant le schéma en langage XSD (XML Schema Definition) ou d’un document XML avec un schéma XML inline. **InferXmlSchema** vous permet de déduire le schéma à partir du document XML tout en ignorant certains espaces de noms XML que vous spécifiez.  
  
> [!NOTE]
> L’ordre des tables dans un **DataSet** peut ne pas être préservé quand vous utilisez des services Web ou la sérialisation XML pour transférer un **DataSet** qui a été créé en mémoire à l’aide de constructions XSD (telles que les relations imbriquées). Par conséquent, le destinataire du **DataSet** ne doit pas dépendre de l’ordre des tables dans ce cas. Toutefois, l’ordre des tables est toujours préservé si le schéma du **jeu de données** transféré a été lu à partir de fichiers XSD, au lieu d’être créé en mémoire.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  

 Pour charger le schéma d’un **DataSet** à partir d’un document XML sans charger de données, vous pouvez utiliser la méthode **ReadXmlSchema** du **DataSet**. **ReadXmlSchema** crée un schéma de **DataSet** défini à l’aide du schéma en langage XSD (XML Schema Definition).  
  
 La méthode **ReadXmlSchema** accepte un seul argument d’un nom de fichier, un flux ou un **XmlReader** contenant le document XML à charger. Le document XML peut contenir uniquement le schéma ou contenir le schéma inline avec des éléments XML contenant des données. Pour plus d’informations sur l’écriture d’un schéma Inline en tant que schéma XML, consultez [dérivation de la structure relationnelle d’un DataSet à partir d’un schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Si le document XML passé à **ReadXmlSchema** ne contient aucune information de schéma Inline, **ReadXmlSchema** déduira le schéma à partir des éléments du document XML. Si le **jeu de données** contient déjà un schéma, le schéma actuel est étendu par l’ajout de nouvelles tables s’ils n’existent pas déjà. De nouvelles colonnes ne seront pas ajoutées aux tables existantes. Si une colonne ajoutée existe déjà dans le **DataSet** mais possède un type incompatible avec la colonne trouvée dans le XML, une exception est levée. Pour plus d’informations sur la façon dont **ReadXmlSchema** déduit un schéma à partir d’un document XML, consultez [déduction de la structure relationnelle d’un jeu de données à partir de XML](inferring-dataset-relational-structure-from-xml.md).  
  
 Bien que **ReadXmlSchema** charge ou déduit uniquement le schéma d’un **DataSet**, la méthode **ReadXml** du **DataSet** charge ou déduit le schéma et les données contenues dans le document XML. Pour plus d’informations, consultez [chargement d’un DataSet à partir de XML](loading-a-dataset-from-xml.md).  
  
 Les exemples de code suivants montrent comment charger un schéma de **DataSet** à partir d’un document ou d’un flux XML. Le premier exemple montre un nom de fichier de schéma XML passé à la méthode **ReadXmlSchema** . Le deuxième exemple montre un **System. IO. StreamReader**.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a>InferXmlSchema  

 Vous pouvez également demander au **DataSet** de déduire son schéma à partir d’un document XML à l’aide de la méthode **InferXmlSchema** du **DataSet**. **InferXmlSchema** fonctionne de la même façon que **ReadXml** avec un **XmlReadMode** de **InferSchema** (charge des données et déduit le schéma), et **ReadXmlSchema** si le document en cours de lecture ne contient pas de schéma Inline. Toutefois, **InferXmlSchema** offre la possibilité supplémentaire de vous permettre de spécifier des espaces de noms XML particuliers à ignorer lorsque le schéma est déduit. **InferXmlSchema** prend deux arguments requis : l’emplacement du document XML, spécifié par un nom de fichier, un flux ou un **XmlReader**; et un tableau de chaînes d’espaces de noms XML qui doivent être ignorés par l’opération.  
  
 Examinons, par exemple, le code XML suivant :  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>
  <Description od:adotype="203">Soft drinks and teas</Description>
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>
  <ReorderLevel od:adotype="3">10</ReorderLevel>
  <Discontinued od:adotype="11">0</Discontinued>
</Products>  
</NewDataSet>  
```  
  
 En raison des attributs spécifiés pour les éléments du document XML précédent, la méthode **ReadXmlSchema** et la méthode **ReadXml** avec un **XmlReadMode** de **InferSchema** créent des tables pour chaque élément du document : **categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**et **Discontinued**. (Pour plus d’informations, consultez [déduction de la structure relationnelle d’un DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md).) Toutefois, une structure plus appropriée consiste à créer uniquement les tables **categories** et **Products** , puis à créer les colonnes **CategoryID**, **CategoryName**et **Description** dans la table **categories** , et les colonnes **ProductID**, **ReorderLevel**et **Discontinued** dans la table **Products** . Pour vous assurer que le schéma inféré ignore les attributs spécifiés dans les éléments XML, utilisez la méthode **InferXmlSchema** et spécifiez que l’espace de noms XML de **officedata** doit être ignoré, comme illustré dans l’exemple suivant.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Déduction de la structure relationnelle des DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md)
- [Chargement d'un DataSet à partir de XML](loading-a-dataset-from-xml.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
