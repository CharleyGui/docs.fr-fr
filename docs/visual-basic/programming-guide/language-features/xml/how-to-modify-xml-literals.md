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
# <a name="how-to-modify-xml-literals-visual-basic"></a>Comment : modifier des littéraux XML (Visual Basic)

Visual Basic fournit des méthodes pratiques pour modifier des littéraux XML. Vous pouvez ajouter ou supprimer des éléments et des attributs, et vous pouvez également remplacer un élément existant par un nouvel élément XML. Cette rubrique fournit plusieurs exemples de modification d’un littéral XML existant.

### <a name="to-modify-the-value-of-an-xml-literal"></a>Pour modifier la valeur d’un littéral XML

1. Pour modifier la valeur d’un littéral XML, obtenez une référence au littéral XML et définissez la propriété `Value` sur la valeur souhaitée.

    L’exemple de code suivant met à jour la valeur de tous les éléments de \<Price > dans un document XML.

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    L’exemple suivant montre des exemples de code source XML et des données XML modifiées à partir de cet exemple de code.

    XML source :

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

    XML modifié :

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
    > La propriété `Value` fait référence au premier élément XML d’une collection. Si plusieurs éléments ont le même nom dans une collection, la définition de la propriété `Value` affecte uniquement le premier élément de la collection.

### <a name="to-add-an-attribute-to-an-xml-literal"></a>Pour ajouter un attribut à un littéral XML

1. Pour ajouter un attribut à un littéral XML, commencez par obtenir une référence au littéral XML. Vous pouvez ensuite ajouter un attribut en ajoutant une nouvelle propriété d’axe d’attribut XML. Vous pouvez également ajouter un nouvel objet <xref:System.Xml.Linq.XAttribute> au littéral XML à l’aide de la méthode <xref:System.Xml.Linq.XContainer.Add%2A>. L’exemple suivant illustre les deux options.

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    L’exemple suivant montre des exemples de code source XML et des données XML modifiées à partir de cet exemple de code.

    XML source :

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

    XML modifié :

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

    Pour plus d’informations sur les propriétés d’axe d’attribut XML, consultez [propriété d’axe d’attribut XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).

### <a name="to-add-an-element-to-an-xml-literal"></a>Pour ajouter un élément à un littéral XML

1. Pour ajouter un élément à un littéral XML, commencez par obtenir une référence au littéral XML. Vous pouvez ensuite ajouter un nouvel objet <xref:System.Xml.Linq.XElement> en tant que dernier sous-élément de l’élément à l’aide de la méthode <xref:System.Xml.Linq.XContainer.Add%2A>. Vous pouvez ajouter un nouvel objet <xref:System.Xml.Linq.XElement> en tant que premier sous-élément à l’aide de la méthode <xref:System.Xml.Linq.XContainer.AddFirst%2A>.

    Pour ajouter un nouvel élément à un emplacement spécifique par rapport à d’autres sous-éléments, commencez par obtenir une référence à un sous-élément adjacent. Vous pouvez ensuite ajouter le nouvel objet <xref:System.Xml.Linq.XElement> avant le sous-élément adjacent à l’aide de la méthode <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>. Vous pouvez également ajouter le nouvel objet <xref:System.Xml.Linq.XElement> après le sous-élément adjacent à l’aide de la méthode <xref:System.Xml.Linq.XNode.AddAfterSelf%2A>.

    L’exemple suivant montre des exemples de chacune de ces techniques.

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    L’exemple suivant montre des exemples de code source XML et des données XML modifiées à partir de cet exemple de code.

    XML source :

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

    XML modifié :

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

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>Pour supprimer un élément ou un attribut d’un littéral XML

1. Pour supprimer un élément ou un attribut d’un littéral XML, obtenez une référence à l’élément ou à l’attribut et appelez la méthode `Remove`, comme indiqué dans l’exemple suivant.

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    L’exemple suivant montre des exemples de code source XML et des données XML modifiées à partir de cet exemple de code.

    XML source :

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

    XML modifié :

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

    Pour supprimer tous les éléments ou attributs d’un littéral XML, obtenez une référence au littéral XML et appelez la méthode <xref:System.Xml.Linq.XElement.RemoveAll%2A>.

### <a name="to-modify-an-xml-literal"></a>Pour modifier un littéral XML

1. Pour modifier le nom d’un élément XML, obtenez d’abord une référence à l’élément. Vous pouvez ensuite créer un nouvel objet <xref:System.Xml.Linq.XElement> avec un nouveau nom et passer le nouvel objet <xref:System.Xml.Linq.XElement> à la méthode <xref:System.Xml.Linq.XNode.ReplaceWith%2A> de l’objet <xref:System.Xml.Linq.XElement> existant.

    Si l’élément que vous remplacez contient des sous-éléments qui doivent être conservés, affectez la valeur du nouvel objet <xref:System.Xml.Linq.XElement> à la propriété <xref:System.Xml.Linq.XContainer.Nodes%2A> de l’élément existant. La valeur du nouvel élément est alors définie sur le code XML interne de l’élément existant. Sinon, vous pouvez définir la valeur du nouvel élément sur la propriété `Value` de l’élément existant.

    L’exemple de code suivant remplace tous les éléments \<Description > par un élément > Abstrait \<. Le contenu de la description de l' \<> élément est conservé dans le nouvel élément > Abstrait \<à l’aide de la propriété <xref:System.Xml.Linq.XContainer.Nodes%2A> de la description \<> objet <xref:System.Xml.Linq.XElement>.

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    L’exemple suivant montre des exemples de code source XML et des données XML modifiées à partir de cet exemple de code.

    XML source :

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

    XML modifié :

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

## <a name="see-also"></a>Voir aussi

- [Manipulation de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Guide pratique : charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
