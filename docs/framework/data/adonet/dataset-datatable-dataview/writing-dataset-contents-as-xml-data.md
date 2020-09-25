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
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="6e3fe-102">Écriture du contenu d'un DataSet comme données XML</span><span class="sxs-lookup"><span data-stu-id="6e3fe-102">Writing DataSet Contents as XML Data</span></span>

<span data-ttu-id="6e3fe-103">Dans ADO.NET, vous pouvez écrire une représentation XML d'un objet<xref:System.Data.DataSet>, avec ou sans son schéma.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="6e3fe-104">Si les informations de schéma sont incluses inline avec le XML, elles sont écrites à l'aide du langage XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="6e3fe-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="6e3fe-105">Le schéma contient les définitions des tables de l'objet <xref:System.Data.DataSet>, ainsi que les définitions des relations et des contraintes.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="6e3fe-106">Lorsqu'un objet <xref:System.Data.DataSet> est écrit sous forme de données XML, les lignes de l'objet <xref:System.Data.DataSet> sont écrites dans leur version actuelle.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="6e3fe-107">Toutefois, l'objet <xref:System.Data.DataSet> peut aussi être écrit sous la forme d'un DiffGram pour que les valeurs actuelles comme les valeurs d'origine des lignes soient incluses.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="6e3fe-108">La représentation XML du <xref:System.Data.DataSet> peut être écrite dans un fichier, un flux, un **XmlWriter**ou une chaîne.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="6e3fe-109">Ces différentes possibilités offrent une grande souplesse pour le transport de la représentation XML de l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6e3fe-110">Pour obtenir la représentation XML de <xref:System.Data.DataSet> sous forme de chaîne, utilisez la méthode **GetXml** comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="6e3fe-111">**GetXml** retourne la représentation XML du <xref:System.Data.DataSet> sans informations de schéma.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="6e3fe-112">Pour écrire les informations de schéma à partir du <xref:System.Data.DataSet> (comme schéma XML) dans une chaîne, utilisez **GetXmlSchema**.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="6e3fe-113">Pour écrire <xref:System.Data.DataSet> dans un fichier, un flux ou un **XmlWriter**, utilisez la méthode **WriteXml** .</span><span class="sxs-lookup"><span data-stu-id="6e3fe-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="6e3fe-114">Le premier paramètre que vous transmettez à **WriteXml** est la destination de la sortie XML.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="6e3fe-115">Par exemple, transmettez une chaîne contenant un nom de fichier, un objet **System. IO. TextWriter** , et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="6e3fe-116">Vous pouvez passer un deuxième paramètre facultatif d’un **XmlWriteMode** pour spécifier le mode d’écriture de la sortie XML.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="6e3fe-117">Le tableau suivant présente les options de **XmlWriteMode**.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="6e3fe-118">Option XmlWriteMode</span><span class="sxs-lookup"><span data-stu-id="6e3fe-118">XmlWriteMode option</span></span>|<span data-ttu-id="6e3fe-119">Description</span><span class="sxs-lookup"><span data-stu-id="6e3fe-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="6e3fe-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="6e3fe-120">**IgnoreSchema**</span></span>|<span data-ttu-id="6e3fe-121">Écrit le contenu actuel de l'objet <xref:System.Data.DataSet> sous forme de données XML, sans schéma XML.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="6e3fe-122">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-122">This is the default.</span></span>|  
|<span data-ttu-id="6e3fe-123">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="6e3fe-123">**WriteSchema**</span></span>|<span data-ttu-id="6e3fe-124">Écrit le contenu actuel de l'objet <xref:System.Data.DataSet> en tant que données XML, avec la structure relationnelle comme schéma XML inline.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="6e3fe-125">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="6e3fe-125">**DiffGram**</span></span>|<span data-ttu-id="6e3fe-126">Écrit l'ensemble de l'objet <xref:System.Data.DataSet> en tant que DiffGram, y compris les valeurs d'origine et actuelle.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="6e3fe-127">Pour plus d’informations, consultez [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="6e3fe-127">For more information, see [DiffGrams](diffgrams.md).</span></span>|  
  
 <span data-ttu-id="6e3fe-128">Lors de l’écriture d’une représentation XML d’un <xref:System.Data.DataSet> qui contient des objets **DataRelation** , vous souhaiterez probablement que le XML obtenu ait les lignes enfants de chaque relation imbriquées dans leurs éléments parents associés.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="6e3fe-129">Pour ce faire, affectez la **valeur true** à la propriété **Nested** du **DataRelation** lorsque vous ajoutez le **DataRelation** à <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="6e3fe-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6e3fe-130">Pour plus d’informations, consultez [imbrication de DataRelations](nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="6e3fe-130">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="6e3fe-131">Voici deux exemples d’écriture de la représentation XML d’un <xref:System.Data.DataSet> dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-131">The following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="6e3fe-132">Le premier exemple passe le nom de fichier pour le XML résultant en tant que chaîne à **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="6e3fe-133">Le deuxième exemple passe un objet **System. IO. StreamWriter** .</span><span class="sxs-lookup"><span data-stu-id="6e3fe-133">The second example passes a **System.IO.StreamWriter** object.</span></span>
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="6e3fe-134">Mappage de colonnes à des éléments, des attributs et du texte XML</span><span class="sxs-lookup"><span data-stu-id="6e3fe-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  

 <span data-ttu-id="6e3fe-135">Vous pouvez spécifier la façon dont une colonne d’une table est représentée en XML à l’aide de la propriété **ColumnMapping** de l’objet **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="6e3fe-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="6e3fe-136">Le tableau suivant présente les différentes valeurs de **MappingType** pour la propriété **ColumnMapping** d’une colonne de table, ainsi que les données XML résultantes.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="6e3fe-137">Valeur MappingType</span><span class="sxs-lookup"><span data-stu-id="6e3fe-137">MappingType value</span></span>|<span data-ttu-id="6e3fe-138">Description</span><span class="sxs-lookup"><span data-stu-id="6e3fe-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="6e3fe-139">**Element**</span><span class="sxs-lookup"><span data-stu-id="6e3fe-139">**Element**</span></span>|<span data-ttu-id="6e3fe-140">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-140">This is the default.</span></span> <span data-ttu-id="6e3fe-141">La colonne est écrite sous la forme d'un élément XML, où ColumnName représente le nom de l'élément et le contenu de la colonne est écrit en tant que texte de l'élément.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="6e3fe-142">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6e3fe-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="6e3fe-143">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="6e3fe-143">**Attribute**</span></span>|<span data-ttu-id="6e3fe-144">La colonne est écrite sous la forme d'un attribut XML de l'élément XML de la ligne actuelle, où ColumnName représente le nom de l'attribut et le contenu de la colonne est écrit en tant que valeur de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="6e3fe-145">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6e3fe-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="6e3fe-146">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="6e3fe-146">**SimpleContent**</span></span>|<span data-ttu-id="6e3fe-147">Le contenu de la colonne est écrit sous forme de texte dans l'élément XML de la ligne actuelle.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="6e3fe-148">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6e3fe-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="6e3fe-149">Notez que **simpleContent** ne peut pas être défini pour une colonne d’une table qui contient des colonnes d' **éléments** ou des relations imbriquées.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="6e3fe-150">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="6e3fe-150">**Hidden**</span></span>|<span data-ttu-id="6e3fe-151">La colonne n'est pas écrite dans la sortie XML.</span><span class="sxs-lookup"><span data-stu-id="6e3fe-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e3fe-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e3fe-152">See also</span></span>

- [<span data-ttu-id="6e3fe-153">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="6e3fe-153">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="6e3fe-154">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="6e3fe-154">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="6e3fe-155">Imbrication de DataRelations</span><span class="sxs-lookup"><span data-stu-id="6e3fe-155">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="6e3fe-156">Écriture des informations de schéma de DataSet comme XSD</span><span class="sxs-lookup"><span data-stu-id="6e3fe-156">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="6e3fe-157">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="6e3fe-157">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="6e3fe-158">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6e3fe-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
