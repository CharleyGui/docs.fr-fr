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
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="023d8-102">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="023d8-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="023d8-103">Le schéma <xref:System.Data.DataSet> d’un (ses tableaux, colonnes, relations et contraintes) peut être défini programmatiquement, créé par les méthodes **Fill** ou **FillSchema** d’un <xref:System.Data.Common.DataAdapter>document, ou chargé à partir d’un document XML.</span><span class="sxs-lookup"><span data-stu-id="023d8-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="023d8-104">Pour charger les informations de schéma **DataSet** à partir d’un document XML, vous pouvez utiliser soit le **ReadXmlSchema** ou la méthode **InferXmlSchema** du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="023d8-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="023d8-105">**ReadXmlSchema** vous permet de charger ou d’inférer les informations sur les schémas **DataSet** à partir du document contenant le schéma de définition XML Schema (XSD), ou un document XML avec inline XML Schema.</span><span class="sxs-lookup"><span data-stu-id="023d8-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="023d8-106">**InferXmlSchema** vous permet d’inférer le schéma du document XML tout en ignorant certains espaces de noms XML que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="023d8-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="023d8-107">La commande de table dans un **ensemble de données** peut ne pas être préservée lorsque vous utilisez les services Web ou la sérialisation XML pour transférer un ensemble de **données** qui a été créé en mémoire en utilisant des constructions XSD (telles que les relations imbriquées).</span><span class="sxs-lookup"><span data-stu-id="023d8-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="023d8-108">Par conséquent, le destinataire du **DataSet** ne devrait pas dépendre de la commande de table dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="023d8-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="023d8-109">Cependant, la commande de table est toujours préservée si le schéma du **DataSet** transféré a été lu à partir de fichiers XSD, au lieu d’être créé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="023d8-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="023d8-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="023d8-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="023d8-111">Pour charger le schéma d’un **DataSet** à partir d’un document XML sans charger de données, vous pouvez utiliser la méthode **ReadXmlSchema** du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="023d8-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="023d8-112">**ReadXmlSchema** crée le schéma **DataSet** défini à l’aide du schéma de définition XML Schema (XSD).</span><span class="sxs-lookup"><span data-stu-id="023d8-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="023d8-113">La méthode **ReadXmlSchema** prend un seul argument d’un nom de fichier, d’un flux ou d’un **XmlReader** contenant le document XML à charger.</span><span class="sxs-lookup"><span data-stu-id="023d8-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="023d8-114">Le document XML peut contenir uniquement le schéma ou contenir le schéma inline avec des éléments XML contenant des données.</span><span class="sxs-lookup"><span data-stu-id="023d8-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="023d8-115">Pour plus de détails sur l’écriture schéma inline comme XML Schema, voir [Deriving DataSet Relational Structure de XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="023d8-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="023d8-116">Si le document XML transmis à **ReadXmlSchema** ne contient aucune information sur les schémas inlines, **ReadXmlSchema** inférera le schéma des éléments du document XML.</span><span class="sxs-lookup"><span data-stu-id="023d8-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="023d8-117">Si le **DataSet** contient déjà un schéma, le schéma actuel sera prolongé en ajoutant de nouvelles tables si elles n’existent pas déjà.</span><span class="sxs-lookup"><span data-stu-id="023d8-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="023d8-118">De nouvelles colonnes ne seront pas ajoutées aux tables existantes.</span><span class="sxs-lookup"><span data-stu-id="023d8-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="023d8-119">Si une colonne ajoutée existe déjà dans le **DataSet** mais a un type incompatible avec la colonne trouvée dans le XML, une exception est lancée.</span><span class="sxs-lookup"><span data-stu-id="023d8-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="023d8-120">Pour plus de détails sur la façon dont **ReadXmlSchema** déduit un schéma d’un document XML, voir [Inferring DataSet Relational Structure de XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="023d8-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="023d8-121">Bien que **ReadXmlSchema** charge ou déduit seulement le schéma d’un **DataSet**, la méthode **ReadXml** des charges **de DataSet** ou déduit à la fois le schéma et les données contenues dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="023d8-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="023d8-122">Pour plus d’informations, voir [Chargement d’un ensemble de données de XML](loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="023d8-122">For more information, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="023d8-123">Les exemples de code suivants montrent comment charger un schéma **DataSet** à partir d’un document ou d’un flux XML.</span><span class="sxs-lookup"><span data-stu-id="023d8-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="023d8-124">Le premier exemple montre un nom de fichier XML Schema transmis à la méthode **ReadXmlSchema.**</span><span class="sxs-lookup"><span data-stu-id="023d8-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="023d8-125">Le deuxième exemple montre un **System.IO.StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="023d8-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="023d8-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="023d8-126">InferXmlSchema</span></span>  
 <span data-ttu-id="023d8-127">Vous pouvez également demander au **DataSet** d’inférer son schéma à partir d’un document XML à l’aide de la méthode **InferXmlSchema** du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="023d8-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="023d8-128">**InferXmlSchema** fonctionne de la même façon que **le readXml** avec un **XmlReadMode** d’InferSchema (charges données ainsi que le schéma infers), et **ReadXmlSchema** si le document lu ne contient aucun schéma en ligne. **InferSchema**</span><span class="sxs-lookup"><span data-stu-id="023d8-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="023d8-129">Cependant, **InferXmlSchema** fournit la capacité supplémentaire de vous permettre de spécifier des espaces de noms XML particuliers à ignorer lorsque le schéma est déduit.</span><span class="sxs-lookup"><span data-stu-id="023d8-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="023d8-130">**InferXmlSchema** prend deux arguments requis : l’emplacement du document XML, spécifié par un nom de fichier, un flux ou un **XmlReader**; et un tableau de chaînes d’espaces de noms XML à ignorer par l’opération.</span><span class="sxs-lookup"><span data-stu-id="023d8-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="023d8-131">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="023d8-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="023d8-132">En raison des attributs spécifiés pour les éléments du document XML précédent, à la fois la méthode **ReadXmlSchema** et la méthode **ReadXmlml** avec un **XmlReadMode** d’InferSchema créerait des tables pour chaque élément dans le document: **Catégories**, **CategoryID**, **CategoryName**, **Description**, **Produits**, **ProductID**, **ReorderLevel**, et **Discontinued**. **InferSchema**</span><span class="sxs-lookup"><span data-stu-id="023d8-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="023d8-133">(Pour plus d’informations, voir [Inferring DataSet Relational Structure de XML](inferring-dataset-relational-structure-from-xml.md).) Cependant, une structure plus appropriée serait de créer uniquement les tableaux **catégories** et **produits,** puis de créer **CatégorieID**, **CategoryName**, et **description** des colonnes dans le tableau **catégories,** et **ProductID**, **ReorderLevel**, et les colonnes **abandonnées** dans le tableau **produits.**</span><span class="sxs-lookup"><span data-stu-id="023d8-133">(For more information, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="023d8-134">Pour vous assurer que le schéma déduit ignore les attributs spécifiés dans les éléments XML, utilisez la méthode **InferXmlSchema** et spécifiez l’espace de nom XML pour **les données de bureau** à ignorer, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="023d8-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="023d8-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="023d8-135">See also</span></span>

- [<span data-ttu-id="023d8-136">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="023d8-136">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="023d8-137">Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="023d8-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="023d8-138">Déduction de la structure relationnelle des DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="023d8-138">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="023d8-139">Chargement d'un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="023d8-139">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="023d8-140">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="023d8-140">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="023d8-141">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="023d8-141">ADO.NET Overview</span></span>](../ado-net-overview.md)
