---
title: Construction fonctionnelle-LINQ to XML
description: LINQ to XML fournit une construction fonctionnelle, qui vous permet de créer une arborescence XML dans une instruction unique.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: bcdc153d7f60cfb165dcb741d62b6af5c07a148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552504"
---
# <a name="functional-construction-linq-to-xml"></a>Construction fonctionnelle (LINQ to XML)

LINQ to XML offre un moyen puissant de créer des éléments XML appelés *construction fonctionnelle*. La construction fonctionnelle vous permet de créer une arborescence XML dans une instruction unique.

Plusieurs fonctionnalités clés de l’interface de programmation LINQ to XML sont utilisées dans la construction fonctionnelle :

- Le constructeur <xref:System.Xml.Linq.XElement> prend différents types d'arguments comme contenu. Par exemple, vous pouvez passer un autre objet <xref:System.Xml.Linq.XElement>, qui devient un élément enfant. Vous pouvez passer un objet <xref:System.Xml.Linq.XAttribute>, qui devient un attribut de l'élément. Ou vous pouvez passer tout autre type d'objet, qui est converti en chaîne et devient le contenu texte de l'élément.
- Le constructeur <xref:System.Xml.Linq.XElement> prend un tableau `params` de type <xref:System.Object>, de sorte que vous puissiez passer toute quantité d'objets au constructeur. Cela vous permet de créer un élément dont le contenu est complexe.
- Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l'objet est énumérée et tous les éléments de la collection sont ajoutés. Si la collection contient des objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, chaque élément de la collection est ajouté séparément. Cela est important car il vous permet de passer les résultats d’une requête LINQ au constructeur.

## <a name="example-create-an-xml-tree"></a>Exemple : création d’une arborescence XML

Vous pouvez utiliser la construction fonctionnelle pour écrire du code afin de créer une arborescence XML. Par exemple :

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

## <a name="example-create-an-xml-tree-using-linq-query-results"></a>Exemple : créer une arborescence XML à l’aide des résultats de requête LINQ

Ces fonctionnalités vous permettent également d’écrire du code qui utilise les résultats de requêtes LINQ lorsque vous créez une arborescence XML, comme dans l’exemple suivant :

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

Dans Visual Basic, la même chose est accomplie avec des littéraux XML :

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where CInt(el) > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

Cet exemple produit la sortie suivante :

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="see-also"></a>Voir aussi

- [Créer des arborescences XML en C #](create-xml-trees.md)
- [Littéraux XML dans Visual Basic](xml-literals.md)
