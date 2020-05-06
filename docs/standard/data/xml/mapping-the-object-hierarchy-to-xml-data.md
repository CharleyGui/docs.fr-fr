---
title: Mappage de la hiérarchie d'objets à des données XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 4ad505749625e22a09406549329179990b81c140
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794388"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="b8cf6-102">Mappage de la hiérarchie d'objets à des données XML</span><span class="sxs-lookup"><span data-stu-id="b8cf6-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="b8cf6-103">Quand un document XML est en mémoire, sa représentation conceptuelle est une arborescence.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="b8cf6-104">Pour la programmation, vous disposez d’une hiérarchie d’objets pour accéder aux nœuds de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="b8cf6-105">L'exemple suivant illustre la manière dont le contenu XML se transforme en nœuds.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="b8cf6-106">Lorsque le contenu XML est lu dans le DOM (Document Object Model) XML, ses fragments sont convertis en nœuds, et ces nœuds conservent des métadonnées supplémentaires à leur propre sujet, telles que leur type de nœud et leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="b8cf6-107">Le type de nœud est son objet et est l'élément qui détermine les actions pouvant être réalisées ainsi que les propriétés pouvant être définies ou extraites.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="b8cf6-108">Supposons l'exemple de code XML simple suivant :</span><span class="sxs-lookup"><span data-stu-id="b8cf6-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="b8cf6-109">**Input**</span><span class="sxs-lookup"><span data-stu-id="b8cf6-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="b8cf6-110">L’entrée est représentée dans la mémoire sous la forme de l’arborescence de nœuds suivante, avec la propriété de type de nœud assignée :</span><span class="sxs-lookup"><span data-stu-id="b8cf6-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="b8cf6-111">![Exemple d'arborescence de nœuds](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="b8cf6-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="b8cf6-112">Représentation sous forme d’arborescence de nœuds book et title</span><span class="sxs-lookup"><span data-stu-id="b8cf6-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="b8cf6-113">L'élément `book` devient un objet **XmlElement**, tout comme l'élément suivant `title` devient aussi un objet **XmlElement**, tandis que le contenu de l'élément devient un objet **XmlText**.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="b8cf6-114">Si vous examinez les méthodes et propriétés de **XmlElement**, vous constaterez qu'elles sont différentes des méthodes et propriétés disponibles pour un objet **XmlText**.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="b8cf6-115">Il est donc vital de connaître le type de nœud dans lequel le balisage XML se transforme, puisque ce type de nœud détermine les actions possibles.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="b8cf6-116">L'exemple suivant lit dans les données XML et écrit le texte différent, en fonction du type de nœud.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="b8cf6-117">En utilisant comme entrée le fichier de données XML **items.xml** :</span><span class="sxs-lookup"><span data-stu-id="b8cf6-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="b8cf6-118">**Input**</span><span class="sxs-lookup"><span data-stu-id="b8cf6-118">**Input**</span></span>  
  
```xml  
<?xml version="1.0"?>  
<!-- This is a sample XML document -->  
<!DOCTYPE Items [<!ENTITY number "123">]>  
<Items>  
  <Item>Test with an entity: &number;</Item>  
  <Item>test with a child element <more/> stuff</Item>  
  <Item>test with a CDATA section <![CDATA[<456>]]> def</Item>  
  <Item>Test with a char entity: A</Item>  
  <!-- Fourteen chars in this element.-->  
  <Item>1234567890ABCD</Item>  
</Items>  
```  
  
 <span data-ttu-id="b8cf6-119">L'exemple de code suivant lit le fichier **items.xml** et affiche des informations pour chaque type de nœud.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
    Private Const filename As String = "items.xml"  
  
    Public Shared Sub Main()  
  
        Dim reader As XmlTextReader = Nothing  
  
        Try  
            ' Load the reader with the data file and
            'ignore all white space nodes.
            reader = New XmlTextReader(filename)  
            reader.WhitespaceHandling = WhitespaceHandling.None  
  
            ' Parse the file and display each of the nodes.  
            While reader.Read()  
                Select Case reader.NodeType  
                    Case XmlNodeType.Element  
                        Console.Write("<{0}>", reader.Name)  
                    Case XmlNodeType.Text  
                        Console.Write(reader.Value)  
                    Case XmlNodeType.CDATA  
                        Console.Write("<![CDATA[{0}]]>", reader.Value)  
                    Case XmlNodeType.ProcessingInstruction  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value)  
                    Case XmlNodeType.Comment  
                        Console.Write("<!--{0}-->", reader.Value)  
                    Case XmlNodeType.XmlDeclaration  
                        Console.Write("<?xml version='1.0'?>")  
                    Case XmlNodeType.Document  
                    Case XmlNodeType.DocumentType  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value)  
                    Case XmlNodeType.EntityReference  
                        Console.Write(reader.Name)  
                    Case XmlNodeType.EndElement  
                        Console.Write("</{0}>", reader.Name)  
                End Select  
            End While  
  
        Finally  
            If Not (reader Is Nothing) Then  
                reader.Close()  
            End If  
        End Try  
    End Sub 'Main ' End class  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    private const String filename = "items.xml";  
  
    public static void Main()  
    {  
        XmlTextReader reader = null;  
  
        try  
        {  
            // Load the reader with the data file and ignore
            // all white space nodes.  
            reader = new XmlTextReader(filename);  
            reader.WhitespaceHandling = WhitespaceHandling.None;  
  
            // Parse the file and display each of the nodes.  
            while (reader.Read())  
            {  
                switch (reader.NodeType)  
                {  
                    case XmlNodeType.Element:  
                        Console.Write("<{0}>", reader.Name);  
                        break;  
                    case XmlNodeType.Text:  
                        Console.Write(reader.Value);  
                        break;  
                    case XmlNodeType.CDATA:  
                        Console.Write("<![CDATA[{0}]]>", reader.Value);  
                        break;  
                    case XmlNodeType.ProcessingInstruction:  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.Comment:  
                        Console.Write("<!--{0}-->", reader.Value);  
                        break;  
                    case XmlNodeType.XmlDeclaration:  
                        Console.Write("<?xml version='1.0'?>");  
                        break;  
                    case XmlNodeType.Document:  
                        break;  
                    case XmlNodeType.DocumentType:  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.EntityReference:  
                        Console.Write(reader.Name);  
                        break;  
                    case XmlNodeType.EndElement:  
                        Console.Write("</{0}>", reader.Name);  
                        break;  
                }  
            }  
        }  
  
        finally  
        {  
            if (reader != null)  
                reader.Close();  
        }  
    }  
} // End class  
```  
  
 <span data-ttu-id="b8cf6-120">La sortie de cet exemple révèle le mappage des données aux types de nœud.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="b8cf6-121">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="b8cf6-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>
```  
  
 <span data-ttu-id="b8cf6-122">En prenant l'entrée une ligne à la fois et en utilisant la sortie générée par le code, vous pouvez vous servir du tableau suivant pour analyser quel nœud test a généré quelles lignes de sortie, ce qui vous aidera à déterminer plus clairement quelles données XML se sont transformées en quelle catégorie de types de nœud.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="b8cf6-123">Entrée</span><span class="sxs-lookup"><span data-stu-id="b8cf6-123">Input</span></span>|<span data-ttu-id="b8cf6-124">Output</span><span class="sxs-lookup"><span data-stu-id="b8cf6-124">Output</span></span>|<span data-ttu-id="b8cf6-125">Type de nœud test</span><span class="sxs-lookup"><span data-stu-id="b8cf6-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="b8cf6-126">\<?xml version="1.0"?></span><span class="sxs-lookup"><span data-stu-id="b8cf6-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="b8cf6-127">\<?xml version='1.0'?></span><span class="sxs-lookup"><span data-stu-id="b8cf6-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="b8cf6-128">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="b8cf6-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="b8cf6-129">\<!-- Exemple de document XML --></span><span class="sxs-lookup"><span data-stu-id="b8cf6-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="b8cf6-130">\<!--Exemple de document XML --></span><span class="sxs-lookup"><span data-stu-id="b8cf6-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="b8cf6-131">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="b8cf6-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="b8cf6-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span><span class="sxs-lookup"><span data-stu-id="b8cf6-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="b8cf6-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span><span class="sxs-lookup"><span data-stu-id="b8cf6-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="b8cf6-134">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="b8cf6-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="b8cf6-135">\<Items></span><span class="sxs-lookup"><span data-stu-id="b8cf6-135">\<Items></span></span>|<span data-ttu-id="b8cf6-136">\<Items></span><span class="sxs-lookup"><span data-stu-id="b8cf6-136">\<Items></span></span>|<span data-ttu-id="b8cf6-137">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b8cf6-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b8cf6-138">\<Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-138">\<Item></span></span>|<span data-ttu-id="b8cf6-139">\<Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-139">\<Item></span></span>|<span data-ttu-id="b8cf6-140">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b8cf6-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b8cf6-141">Test with an entity: &number;</span><span class="sxs-lookup"><span data-stu-id="b8cf6-141">Test with an entity: &number;</span></span>|<span data-ttu-id="b8cf6-142">Test with an entity: 123</span><span class="sxs-lookup"><span data-stu-id="b8cf6-142">Test with an entity: 123</span></span>|<span data-ttu-id="b8cf6-143">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b8cf6-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b8cf6-144">\</Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-144">\</Item></span></span>|<span data-ttu-id="b8cf6-145">\</Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-145">\</Item></span></span>|<span data-ttu-id="b8cf6-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b8cf6-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="b8cf6-147">\<Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-147">\<Item></span></span>|<span data-ttu-id="b8cf6-148">\<Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-148">\<Item></span></span>|<span data-ttu-id="b8cf6-149">XmNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b8cf6-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="b8cf6-150">test with a child element</span><span class="sxs-lookup"><span data-stu-id="b8cf6-150">test with a child element</span></span>|<span data-ttu-id="b8cf6-151">test with a child element</span><span class="sxs-lookup"><span data-stu-id="b8cf6-151">test with a child element</span></span>|<span data-ttu-id="b8cf6-152">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b8cf6-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b8cf6-153">\<more></span><span class="sxs-lookup"><span data-stu-id="b8cf6-153">\<more></span></span>|<span data-ttu-id="b8cf6-154">\<more></span><span class="sxs-lookup"><span data-stu-id="b8cf6-154">\<more></span></span>|<span data-ttu-id="b8cf6-155">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b8cf6-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b8cf6-156">stuff</span><span class="sxs-lookup"><span data-stu-id="b8cf6-156">stuff</span></span>|<span data-ttu-id="b8cf6-157">stuff</span><span class="sxs-lookup"><span data-stu-id="b8cf6-157">stuff</span></span>|<span data-ttu-id="b8cf6-158">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b8cf6-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b8cf6-159">\</Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-159">\</Item></span></span>|<span data-ttu-id="b8cf6-160">\</Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-160">\</Item></span></span>|<span data-ttu-id="b8cf6-161">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b8cf6-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="b8cf6-162">\<Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-162">\<Item></span></span>|<span data-ttu-id="b8cf6-163">\<Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-163">\<Item></span></span>|<span data-ttu-id="b8cf6-164">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b8cf6-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b8cf6-165">test with a CDATA section</span><span class="sxs-lookup"><span data-stu-id="b8cf6-165">test with a CDATA section</span></span>|<span data-ttu-id="b8cf6-166">test with a CDATA section</span><span class="sxs-lookup"><span data-stu-id="b8cf6-166">test with a CDATA section</span></span>|<span data-ttu-id="b8cf6-167">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="b8cf6-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="b8cf6-168"><![CDATA[\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="b8cf6-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="b8cf6-169"><![CDATA[\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="b8cf6-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="b8cf6-170">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="b8cf6-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="b8cf6-171">def</span><span class="sxs-lookup"><span data-stu-id="b8cf6-171">def</span></span>|<span data-ttu-id="b8cf6-172">def</span><span class="sxs-lookup"><span data-stu-id="b8cf6-172">def</span></span>|<span data-ttu-id="b8cf6-173">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b8cf6-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b8cf6-174">\</Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-174">\</Item></span></span>|<span data-ttu-id="b8cf6-175">\</Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-175">\</Item></span></span>|<span data-ttu-id="b8cf6-176">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b8cf6-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="b8cf6-177">\<Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-177">\<Item></span></span>|<span data-ttu-id="b8cf6-178">\<Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-178">\<Item></span></span>|<span data-ttu-id="b8cf6-179">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b8cf6-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b8cf6-180">Test with a char entity: &\#65;</span><span class="sxs-lookup"><span data-stu-id="b8cf6-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="b8cf6-181">Test with a char entity: A</span><span class="sxs-lookup"><span data-stu-id="b8cf6-181">Test with a char entity: A</span></span>|<span data-ttu-id="b8cf6-182">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b8cf6-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b8cf6-183">\</Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-183">\</Item></span></span>|<span data-ttu-id="b8cf6-184">\</Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-184">\</Item></span></span>|<span data-ttu-id="b8cf6-185">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b8cf6-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="b8cf6-186">\<!-- Quatorze caractères dans cet élément.--></span><span class="sxs-lookup"><span data-stu-id="b8cf6-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="b8cf6-187">\<--Quatorze caractères dans cet élément.--></span><span class="sxs-lookup"><span data-stu-id="b8cf6-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="b8cf6-188">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="b8cf6-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="b8cf6-189">\<Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-189">\<Item></span></span>|<span data-ttu-id="b8cf6-190">\<Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-190">\<Item></span></span>|<span data-ttu-id="b8cf6-191">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b8cf6-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b8cf6-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="b8cf6-192">1234567890ABCD</span></span>|<span data-ttu-id="b8cf6-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="b8cf6-193">1234567890ABCD</span></span>|<span data-ttu-id="b8cf6-194">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b8cf6-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b8cf6-195">\</Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-195">\</Item></span></span>|<span data-ttu-id="b8cf6-196">\</Item></span><span class="sxs-lookup"><span data-stu-id="b8cf6-196">\</Item></span></span>|<span data-ttu-id="b8cf6-197">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b8cf6-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="b8cf6-198">\</Items></span><span class="sxs-lookup"><span data-stu-id="b8cf6-198">\</Items></span></span>|<span data-ttu-id="b8cf6-199">\</Items></span><span class="sxs-lookup"><span data-stu-id="b8cf6-199">\</Items></span></span>|<span data-ttu-id="b8cf6-200">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b8cf6-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="b8cf6-201">Il est essentiel de savoir quel type de nœud est assigné, puisque le type de nœud régit les actions valides et les types de propriétés qu'il est possible de définir et d'extraire.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="b8cf6-202">La création de nœuds pour l'espace blanc est contrôlée au moment du chargement des données dans le DOM par l'indicateur **PreserveWhitespace**.</span><span class="sxs-lookup"><span data-stu-id="b8cf6-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="b8cf6-203">Pour plus d'informations, consultez [Gestion des espaces blancs significatifs ou non lors du chargement du DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="b8cf6-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="b8cf6-204">Pour ajouter de nouveaux nœuds au DOM, voir [Insertion de nœuds dans un document XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b8cf6-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="b8cf6-205">Pour supprimer des nœuds du DOM, voir [Suppression de nœuds, de contenu et de valeurs d'un document XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b8cf6-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="b8cf6-206">Pour modifier le contenu de nœuds dans le DOM, voir [Modification de nœuds, de contenu et de valeurs dans un document XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b8cf6-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8cf6-207">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8cf6-207">See also</span></span>

- [<span data-ttu-id="b8cf6-208">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="b8cf6-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
