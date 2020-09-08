---
title: Vue d’ensemble de la classe XDocument
description: La classe LINQ to XML XDocument contient les informations nécessaires pour un document XML valide. Dans de nombreux cas, vous n’avez pas besoin de la fonctionnalité d’un objet XDocument et pouvez utiliser un objet XElement à la place.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: c26b7ac42733aad24d831f4a0a181e0fd8275eaf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552388"
---
# <a name="xdocument-class-overview"></a><span data-ttu-id="e5bc4-104">Vue d’ensemble de la classe XDocument</span><span class="sxs-lookup"><span data-stu-id="e5bc4-104">XDocument class overview</span></span>

<span data-ttu-id="e5bc4-105">La <xref:System.Xml.Linq.XDocument> classe contient les informations nécessaires pour un document XML valide, qui inclut une déclaration XML, des instructions de traitement et des commentaires.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document, which includes an XML declaration, processing instructions, and comments.</span></span>

<span data-ttu-id="e5bc4-106">Vous devez uniquement créer des <xref:System.Xml.Linq.XDocument> objets si vous avez besoin de la fonctionnalité spécifique fournie par la <xref:System.Xml.Linq.XDocument> classe.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-106">You only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="e5bc4-107">Dans de nombreux cas, vous pouvez travailler directement avec <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-107">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="e5bc4-108">L'utilisation directe de l'objet <xref:System.Xml.Linq.XElement> est un modèle de programmation plus simple.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-108">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>

<span data-ttu-id="e5bc4-109"><xref:System.Xml.Linq.XDocument> dérive de <xref:System.Xml.Linq.XContainer> , afin qu’il puisse contenir des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-109"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>, so it can contain child nodes.</span></span> <span data-ttu-id="e5bc4-110">Toutefois, les objets <xref:System.Xml.Linq.XDocument> ne peuvent avoir qu'un seul nœud <xref:System.Xml.Linq.XElement> enfant.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-110">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="e5bc4-111">Cela reflète la norme XML selon laquelle il ne doit y avoir qu'un seul élément racine dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-111">This reflects the XML standard that there can be only one root element in an XML document.</span></span>

## <a name="components-of-xdocument"></a><span data-ttu-id="e5bc4-112">Composants de XDocument</span><span class="sxs-lookup"><span data-stu-id="e5bc4-112">Components of XDocument</span></span>

<span data-ttu-id="e5bc4-113">Un objet <xref:System.Xml.Linq.XDocument> peut contenir les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e5bc4-113">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>

- <span data-ttu-id="e5bc4-114">Un objet <xref:System.Xml.Linq.XDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-114">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="e5bc4-115"><xref:System.Xml.Linq.XDeclaration> vous permet de spécifier les parties pertinentes d’une déclaration XML : la version XML, l’encodage du document et si le document XML est autonome.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-115"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is standalone.</span></span>
- <span data-ttu-id="e5bc4-116">Un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-116">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="e5bc4-117">Cet objet est le nœud racine du document XML.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-117">This object is the root node of the XML document.</span></span>
- <span data-ttu-id="e5bc4-118">Une quantité quelconque d'objets <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-118">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="e5bc4-119">Une instruction de traitement communique des informations à une application qui traite le code XML.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-119">A processing instruction communicates information to an application that processes the XML.</span></span>
- <span data-ttu-id="e5bc4-120">Une quantité quelconque d'objets <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-120">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="e5bc4-121">Les commentaires seront des frères de l'élément racine.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-121">The comments will be siblings to the root element.</span></span> <span data-ttu-id="e5bc4-122">L' <xref:System.Xml.Linq.XComment> objet ne peut pas être le premier argument de la liste, car il n’est pas valide pour qu’un document XML commence par un commentaire.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-122">The <xref:System.Xml.Linq.XComment> object can't be the first argument in the list, because it's not valid for an XML document to start with a comment.</span></span>
- <span data-ttu-id="e5bc4-123">Un objet <xref:System.Xml.Linq.XDocumentType> pour le DTD.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-123">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>

<span data-ttu-id="e5bc4-124">Lorsque vous sérialisez un objet <xref:System.Xml.Linq.XDocument>, même si `XDocument.Declaration` a la valeur `null`, la sortie aura une déclaration XML à condition que la propriété `Writer.Settings.OmitXmlDeclaration` du writer ait la valeur `false` (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="e5bc4-124">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>

<span data-ttu-id="e5bc4-125">Par défaut, LINQ to XML définit la version sur « 1,0 » et définit l’encodage sur « UTF-8 ».</span><span class="sxs-lookup"><span data-stu-id="e5bc4-125">By default, LINQ to XML sets the version to "1.0", and sets the encoding to "utf-8".</span></span>

## <a name="use-xelement-without-xdocument"></a><span data-ttu-id="e5bc4-126">Utiliser XElement sans XDocument</span><span class="sxs-lookup"><span data-stu-id="e5bc4-126">Use XElement without XDocument</span></span>

<span data-ttu-id="e5bc4-127">Comme mentionné précédemment, la <xref:System.Xml.Linq.XElement> classe est la classe principale dans l’interface de programmation LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-127">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the LINQ to XML programming interface.</span></span> <span data-ttu-id="e5bc4-128">Dans de nombreux cas, votre application ne nécessite pas la création d’un document.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-128">In many cases, your application won't require that you create a document.</span></span> <span data-ttu-id="e5bc4-129">À l’aide de la <xref:System.Xml.Linq.XElement> classe, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="e5bc4-129">By using the <xref:System.Xml.Linq.XElement> class, you can:</span></span>

- <span data-ttu-id="e5bc4-130">Créez une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-130">Create an XML tree.</span></span>
- <span data-ttu-id="e5bc4-131">Y ajouter d’autres arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-131">Add other XML trees to it.</span></span>
- <span data-ttu-id="e5bc4-132">Modifiez l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-132">Modify the XML tree.</span></span>
- <span data-ttu-id="e5bc4-133">Enregistrez-le.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-133">Save it.</span></span>

## <a name="use-xdocument"></a><span data-ttu-id="e5bc4-134">Utiliser XDocument</span><span class="sxs-lookup"><span data-stu-id="e5bc4-134">Use XDocument</span></span>

<span data-ttu-id="e5bc4-135">Pour construire un objet <xref:System.Xml.Linq.XDocument>, utilisez la construction fonctionnelle, comme pour construire des objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-135">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>

<span data-ttu-id="e5bc4-136">L’exemple suivant crée un <xref:System.Xml.Linq.XDocument> objet et ses objets contenus associés.</span><span class="sxs-lookup"><span data-stu-id="e5bc4-136">The following example creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>

```csharp
XDocument d = new XDocument(
    new XComment("This is a comment."),
    new XProcessingInstruction("xml-stylesheet",
        "href='mystyle.css' title='Compact' type='text/css'"),
    new XElement("Pubs",
        new XElement("Book",
            new XElement("Title", "Artifacts of Roman Civilization"),
            new XElement("Author", "Moreno, Jordao")
        ),
        new XElement("Book",
            new XElement("Title", "Midieval Tools and Implements"),
            new XElement("Author", "Gazit, Inbar")
        )
    ),
    new XComment("This is another comment.")
);
d.Declaration = new XDeclaration("1.0", "utf-8", "true");
Console.WriteLine(d);

d.Save("test.xml");
```

```vb
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>
                       <!--This is a comment.-->
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>
                       <Pubs>
                           <Book>
                               <Title>Artifacts of Roman Civilization</Title>
                               <Author>Moreno, Jordao</Author>
                           </Book>
                           <Book>
                               <Title>Midieval Tools and Implements</Title>
                               <Author>Gazit, Inbar</Author>
                           </Book>
                       </Pubs>
                       <!--This is another comment.-->
doc.Save("test.xml")
```

<span data-ttu-id="e5bc4-137">L’exemple génère cette sortie dans test.xml :</span><span class="sxs-lookup"><span data-stu-id="e5bc4-137">The example produces this output in test.xml:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--This is a comment.-->
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>
<Pubs>
  <Book>
    <Title>Artifacts of Roman Civilization</Title>
    <Author>Moreno, Jordao</Author>
  </Book>
  <Book>
    <Title>Midieval Tools and Implements</Title>
    <Author>Gazit, Inbar</Author>
  </Book>
</Pubs>
<!--This is another comment.-->
```

## <a name="see-also"></a><span data-ttu-id="e5bc4-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5bc4-138">See also</span></span>

- [<span data-ttu-id="e5bc4-139">Présentation de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="e5bc4-139">LINQ to XML overview</span></span>](linq-xml-overview.md)
