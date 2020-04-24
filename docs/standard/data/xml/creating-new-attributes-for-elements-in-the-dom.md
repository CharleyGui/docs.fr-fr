---
title: Création de nouveaux attributs pour des éléments du DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
ms.openlocfilehash: 79a3390933256ed862d35c90db0aab2177cdfc41
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711010"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="b0836-102">Création de nouveaux attributs pour des éléments du DOM</span><span class="sxs-lookup"><span data-stu-id="b0836-102">Creating New Attributes for Elements in the DOM</span></span>

<span data-ttu-id="b0836-103">La création de nouveaux attributs diffère de la création d'autres types de nœud, car les attributs ne sont pas des nœuds, mais des propriétés d'un nœud d'élément, et appartiennent à un **XmlAttributeCollection** associé à cet élément.</span><span class="sxs-lookup"><span data-stu-id="b0836-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="b0836-104">Il existe plusieurs manières de créer un attribut et de le joindre à un élément :</span><span class="sxs-lookup"><span data-stu-id="b0836-104">There are multiple ways to create an attribute and attach it to an element:</span></span>

- <span data-ttu-id="b0836-105">Obtenir le nœud d’élément et utiliser **SetAttribute** pour ajouter un attribut à la collection d’attributs de cet élément</span><span class="sxs-lookup"><span data-stu-id="b0836-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>

- <span data-ttu-id="b0836-106">Créer un nœud **XmlAttribute** à l’aide de la méthode **CreateAttribute**, obtenir le nœud d’élément, puis utiliser **SetAttributeNode** pour ajouter le nœud à la collection d’attributs de cet élément</span><span class="sxs-lookup"><span data-stu-id="b0836-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>

<span data-ttu-id="b0836-107">L’exemple suivant montre comment ajouter un attribut à un élément à l’aide de la méthode **setAttribute** :</span><span class="sxs-lookup"><span data-stu-id="b0836-107">The following example shows how to add an attribute to an element using the **SetAttribute** method:</span></span>

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As New XmlDocument()
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _
                    "<title>Pride And Prejudice</title>" & _
                    "</book>")
        Dim root As XmlElement = doc.DocumentElement

        ' Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel")

        Console.WriteLine("Display the modified XML...")
        Console.WriteLine(doc.InnerXml)
    End Sub
End Class
```  
  
```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{
    public static void Main()
    {
        var doc = new XmlDocument();
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +
                    "<title>Pride And Prejudice</title>" +
                    "</book>");
        XmlElement root = doc.DocumentElement;

        // Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel");

        Console.WriteLine("Display the modified XML...");
        Console.WriteLine(doc.InnerXml);
    }
}
```

<span data-ttu-id="b0836-108">L'exemple suivant illustre la création d'un nouvel attribut à l'aide de la méthode **CreateAttribute**.</span><span class="sxs-lookup"><span data-stu-id="b0836-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="b0836-109">Il affiche ensuite l’attribut ajouté à la collection d’attributs de l’élément **book** à l’aide de la méthode **SetAttributeNode**.</span><span class="sxs-lookup"><span data-stu-id="b0836-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>

<span data-ttu-id="b0836-110">En partant du code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="b0836-110">Given the following XML:</span></span>
  
```xml
<book genre='novel' ISBN='1-861001-57-5'>
<title>Pride And Prejudice</title>
</book>
```

<span data-ttu-id="b0836-111">créez un nouvel attribut et attribuez-lui une valeur :</span><span class="sxs-lookup"><span data-stu-id="b0836-111">create a new attribute and give it a value:</span></span>

```vb
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")
attr.Value = "WorldWide Publishing"
```

```csharp
XmlAttribute attr = doc.CreateAttribute("publisher");
attr.Value = "WorldWide Publishing";
```

<span data-ttu-id="b0836-112">Puis, joignez-le à l'élément :</span><span class="sxs-lookup"><span data-stu-id="b0836-112">and attach it to the element:</span></span>

```vb
doc.DocumentElement.SetAttributeNode(attr)
```

```csharp
doc.DocumentElement.SetAttributeNode(attr);
```

<span data-ttu-id="b0836-113">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="b0836-113">**Output**</span></span>

```xml
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">
<title>Pride And Prejudice</title>
</book>
```

<span data-ttu-id="b0836-114">Pour obtenir l’exemple de code complet, consultez <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0836-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>

<span data-ttu-id="b0836-115">Vous pouvez également créer un nœud **XmlAttribute** et utiliser la méthode **InsertBefore** ou **InsertAfter** pour le placer à la position voulue dans la collection.</span><span class="sxs-lookup"><span data-stu-id="b0836-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="b0836-116">Si un attribut de même nom figure déjà dans la collection d’attributs, le nœud **XmlAttribute** existant est supprimé de la collection et le nouveau nœud **XmlAttribute** est inséré.</span><span class="sxs-lookup"><span data-stu-id="b0836-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="b0836-117">Ce comportement est le même qu'avec la méthode **SetAttribute**.</span><span class="sxs-lookup"><span data-stu-id="b0836-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="b0836-118">Ces méthodes prennent comme paramètre un nœud existant comme point de référence pour réaliser les opérations **InsertBefore** et **InsertAfter**.</span><span class="sxs-lookup"><span data-stu-id="b0836-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="b0836-119">Si vous ne fournissez pas de nœud de référence indiquant la position d’insertion du nouveau nœud, la méthode **InsertAfter**, par défaut, place ce dernier au début de la collection.</span><span class="sxs-lookup"><span data-stu-id="b0836-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="b0836-120">Pour la méthode **InsertBefore**, la position par défaut si aucun nœud de référence n’est fourni est la fin de la collection.</span><span class="sxs-lookup"><span data-stu-id="b0836-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>

<span data-ttu-id="b0836-121">Si vous avez créé un **XmlNamedNodeMap** d’attributs, vous pouvez ajouter un attribut par nom à <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A> l’aide de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b0836-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A> method.</span></span> <span data-ttu-id="b0836-122">Pour plus d’informations, consultez [Collections de nœuds dans NamedNodeMap et NodeList](node-collections-in-namednodemaps-and-nodelists.md).</span><span class="sxs-lookup"><span data-stu-id="b0836-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](node-collections-in-namednodemaps-and-nodelists.md).</span></span>

## <a name="default-attributes"></a><span data-ttu-id="b0836-123">Attributs par défaut</span><span class="sxs-lookup"><span data-stu-id="b0836-123">Default attributes</span></span>

<span data-ttu-id="b0836-124">Si vous créez un élément déclaré comme possédant un attribut par défaut, un nouvel attribut par défaut avec sa valeur par défaut est créé par le DOM (Document Object Model) XML et joint à cet élément.</span><span class="sxs-lookup"><span data-stu-id="b0836-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="b0836-125">Les nœuds enfants de l'attribut par défaut sont également créés en même temps.</span><span class="sxs-lookup"><span data-stu-id="b0836-125">The child nodes of the default attribute are also created at this time.</span></span>

## <a name="attribute-child-nodes"></a><span data-ttu-id="b0836-126">Nœuds enfants d’attribut</span><span class="sxs-lookup"><span data-stu-id="b0836-126">Attribute child nodes</span></span>

<span data-ttu-id="b0836-127">La valeur d'un nœud d'attribut devient ses nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="b0836-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="b0836-128">Il n’existe que deux types de nœuds enfants valides : les nœuds **XmlText** et les nœuds **XmlEntityReference** .</span><span class="sxs-lookup"><span data-stu-id="b0836-128">There are only two types of valid child nodes: **XmlText** nodes and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="b0836-129">Ces nœuds sont des nœuds enfants, en ce sens que des méthodes telles que **FirstChild** et **LastChild** les traitent comme tels.</span><span class="sxs-lookup"><span data-stu-id="b0836-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="b0836-130">Cette distinction qui caractérise un attribut possédant des nœuds enfants est importante lorsque vous tentez de supprimer des attributs ou des nœuds enfants d'attribut.</span><span class="sxs-lookup"><span data-stu-id="b0836-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="b0836-131">Pour plus d'informations, consultez [Suppression d'attributs d'un nœud d'élément dans le DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="b0836-131">For more information, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0836-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0836-132">See also</span></span>

- [<span data-ttu-id="b0836-133">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="b0836-133">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
