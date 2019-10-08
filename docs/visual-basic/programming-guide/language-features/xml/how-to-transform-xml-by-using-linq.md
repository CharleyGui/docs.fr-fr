---
title: 'Procédure : Transformer du code XML à l’aide de LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 08378775f2c30d8ebfcc4f7ceea6fc3ecb2066e5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003266"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Procédure : Transformer du code XML à l’aide de LINQ (Visual Basic)
Les [littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md) facilitent la lecture des données XML à partir d’une source et leur transformation dans un nouveau format XML. Vous pouvez tirer parti des requêtes LINQ pour récupérer le contenu à transformer ou modifier le contenu d’un document existant en un nouveau format XML.  
  
 L’exemple de cette rubrique transforme le contenu d’un document source XML en HTML à afficher dans un navigateur.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a>Pour transformer un document XML  
  
1. Dans Visual Studio, créez un projet de Visual Basic dans le modèle de projet d' **application console** .  
  
2. Double-cliquez sur le fichier Module1. vb créé dans le projet pour modifier le code d’Visual Basic. Ajoutez le code suivant au `Sub Main` du module `Module1`. Ce code crée le document XML source en tant qu’objet <xref:System.Xml.Linq.XDocument>.  
  
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
  
     [Guide pratique pour Charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux @ no__t-0.  
  
3. Après le code pour créer le document XML source, ajoutez le code suivant pour récupérer tous les éléments \<Book > de l’objet et les transformer en un document HTML. La liste des éléments de > @no__t 0Book est créée à l’aide d’une requête LINQ qui retourne une collection d’objets <xref:System.Xml.Linq.XElement> qui contiennent le code HTML transformé. Vous pouvez utiliser des expressions incorporées pour placer les valeurs du document source au nouveau format XML.  
  
     Le document HTML obtenu est écrit dans un fichier à l’aide de la méthode <xref:System.Xml.Linq.XElement.Save%2A>.  
  
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
  
4. Une fois `Sub Main` sur `Module1`, ajoutez une nouvelle méthode (`Sub`) pour transformer un nœud > \<Description dans le format HTML spécifié. Cette méthode est appelée par le code de l’étape précédente et est utilisée pour conserver le format des éléments > \<Description.  
  
     Cette méthode remplace les sous-éléments de l’élément \<Description > par du code HTML. La méthode `ReplaceWith` est utilisée pour conserver l’emplacement des sous-éléments. Le contenu transformé de l’élément \<Description > est inclus dans un élément de paragraphe HTML (\<P >). La propriété <xref:System.Xml.Linq.XContainer.Nodes%2A> est utilisée pour récupérer le contenu transformé de l’élément > \<Description. Cela permet de s’assurer que les sous-éléments sont inclus dans le contenu transformé.  
  
     Ajoutez le code suivant après `Sub Main` de `Module1`.  
  
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
  
5. Enregistrez les modifications apportées.  
  
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

- [Littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md)
- [Manipulation de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Guide pratique pour Charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux @ no__t-0
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
