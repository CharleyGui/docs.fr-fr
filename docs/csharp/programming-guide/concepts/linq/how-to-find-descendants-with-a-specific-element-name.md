---
title: 'Procédure : Rechercher les descendants avec un nom d’élément spécifique (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: c54b3c6a01459781b8ed9d5495bf9eb8937363fa
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486751"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="154b1-102">Procédure : Rechercher les descendants avec un nom d’élément spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="154b1-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="154b1-103">Parfois, vous souhaitez rechercher tous les descendants avec un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="154b1-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="154b1-104">Vous pourriez écrire du code pour itérer au sein de tous les descendants, mais il est plus facile d'utiliser l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="154b1-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="154b1-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="154b1-105">Example</span></span>  
 <span data-ttu-id="154b1-106">L'exemple suivant montre comment rechercher des descendants en fonction du nom d'élément.</span><span class="sxs-lookup"><span data-stu-id="154b1-106">The following example shows how to find descendants based on the element name.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
IEnumerable<string> textSegs =  
    from seg in root.Descendants("t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="154b1-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="154b1-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="154b1-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="154b1-108">Example</span></span>  
 <span data-ttu-id="154b1-109">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="154b1-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="154b1-110">Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="154b1-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root xmlns='http://www.adatum.com'>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<string> textSegs =  
    from seg in root.Descendants(ad + "t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="154b1-111">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="154b1-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="154b1-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="154b1-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
