---
title: "Comment : transformer du code XML à l'aide de LINQ"
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: dab394ec45567589e002b5d2ac76ec19fb0f76c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374880"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="b4909-102">Comment : transformer du code XML à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4909-102">How to: Transform XML by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="b4909-103">Les [littéraux XML](../../../language-reference/xml-literals/index.md) facilitent la lecture des données XML à partir d’une source et leur transformation dans un nouveau format XML.</span><span class="sxs-lookup"><span data-stu-id="b4909-103">[XML Literals](../../../language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="b4909-104">Vous pouvez tirer parti des requêtes LINQ pour récupérer le contenu à transformer ou modifier le contenu d’un document existant en un nouveau format XML.</span><span class="sxs-lookup"><span data-stu-id="b4909-104">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>

<span data-ttu-id="b4909-105">L’exemple de cette rubrique transforme le contenu d’un document source XML en HTML à afficher dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="b4909-105">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-transform-an-xml-document"></a><span data-ttu-id="b4909-106">Pour transformer un document XML</span><span class="sxs-lookup"><span data-stu-id="b4909-106">To transform an XML document</span></span>

1. <span data-ttu-id="b4909-107">Dans Visual Studio, créez un projet de Visual Basic dans le modèle de projet d' **application console** .</span><span class="sxs-lookup"><span data-stu-id="b4909-107">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>

2. <span data-ttu-id="b4909-108">Double-cliquez sur le fichier Module1. vb créé dans le projet pour modifier le code d’Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b4909-108">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="b4909-109">Ajoutez le code suivant à l' `Sub Main` du `Module1` module.</span><span class="sxs-lookup"><span data-stu-id="b4909-109">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="b4909-110">Ce code crée le document XML source en tant qu' <xref:System.Xml.Linq.XDocument> objet.</span><span class="sxs-lookup"><span data-stu-id="b4909-110">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>

    ```vb
    Dim catalog =
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
              Get the expert insights, practical code samples,
              and best practices you need
              to advance your expertise with <technology>Visual
              Basic .NET</technology>.
              Learn how to create faster, more reliable applications
              based on professional,
              pragmatic guidance by today's top <audience>developers</audience>.
            </Description>
          </Book>
        </Catalog>
    ```

     <span data-ttu-id="b4909-111">[Comment : charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux](how-to-load-xml-from-a-file-string-or-stream.md).</span><span class="sxs-lookup"><span data-stu-id="b4909-111">[How to: Load XML from a File, String, or Stream](how-to-load-xml-from-a-file-string-or-stream.md).</span></span>

3. <span data-ttu-id="b4909-112">Après le code pour créer le document XML source, ajoutez le code suivant pour récupérer tous les \<Book> éléments de l’objet et les transformer en un document HTML.</span><span class="sxs-lookup"><span data-stu-id="b4909-112">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="b4909-113">La liste des \<Book> éléments est créée à l’aide d’une requête LINQ qui retourne une collection d' <xref:System.Xml.Linq.XElement> objets qui contiennent le code html transformé.</span><span class="sxs-lookup"><span data-stu-id="b4909-113">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="b4909-114">Vous pouvez utiliser des expressions incorporées pour placer les valeurs du document source au nouveau format XML.</span><span class="sxs-lookup"><span data-stu-id="b4909-114">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>

     <span data-ttu-id="b4909-115">Le document HTML obtenu est écrit dans un fichier à l’aide de la <xref:System.Xml.Linq.XElement.Save%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="b4909-115">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>

    ```vb
    Dim htmlOutput =
      <html>
        <body>
          <%= From book In catalog.<Catalog>.<Book>
              Select <div>
                       <h1><%= book.<Title>.Value %></h1>
                       <h3><%= "By " & book.<Author>.Value %></h3>
                        <h3><%= "Price = " & book.<Price>.Value %></h3>
                        <h2>Description</h2>
                        <%= TransformDescription(book.<Description>(0)) %>
                        <hr/>
                      </div> %>
        </body>
      </html>

    htmlOutput.Save("BookDescription.html")
    ```

4. <span data-ttu-id="b4909-116">Après `Sub Main` `Module1` , ajoutez une nouvelle méthode ( `Sub` ) pour transformer un \<Description> nœud dans le format HTML spécifié.</span><span class="sxs-lookup"><span data-stu-id="b4909-116">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="b4909-117">Cette méthode est appelée par le code de l’étape précédente et est utilisée pour conserver le format des \<Description> éléments.</span><span class="sxs-lookup"><span data-stu-id="b4909-117">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>

     <span data-ttu-id="b4909-118">Cette méthode remplace les sous-éléments de l' \<Description> élément par du code html.</span><span class="sxs-lookup"><span data-stu-id="b4909-118">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="b4909-119">La `ReplaceWith` méthode est utilisée pour conserver l’emplacement des sous-éléments.</span><span class="sxs-lookup"><span data-stu-id="b4909-119">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="b4909-120">Le contenu transformé de l' \<Description> élément est inclus dans un élément paragraph ( \<p> ) html.</span><span class="sxs-lookup"><span data-stu-id="b4909-120">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="b4909-121">La <xref:System.Xml.Linq.XContainer.Nodes%2A> propriété est utilisée pour récupérer le contenu transformé de l' \<Description> élément.</span><span class="sxs-lookup"><span data-stu-id="b4909-121">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="b4909-122">Cela permet de s’assurer que les sous-éléments sont inclus dans le contenu transformé.</span><span class="sxs-lookup"><span data-stu-id="b4909-122">This ensures that sub-elements are included in the transformed content.</span></span>

     <span data-ttu-id="b4909-123">Ajoutez le code suivant après `Sub Main` `Module1` .</span><span class="sxs-lookup"><span data-stu-id="b4909-123">Add the following code after `Sub Main` of `Module1`.</span></span>

    ```vb
    Public Function TransformDescription(ByVal desc As XElement) As XElement

      ' Replace <technology> elements with <b>.
      Dim content = (From element In desc...<technology>).ToList()

      If content.Count > 0 Then
        For i = 0 To content.Count - 1
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)
        Next
      End If

      ' Replace <audience> elements with <i>.
      content = (From element In desc...<audience>).ToList()

      If content.Count > 0 Then
        For i = 0 To content.Count - 1
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)
        Next
      End If

      ' Return the updated contents of the <Description> element.
      Return <p><%= desc.Nodes %></p>
    End Function
    ```

5. <span data-ttu-id="b4909-124">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="b4909-124">Save your changes.</span></span>

6. <span data-ttu-id="b4909-125">Appuyez sur F5 pour exécuter le code.</span><span class="sxs-lookup"><span data-stu-id="b4909-125">Press F5 to run the code.</span></span> <span data-ttu-id="b4909-126">Le document enregistré résultant ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="b4909-126">The resulting saved document will resemble the following:</span></span>

    ```html
    <?xml version="1.0"?>
    <html>
      <body>
        <div>
          <h1>XML Developer's Guide</h1>
          <h3>By Garghentini, Davide</h3>
          <h3>Price = 44.95</h3>
          <h2>Description</h2>
          <p>
            An in-depth look at creating applications
            with <b>XML</b>. For
            <i>beginners</i> or
            <i>advanced</i> developers.
          </p>
          <hr />
        </div>
        <div>
          <h1>Developing Applications with Visual Basic .NET</h1>
          <h3>By Spencer, Phil</h3>
          <h3>Price = 45.95</h3>
          <h2>Description</h2>
          <p>
            Get the expert insights, practical code
            samples, and best practices you need
            to advance your expertise with <b>Visual
            Basic .NET</b>. Learn how to create faster,
            more reliable applications based on
            professional, pragmatic guidance by today's
            top <i>developers</i>.
          </p>
          <hr />
        </div>
      </body>
    </html>
    ```

## <a name="see-also"></a><span data-ttu-id="b4909-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4909-127">See also</span></span>

- [<span data-ttu-id="b4909-128">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="b4909-128">XML Literals</span></span>](../../../language-reference/xml-literals/index.md)
- [<span data-ttu-id="b4909-129">Manipulation de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b4909-129">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
- [<span data-ttu-id="b4909-130">XML</span><span class="sxs-lookup"><span data-stu-id="b4909-130">XML</span></span>](index.md)
- [<span data-ttu-id="b4909-131">Guide pratique : charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux</span><span class="sxs-lookup"><span data-stu-id="b4909-131">How to: Load XML from a File, String, or Stream</span></span>](how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="b4909-132">LINQ</span><span class="sxs-lookup"><span data-stu-id="b4909-132">LINQ</span></span>](../linq/index.md)
- [<span data-ttu-id="b4909-133">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b4909-133">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
