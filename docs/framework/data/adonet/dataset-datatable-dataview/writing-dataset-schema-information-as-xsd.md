---
title: Écriture des informations de schéma de DataSet comme XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: f9664d8e7bc221da68492140f30419ea8fb0d316
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204368"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="3aa5f-102">Écriture des informations de schéma de DataSet comme XSD</span><span class="sxs-lookup"><span data-stu-id="3aa5f-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="3aa5f-103">Vous pouvez écrire le schéma d'un objet <xref:System.Data.DataSet> sous la forme d'un schéma en langage XSD (XML Schema Definition), de façon à pouvoir le transporter, avec ou sans les données connexes, dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="3aa5f-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="3aa5f-104">Le schéma XML peut être écrit dans un fichier, un flux, <xref:System.Xml.XmlWriter>un ou une chaîne; il est utile pour générer un **DataSet**fortement typé.</span><span class="sxs-lookup"><span data-stu-id="3aa5f-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="3aa5f-105">Pour plus d’informations sur les objets **DataSet** fortement typés, consultez [DataSets typés](typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="3aa5f-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](typed-datasets.md).</span></span>  
  
 <span data-ttu-id="3aa5f-106">Vous pouvez spécifier la façon dont une colonne d’une table est représentée dans le schéma XML à l’aide <xref:System.Data.DataColumn> de la propriété ColumnMapping de l’objet.</span><span class="sxs-lookup"><span data-stu-id="3aa5f-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="3aa5f-107">Pour plus d’informations, consultez «mappage de colonnes à des éléments, des attributs et du texte XML» dans écriture du contenu d’un [DataSet en tant que données XML](writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="3aa5f-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="3aa5f-108">Pour écrire le schéma d’un **DataSet** sous forme de schéma XML, dans un fichier, un flux ou un **XmlWriter**, utilisez la méthode **WriteXmlSchema** du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="3aa5f-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="3aa5f-109">**WriteXmlSchema** accepte un paramètre qui spécifie la destination du schéma XML résultant.</span><span class="sxs-lookup"><span data-stu-id="3aa5f-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="3aa5f-110">Les exemples de code suivants montrent comment écrire le schéma XML d’un **DataSet** dans un fichier en passant une chaîne contenant un nom de fichier et <xref:System.IO.StreamWriter> un objet.</span><span class="sxs-lookup"><span data-stu-id="3aa5f-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="3aa5f-111">Pour obtenir le schéma d’un **DataSet** et l’écrire sous la forme d’une chaîne de schéma XML, utilisez la méthode **GetXmlSchema** , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3aa5f-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="3aa5f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3aa5f-112">See also</span></span>

- [<span data-ttu-id="3aa5f-113">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="3aa5f-113">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="3aa5f-114">Écriture du contenu d’un DataSet comme données XML</span><span class="sxs-lookup"><span data-stu-id="3aa5f-114">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)
- [<span data-ttu-id="3aa5f-115">Datasets typés</span><span class="sxs-lookup"><span data-stu-id="3aa5f-115">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="3aa5f-116">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="3aa5f-116">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="3aa5f-117">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="3aa5f-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
