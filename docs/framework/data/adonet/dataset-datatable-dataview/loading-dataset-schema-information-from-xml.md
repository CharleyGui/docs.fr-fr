---
title: Chargement des informations de schéma de DataSet à partir de XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 69994c546fea842ffef1c8c43d6d6f5bc35e0629
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151050"
---
# <a name="loading-dataset-schema-information-from-xml"></a>Chargement des informations de schéma de DataSet à partir de XML
Le schéma <xref:System.Data.DataSet> d’un (ses tableaux, colonnes, relations et contraintes) peut être défini programmatiquement, créé par les méthodes **Fill** ou **FillSchema** d’un <xref:System.Data.Common.DataAdapter>document, ou chargé à partir d’un document XML. Pour charger les informations de schéma **DataSet** à partir d’un document XML, vous pouvez utiliser soit le **ReadXmlSchema** ou la méthode **InferXmlSchema** du **DataSet**. **ReadXmlSchema** vous permet de charger ou d’inférer les informations sur les schémas **DataSet** à partir du document contenant le schéma de définition XML Schema (XSD), ou un document XML avec inline XML Schema. **InferXmlSchema** vous permet d’inférer le schéma du document XML tout en ignorant certains espaces de noms XML que vous spécifiez.  
  
> [!NOTE]
> La commande de table dans un **ensemble de données** peut ne pas être préservée lorsque vous utilisez les services Web ou la sérialisation XML pour transférer un ensemble de **données** qui a été créé en mémoire en utilisant des constructions XSD (telles que les relations imbriquées). Par conséquent, le destinataire du **DataSet** ne devrait pas dépendre de la commande de table dans ce cas. Cependant, la commande de table est toujours préservée si le schéma du **DataSet** transféré a été lu à partir de fichiers XSD, au lieu d’être créé en mémoire.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Pour charger le schéma d’un **DataSet** à partir d’un document XML sans charger de données, vous pouvez utiliser la méthode **ReadXmlSchema** du **DataSet**. **ReadXmlSchema** crée le schéma **DataSet** défini à l’aide du schéma de définition XML Schema (XSD).  
  
 La méthode **ReadXmlSchema** prend un seul argument d’un nom de fichier, d’un flux ou d’un **XmlReader** contenant le document XML à charger. Le document XML peut contenir uniquement le schéma ou contenir le schéma inline avec des éléments XML contenant des données. Pour plus de détails sur l’écriture schéma inline comme XML Schema, voir [Deriving DataSet Relational Structure de XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Si le document XML transmis à **ReadXmlSchema** ne contient aucune information sur les schémas inlines, **ReadXmlSchema** inférera le schéma des éléments du document XML. Si le **DataSet** contient déjà un schéma, le schéma actuel sera prolongé en ajoutant de nouvelles tables si elles n’existent pas déjà. De nouvelles colonnes ne seront pas ajoutées aux tables existantes. Si une colonne ajoutée existe déjà dans le **DataSet** mais a un type incompatible avec la colonne trouvée dans le XML, une exception est lancée. Pour plus de détails sur la façon dont **ReadXmlSchema** déduit un schéma d’un document XML, voir [Inferring DataSet Relational Structure de XML](inferring-dataset-relational-structure-from-xml.md).  
  
 Bien que **ReadXmlSchema** charge ou déduit seulement le schéma d’un **DataSet**, la méthode **ReadXml** des charges **de DataSet** ou déduit à la fois le schéma et les données contenues dans le document XML. Pour plus d’informations, voir [Chargement d’un ensemble de données de XML](loading-a-dataset-from-xml.md).  
  
 Les exemples de code suivants montrent comment charger un schéma **DataSet** à partir d’un document ou d’un flux XML. Le premier exemple montre un nom de fichier XML Schema transmis à la méthode **ReadXmlSchema.** Le deuxième exemple montre un **System.IO.StreamReader**.  
  
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
 Vous pouvez également demander au **DataSet** d’inférer son schéma à partir d’un document XML à l’aide de la méthode **InferXmlSchema** du **DataSet**. **InferXmlSchema** fonctionne de la même façon que **le readXml** avec un **XmlReadMode** d’InferSchema (charges données ainsi que le schéma infers), et **ReadXmlSchema** si le document lu ne contient aucun schéma en ligne. **InferSchema** Cependant, **InferXmlSchema** fournit la capacité supplémentaire de vous permettre de spécifier des espaces de noms XML particuliers à ignorer lorsque le schéma est déduit. **InferXmlSchema** prend deux arguments requis : l’emplacement du document XML, spécifié par un nom de fichier, un flux ou un **XmlReader**; et un tableau de chaînes d’espaces de noms XML à ignorer par l’opération.  
  
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
  
 En raison des attributs spécifiés pour les éléments du document XML précédent, à la fois la méthode **ReadXmlSchema** et la méthode **ReadXmlml** avec un **XmlReadMode** d’InferSchema créerait des tables pour chaque élément dans le document: **Catégories**, **CategoryID**, **CategoryName**, **Description**, **Produits**, **ProductID**, **ReorderLevel**, et **Discontinued**. **InferSchema** (Pour plus d’informations, voir [Inferring DataSet Relational Structure de XML](inferring-dataset-relational-structure-from-xml.md).) Cependant, une structure plus appropriée serait de créer uniquement les tableaux **catégories** et **produits,** puis de créer **CatégorieID**, **CategoryName**, et **description** des colonnes dans le tableau **catégories,** et **ProductID**, **ReorderLevel**, et les colonnes **abandonnées** dans le tableau **produits.** Pour vous assurer que le schéma déduit ignore les attributs spécifiés dans les éléments XML, utilisez la méthode **InferXmlSchema** et spécifiez l’espace de nom XML pour **les données de bureau** à ignorer, comme le montre l’exemple suivant.  
  
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
