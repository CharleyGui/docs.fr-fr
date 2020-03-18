---
title: Vue d’ensemble de la classe XDocument (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: de49dc071d22dd77dddea29ca114663261e3edda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590847"
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="90256-102">Vue d’ensemble de la classe XDocument (C#)</span><span class="sxs-lookup"><span data-stu-id="90256-102">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="90256-103">Cette rubrique présente la classe <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="90256-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="90256-104">Vue d'ensemble de la classe XDocument</span><span class="sxs-lookup"><span data-stu-id="90256-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="90256-105">La classe <xref:System.Xml.Linq.XDocument> contient les informations nécessaires pour un document XML valide.</span><span class="sxs-lookup"><span data-stu-id="90256-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="90256-106">Cela inclut une déclaration XML, des instructions de traitement et des commentaires.</span><span class="sxs-lookup"><span data-stu-id="90256-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="90256-107">Notez que la création d'objets <xref:System.Xml.Linq.XDocument> est nécessaire uniquement si vous avez besoin de la fonctionnalité spécifique fournie par la classe <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="90256-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="90256-108">Dans de nombreux cas, vous pouvez travailler directement avec <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="90256-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="90256-109">L'utilisation directe de l'objet <xref:System.Xml.Linq.XElement> est un modèle de programmation plus simple.</span><span class="sxs-lookup"><span data-stu-id="90256-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="90256-110"><xref:System.Xml.Linq.XDocument> dérive de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="90256-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="90256-111">Par conséquent, il peut contenir des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="90256-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="90256-112">Toutefois, les objets <xref:System.Xml.Linq.XDocument> ne peuvent avoir qu'un seul nœud <xref:System.Xml.Linq.XElement> enfant.</span><span class="sxs-lookup"><span data-stu-id="90256-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="90256-113">Cela reflète la norme XML selon laquelle il ne doit y avoir qu'un seul élément racine dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="90256-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="90256-114">Composants de XDocument</span><span class="sxs-lookup"><span data-stu-id="90256-114">Components of XDocument</span></span>  
 <span data-ttu-id="90256-115">Un objet <xref:System.Xml.Linq.XDocument> peut contenir les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="90256-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="90256-116">Un objet <xref:System.Xml.Linq.XDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="90256-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="90256-117"><xref:System.Xml.Linq.XDeclaration> vous permet de spécifier les parties pertinentes d'une déclaration XML : la version XML, l'encodage du document et si le document XML est autonome.</span><span class="sxs-lookup"><span data-stu-id="90256-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="90256-118">Un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="90256-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="90256-119">Il s'agit du nœud racine du document XML.</span><span class="sxs-lookup"><span data-stu-id="90256-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="90256-120">Une quantité quelconque d'objets <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="90256-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="90256-121">Une instruction de traitement communique des informations à une application qui traite le code XML.</span><span class="sxs-lookup"><span data-stu-id="90256-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="90256-122">Une quantité quelconque d'objets <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="90256-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="90256-123">Les commentaires seront des frères de l'élément racine.</span><span class="sxs-lookup"><span data-stu-id="90256-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="90256-124">L'objet <xref:System.Xml.Linq.XComment> ne peut pas être le premier argument de la liste, car un document XML valide ne peut pas commencer par un commentaire.</span><span class="sxs-lookup"><span data-stu-id="90256-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="90256-125">Un objet <xref:System.Xml.Linq.XDocumentType> pour le DTD.</span><span class="sxs-lookup"><span data-stu-id="90256-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="90256-126">Lorsque vous sérialisez un objet <xref:System.Xml.Linq.XDocument>, même si `XDocument.Declaration` a la valeur `null`, la sortie aura une déclaration XML à condition que la propriété `Writer.Settings.OmitXmlDeclaration` du writer ait la valeur `false` (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="90256-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="90256-127">Par défaut, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] définit la version à « 1.0 » l'encodage à « utf-8 ».</span><span class="sxs-lookup"><span data-stu-id="90256-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="90256-128">Utilisation de XElement sans XDocument</span><span class="sxs-lookup"><span data-stu-id="90256-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="90256-129">Comme mentionné précédemment, la classe <xref:System.Xml.Linq.XElement> est la classe principale dans l'interface de programmation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="90256-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="90256-130">Dans de nombreux cas, votre application ne nécessitera pas la création d'un document.</span><span class="sxs-lookup"><span data-stu-id="90256-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="90256-131">L'utilisation de la classe <xref:System.Xml.Linq.XElement> vous permet de créer une arborescence XML, de la modifier, de l'enregistrer et d'y ajouter d'autres arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="90256-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="90256-132">Utilisation de XDocument</span><span class="sxs-lookup"><span data-stu-id="90256-132">Using XDocument</span></span>  
 <span data-ttu-id="90256-133">Pour construire un objet <xref:System.Xml.Linq.XDocument>, utilisez la construction fonctionnelle, comme pour construire des objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="90256-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="90256-134">Le code suivant crée un objet <xref:System.Xml.Linq.XDocument> et ses objets contenus associés.</span><span class="sxs-lookup"><span data-stu-id="90256-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="90256-135">Lorsque vous examinez le fichier test.xml, vous obtenez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="90256-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90256-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90256-136">See also</span></span>

- [<span data-ttu-id="90256-137">Vue d’ensemble de la programmation LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="90256-137">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
