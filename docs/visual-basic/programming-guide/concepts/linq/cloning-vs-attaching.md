---
title: Clonage et attachement
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: aaf3344c0439d96a01006ee000d0a827884a5af9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410875"
---
# <a name="cloning-vs-attaching-visual-basic"></a><span data-ttu-id="6ca78-102">Clonage et attachement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ca78-102">Cloning vs. Attaching (Visual Basic)</span></span>
<span data-ttu-id="6ca78-103">Lors de l'ajout d'objets <xref:System.Xml.Linq.XNode> (y compris <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, si le contenu n'a pas de parent, les objets sont simplement attachés à l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="6ca78-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="6ca78-104">Si le nouveau contenu a déjà un parent et fait partie d'une autre arborescence XML, il est cloné.</span><span class="sxs-lookup"><span data-stu-id="6ca78-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="6ca78-105">Le nouveau contenu cloné est alors attaché à l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="6ca78-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ca78-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="6ca78-106">Example</span></span>  
 <span data-ttu-id="6ca78-107">Le code suivant illustre le comportement lorsque vous ajoutez un élément apparenté à une arborescence et lorsque vous ajoutez un élément non apparenté à une arborescence.</span><span class="sxs-lookup"><span data-stu-id="6ca78-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="6ca78-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6ca78-108">This example produces the following output:</span></span>  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ca78-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ca78-109">See also</span></span>

- [<span data-ttu-id="6ca78-110">Création d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ca78-110">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
