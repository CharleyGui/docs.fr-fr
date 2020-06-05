---
title: 'Comment : modifier des littéraux XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: a2ac2e9802d4c8ab522bb430d15cce5616430437
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374873"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="785f7-102">Comment : modifier des littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="785f7-102">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="785f7-103">Visual Basic fournit des méthodes pratiques pour modifier des littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="785f7-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="785f7-104">Vous pouvez ajouter ou supprimer des éléments et des attributs, et vous pouvez également remplacer un élément existant par un nouvel élément XML.</span><span class="sxs-lookup"><span data-stu-id="785f7-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="785f7-105">Cette rubrique fournit plusieurs exemples de modification d’un littéral XML existant.</span><span class="sxs-lookup"><span data-stu-id="785f7-105">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="785f7-106">Pour modifier la valeur d’un littéral XML</span><span class="sxs-lookup"><span data-stu-id="785f7-106">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="785f7-107">Pour modifier la valeur d’un littéral XML, obtenez une référence au littéral XML et affectez `Value` à la propriété la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="785f7-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="785f7-108">L’exemple de code suivant met à jour la valeur de tous les \<Price> éléments d’un document XML.</span><span class="sxs-lookup"><span data-stu-id="785f7-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="785f7-109">L’exemple suivant montre des exemples de code source XML et des données XML modifiées à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="785f7-109">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="785f7-110">XML source :</span><span class="sxs-lookup"><span data-stu-id="785f7-110">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="785f7-111">XML modifié :</span><span class="sxs-lookup"><span data-stu-id="785f7-111">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>47.20</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>48.25</Price>
      </Book>
    </Catalog>
    ```

    > [!NOTE]
    > <span data-ttu-id="785f7-112">La `Value` propriété fait référence au premier élément XML d’une collection.</span><span class="sxs-lookup"><span data-stu-id="785f7-112">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="785f7-113">Si plusieurs éléments ont le même nom dans une collection, la définition de la `Value` propriété affecte uniquement le premier élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="785f7-113">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="785f7-114">Pour ajouter un attribut à un littéral XML</span><span class="sxs-lookup"><span data-stu-id="785f7-114">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="785f7-115">Pour ajouter un attribut à un littéral XML, commencez par obtenir une référence au littéral XML.</span><span class="sxs-lookup"><span data-stu-id="785f7-115">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="785f7-116">Vous pouvez ensuite ajouter un attribut en ajoutant une nouvelle propriété d’axe d’attribut XML.</span><span class="sxs-lookup"><span data-stu-id="785f7-116">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="785f7-117">Vous pouvez également ajouter un nouvel <xref:System.Xml.Linq.XAttribute> objet au LITTÉRAL XML à l’aide de la <xref:System.Xml.Linq.XContainer.Add%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="785f7-117">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="785f7-118">L’exemple suivant illustre les deux options.</span><span class="sxs-lookup"><span data-stu-id="785f7-118">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="785f7-119">L’exemple suivant montre des exemples de code source XML et des données XML modifiées à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="785f7-119">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="785f7-120">XML source :</span><span class="sxs-lookup"><span data-stu-id="785f7-120">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="785f7-121">XML modifié :</span><span class="sxs-lookup"><span data-stu-id="785f7-121">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="785f7-122">Pour plus d’informations sur les propriétés d’axe d’attribut XML, consultez [propriété d’axe d’attribut XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="785f7-122">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="785f7-123">Pour ajouter un élément à un littéral XML</span><span class="sxs-lookup"><span data-stu-id="785f7-123">To add an element to an XML literal</span></span>

1. <span data-ttu-id="785f7-124">Pour ajouter un élément à un littéral XML, commencez par obtenir une référence au littéral XML.</span><span class="sxs-lookup"><span data-stu-id="785f7-124">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="785f7-125">Vous pouvez ensuite ajouter un nouvel <xref:System.Xml.Linq.XElement> objet en tant que dernier sous-élément de l’élément à l’aide de la <xref:System.Xml.Linq.XContainer.Add%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="785f7-125">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="785f7-126">Vous pouvez ajouter un nouvel <xref:System.Xml.Linq.XElement> objet en tant que premier sous-élément à l’aide de la <xref:System.Xml.Linq.XContainer.AddFirst%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="785f7-126">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="785f7-127">Pour ajouter un nouvel élément à un emplacement spécifique par rapport à d’autres sous-éléments, commencez par obtenir une référence à un sous-élément adjacent.</span><span class="sxs-lookup"><span data-stu-id="785f7-127">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="785f7-128">Vous pouvez ensuite ajouter le nouvel <xref:System.Xml.Linq.XElement> objet avant le sous-élément adjacent à l’aide de la <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="785f7-128">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="785f7-129">Vous pouvez également ajouter le nouvel <xref:System.Xml.Linq.XElement> objet après le sous-élément adjacent à l’aide de la <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="785f7-129">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="785f7-130">L’exemple suivant montre des exemples de chacune de ces techniques.</span><span class="sxs-lookup"><span data-stu-id="785f7-130">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="785f7-131">L’exemple suivant montre des exemples de code source XML et des données XML modifiées à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="785f7-131">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="785f7-132">XML source :</span><span class="sxs-lookup"><span data-stu-id="785f7-132">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="785f7-133">XML modifié :</span><span class="sxs-lookup"><span data-stu-id="785f7-133">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331">
        <Publisher>Microsoft Press</Publisher>
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <PublishDate>2005-2-14</PublishDate>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="785f7-134">Pour supprimer un élément ou un attribut d’un littéral XML</span><span class="sxs-lookup"><span data-stu-id="785f7-134">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="785f7-135">Pour supprimer un élément ou un attribut d’un littéral XML, obtenez une référence à l’élément ou à l’attribut et appelez la `Remove` méthode, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="785f7-135">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="785f7-136">L’exemple suivant montre des exemples de code source XML et des données XML modifiées à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="785f7-136">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="785f7-137">XML source :</span><span class="sxs-lookup"><span data-stu-id="785f7-137">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

    <span data-ttu-id="785f7-138">XML modifié :</span><span class="sxs-lookup"><span data-stu-id="785f7-138">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book></Catalog>
    ```

    <span data-ttu-id="785f7-139">Pour supprimer tous les éléments ou attributs d’un littéral XML, obtenez une référence au littéral XML et appelez la <xref:System.Xml.Linq.XElement.RemoveAll%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="785f7-139">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="785f7-140">Pour modifier un littéral XML</span><span class="sxs-lookup"><span data-stu-id="785f7-140">To modify an XML literal</span></span>

1. <span data-ttu-id="785f7-141">Pour modifier le nom d’un élément XML, obtenez d’abord une référence à l’élément.</span><span class="sxs-lookup"><span data-stu-id="785f7-141">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="785f7-142">Vous pouvez ensuite créer un nouvel <xref:System.Xml.Linq.XElement> objet avec un nouveau nom et passer le nouvel <xref:System.Xml.Linq.XElement> objet à la <xref:System.Xml.Linq.XNode.ReplaceWith%2A> méthode de l’objet existant <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="785f7-142">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="785f7-143">Si l’élément que vous remplacez contient des sous-éléments qui doivent être conservés, affectez la valeur du nouvel <xref:System.Xml.Linq.XElement> objet à la <xref:System.Xml.Linq.XContainer.Nodes%2A> propriété de l’élément existant.</span><span class="sxs-lookup"><span data-stu-id="785f7-143">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="785f7-144">La valeur du nouvel élément est alors définie sur le code XML interne de l’élément existant.</span><span class="sxs-lookup"><span data-stu-id="785f7-144">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="785f7-145">Sinon, vous pouvez définir la valeur du nouvel élément sur la `Value` propriété de l’élément existant.</span><span class="sxs-lookup"><span data-stu-id="785f7-145">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="785f7-146">L’exemple de code suivant remplace tous les \<Description> éléments par un \<Abstract> élément.</span><span class="sxs-lookup"><span data-stu-id="785f7-146">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="785f7-147">Le contenu de l' \<Description> élément est conservé dans le nouvel \<Abstract> élément à l’aide <xref:System.Xml.Linq.XContainer.Nodes%2A> de la propriété de l' \<Description> <xref:System.Xml.Linq.XElement> objet.</span><span class="sxs-lookup"><span data-stu-id="785f7-147">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="785f7-148">L’exemple suivant montre des exemples de code source XML et des données XML modifiées à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="785f7-148">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="785f7-149">XML source :</span><span class="sxs-lookup"><span data-stu-id="785f7-149">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
        <Description>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Description>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <Description>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Description>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="785f7-150">XML modifié :</span><span class="sxs-lookup"><span data-stu-id="785f7-150">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <MSRP>44.95</MSRP>    <Abstract>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Abstract>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <MSRP>45.95</MSRP>    <Abstract>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Abstract>
      </Book>
    </Catalog>
    ```

## <a name="see-also"></a><span data-ttu-id="785f7-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="785f7-151">See also</span></span>

- [<span data-ttu-id="785f7-152">Manipulation de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="785f7-152">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
- [<span data-ttu-id="785f7-153">XML</span><span class="sxs-lookup"><span data-stu-id="785f7-153">XML</span></span>](index.md)
- [<span data-ttu-id="785f7-154">Guide pratique : charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux</span><span class="sxs-lookup"><span data-stu-id="785f7-154">How to: Load XML from a File, String, or Stream</span></span>](how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="785f7-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="785f7-155">LINQ</span></span>](../linq/index.md)
- [<span data-ttu-id="785f7-156">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="785f7-156">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
