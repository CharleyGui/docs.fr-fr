---
title: 'Comment : modifier des littéraux XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 99ec35addcb9fc8d886c9151cde87227b5113eb9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330855"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="ec524-102">Comment : modifier des littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec524-102">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="ec524-103">Visual Basic provides convenient ways to modify XML literals.</span><span class="sxs-lookup"><span data-stu-id="ec524-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="ec524-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span><span class="sxs-lookup"><span data-stu-id="ec524-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="ec524-105">This topic provides several examples of how to modify an existing XML literal.</span><span class="sxs-lookup"><span data-stu-id="ec524-105">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="ec524-106">To modify the value of an XML literal</span><span class="sxs-lookup"><span data-stu-id="ec524-106">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="ec524-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span><span class="sxs-lookup"><span data-stu-id="ec524-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="ec524-108">The following code example updates the value of all the \<Price> elements in an XML document.</span><span class="sxs-lookup"><span data-stu-id="ec524-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="ec524-109">The following shows sample source XML and modified XML from this code example.</span><span class="sxs-lookup"><span data-stu-id="ec524-109">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="ec524-110">Source XML:</span><span class="sxs-lookup"><span data-stu-id="ec524-110">Source XML:</span></span>

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

    <span data-ttu-id="ec524-111">Modified XML:</span><span class="sxs-lookup"><span data-stu-id="ec524-111">Modified XML:</span></span>

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
    > <span data-ttu-id="ec524-112">The `Value` property refers to the first XML element in a collection.</span><span class="sxs-lookup"><span data-stu-id="ec524-112">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="ec524-113">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span><span class="sxs-lookup"><span data-stu-id="ec524-113">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="ec524-114">To add an attribute to an XML literal</span><span class="sxs-lookup"><span data-stu-id="ec524-114">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="ec524-115">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span><span class="sxs-lookup"><span data-stu-id="ec524-115">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="ec524-116">You can then add an attribute by adding a new XML attribute axis property.</span><span class="sxs-lookup"><span data-stu-id="ec524-116">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="ec524-117">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span><span class="sxs-lookup"><span data-stu-id="ec524-117">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="ec524-118">The following example shows both options.</span><span class="sxs-lookup"><span data-stu-id="ec524-118">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="ec524-119">The following shows sample source XML and modified XML from this code example.</span><span class="sxs-lookup"><span data-stu-id="ec524-119">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="ec524-120">Source XML:</span><span class="sxs-lookup"><span data-stu-id="ec524-120">Source XML:</span></span>

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

    <span data-ttu-id="ec524-121">Modified XML:</span><span class="sxs-lookup"><span data-stu-id="ec524-121">Modified XML:</span></span>

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

    <span data-ttu-id="ec524-122">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="ec524-122">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="ec524-123">To add an element to an XML literal</span><span class="sxs-lookup"><span data-stu-id="ec524-123">To add an element to an XML literal</span></span>

1. <span data-ttu-id="ec524-124">To add an element to an XML literal, first obtain a reference to the XML literal.</span><span class="sxs-lookup"><span data-stu-id="ec524-124">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="ec524-125">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span><span class="sxs-lookup"><span data-stu-id="ec524-125">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="ec524-126">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span><span class="sxs-lookup"><span data-stu-id="ec524-126">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="ec524-127">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span><span class="sxs-lookup"><span data-stu-id="ec524-127">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="ec524-128">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span><span class="sxs-lookup"><span data-stu-id="ec524-128">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="ec524-129">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span><span class="sxs-lookup"><span data-stu-id="ec524-129">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="ec524-130">The following example shows examples of each of these techniques.</span><span class="sxs-lookup"><span data-stu-id="ec524-130">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="ec524-131">The following shows sample source XML and modified XML from this code example.</span><span class="sxs-lookup"><span data-stu-id="ec524-131">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="ec524-132">Source XML:</span><span class="sxs-lookup"><span data-stu-id="ec524-132">Source XML:</span></span>

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

    <span data-ttu-id="ec524-133">Modified XML:</span><span class="sxs-lookup"><span data-stu-id="ec524-133">Modified XML:</span></span>

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

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="ec524-134">To remove an element or attribute from an XML literal</span><span class="sxs-lookup"><span data-stu-id="ec524-134">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="ec524-135">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="ec524-135">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="ec524-136">The following shows sample source XML and modified XML from this code example.</span><span class="sxs-lookup"><span data-stu-id="ec524-136">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="ec524-137">Source XML:</span><span class="sxs-lookup"><span data-stu-id="ec524-137">Source XML:</span></span>

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

    <span data-ttu-id="ec524-138">Modified XML:</span><span class="sxs-lookup"><span data-stu-id="ec524-138">Modified XML:</span></span>

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

    <span data-ttu-id="ec524-139">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span><span class="sxs-lookup"><span data-stu-id="ec524-139">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="ec524-140">To modify an XML literal</span><span class="sxs-lookup"><span data-stu-id="ec524-140">To modify an XML literal</span></span>

1. <span data-ttu-id="ec524-141">To change the name of an XML element, first obtain a reference to the element.</span><span class="sxs-lookup"><span data-stu-id="ec524-141">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="ec524-142">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span><span class="sxs-lookup"><span data-stu-id="ec524-142">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="ec524-143">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span><span class="sxs-lookup"><span data-stu-id="ec524-143">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="ec524-144">This will set the value of the new element to the inner XML of the existing element.</span><span class="sxs-lookup"><span data-stu-id="ec524-144">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="ec524-145">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span><span class="sxs-lookup"><span data-stu-id="ec524-145">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="ec524-146">The following code example replaces all \<Description> elements with an \<Abstract> element.</span><span class="sxs-lookup"><span data-stu-id="ec524-146">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="ec524-147">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span><span class="sxs-lookup"><span data-stu-id="ec524-147">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="ec524-148">The following shows sample source XML and modified XML from this code example.</span><span class="sxs-lookup"><span data-stu-id="ec524-148">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="ec524-149">Source XML:</span><span class="sxs-lookup"><span data-stu-id="ec524-149">Source XML:</span></span>

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

    <span data-ttu-id="ec524-150">Modified XML:</span><span class="sxs-lookup"><span data-stu-id="ec524-150">Modified XML:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ec524-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec524-151">See also</span></span>

- [<span data-ttu-id="ec524-152">Manipulation de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec524-152">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="ec524-153">XML</span><span class="sxs-lookup"><span data-stu-id="ec524-153">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="ec524-154">Guide pratique : charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux</span><span class="sxs-lookup"><span data-stu-id="ec524-154">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="ec524-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="ec524-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="ec524-156">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec524-156">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
