---
title: Sérialisation avec une déclaration XML (C#)
description: Découvrez les configurations dans lesquelles la sérialisation en C# génère une déclaration XML, y compris la sérialisation vers un fichier, TextWriter et XmlWriter.
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 7e91b61f037d28149f7c2355f4233dc319b54627
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302358"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="b0c00-103">Sérialisation avec une déclaration XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b0c00-103">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="b0c00-104">Cette rubrique décrit comment contrôler si la sérialisation génère une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="b0c00-104">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="b0c00-105">Génération de déclaration XML</span><span class="sxs-lookup"><span data-stu-id="b0c00-105">XML Declaration Generation</span></span>  
 <span data-ttu-id="b0c00-106">La sérialisation vers un objet <xref:System.IO.File> ou <xref:System.IO.TextWriter> à l'aide de la méthode <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> ou <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>génère une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="b0c00-106">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="b0c00-107">Lorsque vous sérialisez vers un objet <xref:System.Xml.XmlWriter>, les paramètres de writer (spécifiés dans un objet <xref:System.Xml.XmlWriterSettings>) déterminent si une déclaration XML est générée ou non.</span><span class="sxs-lookup"><span data-stu-id="b0c00-107">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="b0c00-108">Si vous sérialisez vers une chaîne à l'aide de la méthode `ToString`, le code XML résultant n'inclura pas de déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="b0c00-108">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="b0c00-109">Sérialisation avec une déclaration XML</span><span class="sxs-lookup"><span data-stu-id="b0c00-109">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="b0c00-110">L'exemple suivant crée un objet <xref:System.Xml.Linq.XElement>, enregistre le document dans un fichier, puis imprime le fichier sur la console :</span><span class="sxs-lookup"><span data-stu-id="b0c00-110">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="b0c00-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b0c00-111">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="b0c00-112">Sérialisation sans déclaration XML</span><span class="sxs-lookup"><span data-stu-id="b0c00-112">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="b0c00-113">L'exemple suivant montre comment enregistrer un objet <xref:System.Xml.Linq.XElement> dans un objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="b0c00-113">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```csharp  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 <span data-ttu-id="b0c00-114">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b0c00-114">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0c00-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0c00-115">See also</span></span>

- [<span data-ttu-id="b0c00-116">Sérialisation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b0c00-116">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
