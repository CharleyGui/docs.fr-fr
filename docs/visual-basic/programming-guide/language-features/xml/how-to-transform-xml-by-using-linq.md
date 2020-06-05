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
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Comment : transformer du code XML à l'aide de LINQ (Visual Basic)

Les [littéraux XML](../../../language-reference/xml-literals/index.md) facilitent la lecture des données XML à partir d’une source et leur transformation dans un nouveau format XML. Vous pouvez tirer parti des requêtes LINQ pour récupérer le contenu à transformer ou modifier le contenu d’un document existant en un nouveau format XML.

L’exemple de cette rubrique transforme le contenu d’un document source XML en HTML à afficher dans un navigateur.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-transform-an-xml-document"></a>Pour transformer un document XML

1. Dans Visual Studio, créez un projet de Visual Basic dans le modèle de projet d' **application console** .

2. Double-cliquez sur le fichier Module1. vb créé dans le projet pour modifier le code d’Visual Basic. Ajoutez le code suivant à l' `Sub Main` du `Module1` module. Ce code crée le document XML source en tant qu' <xref:System.Xml.Linq.XDocument> objet.

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

     [Comment : charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux](how-to-load-xml-from-a-file-string-or-stream.md).

3. Après le code pour créer le document XML source, ajoutez le code suivant pour récupérer tous les \<Book> éléments de l’objet et les transformer en un document HTML. La liste des \<Book> éléments est créée à l’aide d’une requête LINQ qui retourne une collection d' <xref:System.Xml.Linq.XElement> objets qui contiennent le code html transformé. Vous pouvez utiliser des expressions incorporées pour placer les valeurs du document source au nouveau format XML.

     Le document HTML obtenu est écrit dans un fichier à l’aide de la <xref:System.Xml.Linq.XElement.Save%2A> méthode.

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

4. Après `Sub Main` `Module1` , ajoutez une nouvelle méthode ( `Sub` ) pour transformer un \<Description> nœud dans le format HTML spécifié. Cette méthode est appelée par le code de l’étape précédente et est utilisée pour conserver le format des \<Description> éléments.

     Cette méthode remplace les sous-éléments de l' \<Description> élément par du code html. La `ReplaceWith` méthode est utilisée pour conserver l’emplacement des sous-éléments. Le contenu transformé de l' \<Description> élément est inclus dans un élément paragraph ( \<p> ) html. La <xref:System.Xml.Linq.XContainer.Nodes%2A> propriété est utilisée pour récupérer le contenu transformé de l' \<Description> élément. Cela permet de s’assurer que les sous-éléments sont inclus dans le contenu transformé.

     Ajoutez le code suivant après `Sub Main` `Module1` .

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

5. Enregistrez vos modifications.

6. Appuyez sur F5 pour exécuter le code. Le document enregistré résultant ressemble à ce qui suit :

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

## <a name="see-also"></a>Voir aussi

- [Littéraux XML](../../../language-reference/xml-literals/index.md)
- [Manipulation de code XML dans Visual Basic](manipulating-xml.md)
- [XML](index.md)
- [Guide pratique : charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux](how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../linq/index.md)
- [Introduction à LINQ en Visual Basic](../linq/introduction-to-linq.md)
