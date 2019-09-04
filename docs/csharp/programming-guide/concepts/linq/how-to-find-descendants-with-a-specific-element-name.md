---
title: 'Procédure : Rechercher les descendants avec un nom d’élément spécifique (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 8c859c555109a6f68a6b4290c536b10114620f3d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253697"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="4a671-102">Procédure : Rechercher les descendants avec un nom d’élément spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="4a671-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="4a671-103">Parfois, vous souhaitez rechercher tous les descendants avec un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="4a671-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="4a671-104">Vous pourriez écrire du code pour itérer au sein de tous les descendants, mais il est plus facile d'utiliser l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a671-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a671-105">Exemples</span><span class="sxs-lookup"><span data-stu-id="4a671-105">Example</span></span>  
 <span data-ttu-id="4a671-106">L'exemple suivant montre comment rechercher des descendants en fonction du nom d'élément.</span><span class="sxs-lookup"><span data-stu-id="4a671-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="4a671-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4a671-107">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="4a671-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="4a671-108">Example</span></span>  
 <span data-ttu-id="4a671-109">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4a671-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="4a671-110">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4a671-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="4a671-111">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4a671-111">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a671-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a671-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
