---
title: Chargement d'un DataSet à partir de XML
description: Découvrez comment ajouter du contenu à un jeu de données ADO.NET à partir de XML. Le .NET Framework offre la flexibilité nécessaire au chargement et à la structure du jeu de données.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 0920acac2c82677cfce37703b7027dedce91a535
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166805"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="ae331-104">Chargement d'un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="ae331-104">Loading a DataSet from XML</span></span>

<span data-ttu-id="ae331-105">Le contenu d'un objet <xref:System.Data.DataSet> ADO.NET peut être recréé à partir d'un flux ou d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="ae331-105">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="ae331-106">En outre, le .NET Framework vous offre une grande souplesse en ce qui concerne les informations qui seront chargées à partir de XML et le mode de création du schéma ou de la structure relationnelle de l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ae331-106">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="ae331-107">Pour remplir un <xref:System.Data.DataSet> avec des données de XML, utilisez la méthode **ReadXml** de l' <xref:System.Data.DataSet> objet.</span><span class="sxs-lookup"><span data-stu-id="ae331-107">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="ae331-108">La méthode **ReadXml** lit à partir d’un fichier, d’un flux ou d’un **XmlReader**et prend comme arguments la source du code XML plus un argument **XmlReadMode** facultatif.</span><span class="sxs-lookup"><span data-stu-id="ae331-108">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="ae331-109">Pour plus d’informations sur **XmlReader**, consultez [lecture de données XML avec XmlTextReader](/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ae331-109">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="ae331-110">La méthode **ReadXml** lit le contenu du flux ou du document XML et charge le <xref:System.Data.DataSet> avec des données.</span><span class="sxs-lookup"><span data-stu-id="ae331-110">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="ae331-111">Elle crée également le schéma relationnel de <xref:System.Data.DataSet> en fonction du **XmlReadMode** spécifié et de la présence ou non d’un schéma relationnel.</span><span class="sxs-lookup"><span data-stu-id="ae331-111">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="ae331-112">Le tableau suivant décrit les options de l’argument **XmlReadMode** .</span><span class="sxs-lookup"><span data-stu-id="ae331-112">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="ae331-113">Option</span><span class="sxs-lookup"><span data-stu-id="ae331-113">Option</span></span>|<span data-ttu-id="ae331-114">Description</span><span class="sxs-lookup"><span data-stu-id="ae331-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ae331-115">**Automatique**</span><span class="sxs-lookup"><span data-stu-id="ae331-115">**Auto**</span></span>|<span data-ttu-id="ae331-116">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="ae331-116">This is the default.</span></span> <span data-ttu-id="ae331-117">Examine le XML et choisit l'option la mieux appropriée, dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="ae331-117">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="ae331-118">-Si le XML est un DiffGram, **DiffGram** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ae331-118">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="ae331-119">-Si <xref:System.Data.DataSet> contient un schéma ou si le code XML contient un schéma Inline, **ReadSchema** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ae331-119">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="ae331-120">-Si <xref:System.Data.DataSet> ne contient pas de schéma et que le XML ne contient pas de schéma Inline, **InferSchema** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ae331-120">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="ae331-121">Si vous connaissez le format du code XML lu, il est recommandé, pour des performances optimales, de définir un **XmlReadMode**explicite, plutôt que d’accepter la valeur par défaut **automatique** .</span><span class="sxs-lookup"><span data-stu-id="ae331-121">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="ae331-122">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="ae331-122">**ReadSchema**</span></span>|<span data-ttu-id="ae331-123">Lit les schémas inline et charge les données et les schémas.</span><span class="sxs-lookup"><span data-stu-id="ae331-123">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="ae331-124">Si l'objet <xref:System.Data.DataSet> contient déjà un schéma, les nouvelles tables sont ajoutées du schéma inline au schéma existant dans l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ae331-124">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ae331-125">Si des tables du schéma inline existent déjà dans l'objet <xref:System.Data.DataSet>, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="ae331-125">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="ae331-126">Vous ne pouvez pas modifier le schéma d’une table existante à l’aide de **XmlReadMode. ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="ae331-126">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="ae331-127">Si l'objet <xref:System.Data.DataSet> ne contient pas de schéma et qu'il n'existe pas de schéma inline, les données ne sont pas lues.</span><span class="sxs-lookup"><span data-stu-id="ae331-127">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="ae331-128">Un schéma inline peut être défini à l'aide d'un schéma en langage XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="ae331-128">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="ae331-129">Pour plus d’informations sur l’écriture d’un schéma Inline en tant que schéma XML, consultez [dérivation de la structure relationnelle d’un DataSet à partir d’un schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="ae331-129">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="ae331-130">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="ae331-130">**IgnoreSchema**</span></span>|<span data-ttu-id="ae331-131">Ignore les schémas inline et charge les données dans le schéma existant de l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ae331-131">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="ae331-132">Toute donnée ne correspondant pas au schéma existant est ignorée.</span><span class="sxs-lookup"><span data-stu-id="ae331-132">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="ae331-133">S'il n'existe pas de schéma dans l'objet <xref:System.Data.DataSet>, aucune donnée n'est chargée.</span><span class="sxs-lookup"><span data-stu-id="ae331-133">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="ae331-134">Si les données sont un DiffGram, **IgnoreSchema** a les mêmes fonctionnalités que **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="ae331-134">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="ae331-135">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="ae331-135">**InferSchema**</span></span>|<span data-ttu-id="ae331-136">Ignore tout schéma inline et déduit le schéma de la structure des données XML, puis charge les données.</span><span class="sxs-lookup"><span data-stu-id="ae331-136">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="ae331-137">Si le <xref:System.Data.DataSet> contient déjà un schéma, le schéma en cours est étendu par l'ajout de colonnes dans les tables existantes.</span><span class="sxs-lookup"><span data-stu-id="ae331-137">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="ae331-138">Des tables supplémentaires ne seront pas ajoutées s'il n'existe pas de tables.</span><span class="sxs-lookup"><span data-stu-id="ae331-138">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="ae331-139">Une exception est levée si une table déduite existe déjà avec un autre espace de noms, ou en cas de conflit entre des colonnes inférées et des colonnes existantes.</span><span class="sxs-lookup"><span data-stu-id="ae331-139">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="ae331-140">Pour plus d’informations sur la façon dont **ReadXmlSchema** déduit un schéma à partir d’un document XML, consultez [déduction de la structure relationnelle d’un jeu de données à partir de XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ae331-140">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="ae331-141">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="ae331-141">**DiffGram**</span></span>|<span data-ttu-id="ae331-142">Lit un DiffGram et ajoute les données au schéma en cours.</span><span class="sxs-lookup"><span data-stu-id="ae331-142">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="ae331-143">**DiffGram** fusionne les nouvelles lignes avec les lignes existantes où les valeurs d’identificateur uniques correspondent.</span><span class="sxs-lookup"><span data-stu-id="ae331-143">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="ae331-144">Voir « Fusion de données provenant de XML » à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ae331-144">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="ae331-145">Pour plus d’informations sur les DiffGrams, consultez [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="ae331-145">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="ae331-146">**Fragment**</span><span class="sxs-lookup"><span data-stu-id="ae331-146">**Fragment**</span></span>|<span data-ttu-id="ae331-147">Poursuit la lecture de plusieurs fragments XML jusqu'à ce que la fin du flux soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="ae331-147">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="ae331-148">Les fragments qui correspondent au schéma de l'objet <xref:System.Data.DataSet> sont ajoutés aux tables appropriées.</span><span class="sxs-lookup"><span data-stu-id="ae331-148">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="ae331-149">Les fragments qui ne correspondent pas au schéma <xref:System.Data.DataSet> sont écartés.</span><span class="sxs-lookup"><span data-stu-id="ae331-149">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="ae331-150">Si vous transmettez un **XmlReader** à **ReadXml** qui est positionné dans un document XML, **ReadXml** lit le nœud d’élément suivant et le traite comme l’élément racine, en lisant jusqu’à la fin du nœud d’élément uniquement.</span><span class="sxs-lookup"><span data-stu-id="ae331-150">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="ae331-151">Cela ne s’applique pas si vous spécifiez **XmlReadMode. fragment**.</span><span class="sxs-lookup"><span data-stu-id="ae331-151">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="ae331-152">Entités DTD</span><span class="sxs-lookup"><span data-stu-id="ae331-152">DTD Entities</span></span>  

 <span data-ttu-id="ae331-153">Si votre XML contient des entités définies dans un schéma de définition de type de document (DTD), une exception est levée si vous tentez de charger un <xref:System.Data.DataSet> en passant un nom de fichier, un flux ou un **XmlReader** non validant à **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="ae331-153">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="ae331-154">Au lieu de cela, vous devez créer un **XmlValidatingReader**, avec **EntityHandling** défini sur **EntityHandling. ExpandEntities**, et passer votre **XmlValidatingReader** à **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="ae331-154">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="ae331-155">Le **XmlValidatingReader** développera les entités avant la lecture par <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="ae331-155">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="ae331-156">Les exemples de code suivants montrent comment charger un objet <xref:System.Data.DataSet> à partir d'un flux XML.</span><span class="sxs-lookup"><span data-stu-id="ae331-156">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="ae331-157">Le premier exemple montre un nom de fichier passé à la méthode **ReadXml** .</span><span class="sxs-lookup"><span data-stu-id="ae331-157">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="ae331-158">Le second illustre le cas d'une chaîne contenant le XML chargé à l'aide d'un objet <xref:System.IO.StringReader>.</span><span class="sxs-lookup"><span data-stu-id="ae331-158">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
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
> <span data-ttu-id="ae331-159">Si vous appelez **ReadXml** pour charger un fichier très volumineux, vous risquez de rencontrer des problèmes de performances.</span><span class="sxs-lookup"><span data-stu-id="ae331-159">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="ae331-160">Pour garantir des performances optimales pour **ReadXml**, sur un fichier volumineux, appelez la <xref:System.Data.DataTable.BeginLoadData%2A> méthode pour chaque table dans le <xref:System.Data.DataSet> , puis appelez **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="ae331-160">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="ae331-161">Enfin, appelez <xref:System.Data.DataTable.EndLoadData%2A> pour chaque table de l'objet <xref:System.Data.DataSet>, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ae331-161">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="ae331-162">Si le schéma XSD de votre <xref:System.Data.DataSet> inclut un **targetNamespace**, il est possible que les données ne soient pas lues et que vous rencontriez des exceptions lors de l’appel de **ReadXml** pour charger l' <xref:System.Data.DataSet> élément with XML qui contient des éléments sans espace de noms éligible.</span><span class="sxs-lookup"><span data-stu-id="ae331-162">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="ae331-163">Pour lire des éléments non qualifiés dans ce cas, affectez à **elementFormDefault** la valeur « qualified » dans votre schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="ae331-163">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="ae331-164">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ae331-164">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="ae331-165">Fusion de données provenant de XML</span><span class="sxs-lookup"><span data-stu-id="ae331-165">Merging Data from XML</span></span>  

 <span data-ttu-id="ae331-166">Si l'objet <xref:System.Data.DataSet> contient déjà des données, les nouvelles données provenant de XML sont ajoutées aux données déjà présentes dans l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ae331-166">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ae331-167">**ReadXml** ne fusionne pas le XML avec les <xref:System.Data.DataSet> informations de ligne avec les clés primaires correspondantes.</span><span class="sxs-lookup"><span data-stu-id="ae331-167">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="ae331-168">Pour remplacer les informations de ligne existantes par de nouvelles informations à partir de XML, utilisez **ReadXml** pour créer un nouveau <xref:System.Data.DataSet> , puis <xref:System.Data.DataSet.Merge%2A> le nouveau <xref:System.Data.DataSet> dans le existant <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="ae331-168">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ae331-169">Notez que le chargement d’un DiffGram à l’aide de **ReadXml** avec un **XmlReadMode** de **DiffGram** fusionne les lignes qui ont le même identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="ae331-169">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae331-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae331-170">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ae331-171">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="ae331-171">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="ae331-172">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="ae331-172">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="ae331-173">Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ae331-173">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="ae331-174">Déduction de la structure relationnelle des DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="ae331-174">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="ae331-175">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="ae331-175">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="ae331-176">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="ae331-176">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="ae331-177">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ae331-177">ADO.NET Overview</span></span>](../ado-net-overview.md)
