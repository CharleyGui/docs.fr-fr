---
title: XPathNodeIterator dans les transformations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
ms.openlocfilehash: cd8320071f1de15d503c94c138c02cab5742685c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818431"
---
# <a name="xpathnodeiterator-in-transformations"></a><span data-ttu-id="bc39e-102">XPathNodeIterator dans les transformations</span><span class="sxs-lookup"><span data-stu-id="bc39e-102">XPathNodeIterator in Transformations</span></span>
<span data-ttu-id="bc39e-103">L’objet <xref:System.Xml.XPath.XPathNodeIterator> fournit des méthodes pour itérer sur une collection de nœuds créée à la suite d’une requête XPath ou d’un fragment d’arborescence résultat converti en une collection de nœuds à l’aide de la méthode node-set.</span><span class="sxs-lookup"><span data-stu-id="bc39e-103">The <xref:System.Xml.XPath.XPathNodeIterator> provides methods to iterate over a set of nodes created as the result of an XML Path Language (XPath) query or a result tree fragment converted to a node set by use of the node-set method.</span></span> <span data-ttu-id="bc39e-104">L'objet <xref:System.Xml.XPath.XPathNodeIterator> vous permet d'itérer sur les nœuds à l'intérieur de cette collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="bc39e-104">The <xref:System.Xml.XPath.XPathNodeIterator> enables you to iterate over the nodes within that node set.</span></span> <span data-ttu-id="bc39e-105">Dès qu'une collection de nœuds est extraite, la classe <xref:System.Xml.XPath.XPathNodeIterator> fournit un curseur avant uniquement en lecture seule à la collection de nœuds sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="bc39e-105">Once a node set is retrieved, the <xref:System.Xml.XPath.XPathNodeIterator> class provides a read-only, forward-only cursor to the selected set of nodes.</span></span> <span data-ttu-id="bc39e-106">La collection de nœuds étant créée dans l'ordre du document, l'appel de cette méthode permet un déplacement vers le prochain nœud dans l'ordre du document.</span><span class="sxs-lookup"><span data-stu-id="bc39e-106">The node set is created in document order, so calling this method moves to the next node in document order.</span></span> <span data-ttu-id="bc39e-107"><xref:System.Xml.XPath.XPathNodeIterator> ne construit pas une arborescence de nœuds de tous les nœuds de l'ensemble.</span><span class="sxs-lookup"><span data-stu-id="bc39e-107"><xref:System.Xml.XPath.XPathNodeIterator> does not build a node tree of all the nodes in the set.</span></span> <span data-ttu-id="bc39e-108">Elle fournit à la place une seule fenêtre de nœuds dans les données, exposant le nœud sous-jacent vers lequel elle pointe lors du déplacement dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="bc39e-108">Instead, it provides a single node window into the data, exposing the underlying node it points to as you move around in the tree.</span></span> <span data-ttu-id="bc39e-109">Les méthodes et propriétés disponibles à partir de la classe <xref:System.Xml.XPath.XPathNodeIterator> vous permettent d'obtenir des informations à partir du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="bc39e-109">The methods and properties available from the <xref:System.Xml.XPath.XPathNodeIterator> class enable you to get information from the current node.</span></span> <span data-ttu-id="bc39e-110">Pour obtenir la liste des méthodes et propriétés disponibles, voir <xref:System.Windows.Forms.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="bc39e-110">For a list of the available methods and properties, see <xref:System.Windows.Forms.ToolBar>.</span></span>  
  
 <span data-ttu-id="bc39e-111">Dans la mesure où un objet <xref:System.Xml.XPath.XPathNodeIterator> se déplace sur une collection de nœuds créée à partir d’une requête XPath et se déplace uniquement en avant, la méthode <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> permet de se déplacer.</span><span class="sxs-lookup"><span data-stu-id="bc39e-111">Since an <xref:System.Xml.XPath.XPathNodeIterator> moves over a set of nodes created from an XPath query and moves forward only, the way to move is by using the <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> method.</span></span> <span data-ttu-id="bc39e-112">Le type de retour de cette méthode est `Boolean`, qui retourne `true` si elle se déplace vers le nœud sélectionné suivant, et `false` s’il n’y a plus de nœud sélectionné.</span><span class="sxs-lookup"><span data-stu-id="bc39e-112">The return type of this method is `Boolean`, returning `true` if it moves to the next selected node, and `false` if there are no more selected nodes.</span></span> <span data-ttu-id="bc39e-113">Si elle retourne `true`, la liste suivante affiche les propriétés disponibles :</span><span class="sxs-lookup"><span data-stu-id="bc39e-113">If it returns `true`, the following list shows the properties available:</span></span>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 <span data-ttu-id="bc39e-114">Lorsque vous examinez une collection de nœuds pour la premières fois, un appel à la méthode <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> doit être effectué pour placer l'objet <xref:System.Xml.XPath.XPathNodeIterator> sur le premier nœud de la collection sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="bc39e-114">When you are looking at a node set for the first time, a call to <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> must be made to position the <xref:System.Xml.XPath.XPathNodeIterator> on the first node of the selected set.</span></span> <span data-ttu-id="bc39e-115">Cela permet l'écriture d'une boucle while.</span><span class="sxs-lookup"><span data-stu-id="bc39e-115">This allows a while loop to be written.</span></span>  
  
 <span data-ttu-id="bc39e-116">L'exemple de code suivant illustre le passage d'un objet <xref:System.Xml.XPath.XPathNodeIterator> à un autre objet <xref:System.Xml.Xsl.XslTransform> en tant que paramètre dans l'objet <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="bc39e-116">The following code example shows how to pass an <xref:System.Xml.XPath.XPathNodeIterator> to an <xref:System.Xml.Xsl.XslTransform> as a parameter in the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span> <span data-ttu-id="bc39e-117">L'entrée du code est **books.xm** et la feuille de style est **text.xsl**.</span><span class="sxs-lookup"><span data-stu-id="bc39e-117">The input to the code is **books.xml**, and the style sheet is **text.xsl**.</span></span> <span data-ttu-id="bc39e-118">Le fichier **test.xml** est l'objet <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="bc39e-118">The file **test.xml** is the <xref:System.Xml.XPath.XPathDocument>.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
  
Public Class sample  
  
   Public Shared Sub Main()  
      Dim Doc As New XPathDocument("books.xml")  
      Dim nav As XPathNavigator = Doc.CreateNavigator()  
      Dim Iterator As XPathNodeIterator = nav.Select("/bookstore/book")  
  
      Dim arg As New XsltArgumentList()  
      arg.AddParam("param1", "", Iterator)  
  
      Dim xslt As New XslTransform()  
      xslt.Load("test.xsl")  
  
      Dim xd As New XPathDocument("test.xml")  
  
      Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
      xslt.Transform(xd, arg, strmTemp, Nothing)  
   End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XPathDocument Doc = new XPathDocument("books.xml");  
        XPathNavigator nav = Doc.CreateNavigator();  
        XPathNodeIterator Iterator = nav.Select("/bookstore/book");  
  
        XsltArgumentList arg = new XsltArgumentList();  
        arg.AddParam("param1", "", Iterator);  
  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, arg, strmTemp, null);  
    }  
}  
```  
  
## <a name="booksxml"></a><span data-ttu-id="bc39e-119">books.xml</span><span class="sxs-lookup"><span data-stu-id="bc39e-119">books.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database. -->  
<bookstore specialty="novel">  
    <book style="autobiography">  
    <title>Seven Years in Trenton</title>  
        <author>  
            <first-name>Jay</first-name>  
            <last-name>Adams</last-name>  
            <award>Trenton Literary Review Honorable Mention</award>  
            <country>USA</country>  
        </author>  
        <price>12</price>  
    </book>  
    <book style="textbook">  
        <title>History of Trenton</title>  
        <author>  
            <first-name>Kim</first-name>  
            <last-name>Akers</last-name>  
            <publication>  
                Selected Short Stories of  
                <first-name>Scott</first-name>  
                <last-name>Bishop</last-name>  
                <country>US</country>  
            </publication>  
        </author>  
        <price>55</price>  
    </book>  
</bookstore>  
```  
  
## <a name="testxsl"></a><span data-ttu-id="bc39e-120">test.xsl</span><span class="sxs-lookup"><span data-stu-id="bc39e-120">test.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
xmlns:msxsl="urn:schemas-microsoft-com:xslt" exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes"/>  
<xsl:param name="param1"/>  
  
<xsl:template match="/">  
    <out>  
        <xsl:for-each select="$param1/title">  
            <title><xsl:value-of select="."/></title>  
        </xsl:for-each>  
    </out>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a><span data-ttu-id="bc39e-121">test.xml</span><span class="sxs-lookup"><span data-stu-id="bc39e-121">test.xml</span></span>  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a><span data-ttu-id="bc39e-122">Sortie (out.xml)</span><span class="sxs-lookup"><span data-stu-id="bc39e-122">Output (out.xml)</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc39e-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc39e-123">See also</span></span>

- [<span data-ttu-id="bc39e-124">Implémentation du processeur XSLT par la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="bc39e-124">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
