---
title: Littéral d’élément XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6a91de4e279816bafd29f46bb4f5422cbd934ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400187"
---
# <a name="xml-element-literal-visual-basic"></a>Littéral d'élément XML (Visual Basic)

Littéral qui représente un <xref:System.Xml.Linq.XElement> objet.

## <a name="syntax"></a>Syntaxe

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a>Éléments

- `<`

  Obligatoire. Ouvre la balise d’élément de départ.

- `name`

  Obligatoire. Nom de l'élément. Le format est l’un des éléments suivants :

  - Texte littéral pour le nom d’élément, sous la forme `[ePrefix:]eName` , où :

    |Élément|Description|
    |---|---|
    |`ePrefix`|facultatif. Préfixe d’espace de noms XML pour l’élément. Doit être un espace de noms XML global qui est défini avec une `Imports` instruction dans le fichier ou au niveau du projet, ou un espace de noms XML local défini dans cet élément ou un élément parent.|
    |`eName`|Obligatoire. Nom de l'élément. Le format est l’un des éléments suivants :<br /><br /> -Texte littéral. Consultez [les noms des éléments et attributs XML déclarés](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Expression incorporée du formulaire `<%= eNameExp %>` . Le type de `eNameExp` doit être `String` ou un type implicitement convertible en <xref:System.Xml.Linq.XName> .|

  - Expression incorporée du formulaire `<%= nameExp %>` . Le type de `nameExp` doit être `String` ou un type implicitement convertible en <xref:System.Xml.Linq.XName> . Une expression incorporée n’est pas autorisée dans une balise de fermeture d’un élément.

- `attributeList`

  Facultatif. Liste des attributs déclarés dans le littéral.

  `attribute [ attribute ... ]`

  Chacun `attribute` a l’une des syntaxes suivantes :

  - Assignation d’attribut, sous la forme `[aPrefix:]aName=aValue` :

    |Élément|Description|
    |---|---|
    |`aPrefix`|facultatif. Préfixe d’espace de noms XML pour l’attribut. Doit être un espace de noms XML global défini à l’aide d’une `Imports` instruction, ou un espace de noms XML local défini dans cet élément ou un élément parent.|
    |`aName`|Obligatoire. Nom de l'attribut. Le format est l’un des éléments suivants :<br /><br /> -Texte littéral. Consultez [les noms des éléments et attributs XML déclarés](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Expression incorporée du formulaire `<%= aNameExp %>` . Le type de `aNameExp` doit être `String` ou un type implicitement convertible en <xref:System.Xml.Linq.XName> .|
    |`aValue`|Facultatif. Valeur de l’attribut. Le format est l’un des éléments suivants :<br /><br /> -Texte littéral, placé entre guillemets.<br />-Expression incorporée du formulaire `<%= aValueExp %>` . N’importe quel type est autorisé.|

  - Expression incorporée du formulaire `<%= aExp %>` .

- `/>`

  Facultatif. Indique que l’élément est un élément vide, sans contenu.

- `>`

  Obligatoire. Termine la balise d’élément de début ou vide.

- `elementContents`

  Facultatif. Contenu de l’élément.

  `content [ content ... ]`

  Chaque `content` peut être l’un des éléments suivants :

  - Texte littéral. Tous les espaces blancs dans `elementContents` deviennent significatifs s’il y a du texte littéral.

  - Expression incorporée du formulaire `<%= contentExp %>` .

  - Littéral d’élément XML.

  - Littéral de commentaire XML. Consultez [littéral de commentaire XML](xml-comment-literal.md).

  - Littéral d’instruction de traitement XML. Consultez [littéral d’instruction de traitement XML](xml-processing-instruction-literal.md).

  - Littéral CDATA XML. Consultez [LITTÉRAL CDATA XML](xml-cdata-literal.md).

- `</[name]>`

  Facultatif. Représente la balise de fermeture de l’élément. Le `name` paramètre facultatif n’est pas autorisé lorsqu’il est le résultat d’une expression incorporée.

## <a name="return-value"></a>Valeur renvoyée

Objet <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Notes

Vous pouvez utiliser la syntaxe de littéral d’élément XML pour créer <xref:System.Xml.Linq.XElement> des objets dans votre code.

> [!NOTE]
> Un littéral XML peut s’étendre sur plusieurs lignes sans utiliser de caractères de continuation de ligne. Cette fonctionnalité vous permet de copier le contenu d’un document XML et de le coller directement dans un programme de Visual Basic.

Les expressions incorporées du formulaire `<%= exp %>` vous permettent d’ajouter des informations dynamiques à un littéral d’élément XML. Pour plus d’informations, consultez [expressions incorporées en XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).

Le compilateur Visual Basic convertit le littéral d’élément XML en appels au <xref:System.Xml.Linq.XElement.%23ctor%2A> constructeur et, si nécessaire, le <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructeur.

## <a name="xml-namespaces"></a>Espaces de noms XML

Les préfixes d’espaces de noms XML sont utiles quand vous devez créer des littéraux XML avec des éléments du même espace de noms de nombreuses fois dans le code. Vous pouvez utiliser des préfixes d’espaces de noms XML globaux, que vous définissez à l’aide de l' `Imports` instruction, ou des préfixes locaux, que vous définissez à l’aide de la `xmlns:xmlPrefix="xmlNamespace"` syntaxe d’attribut. Pour plus d’informations, consultez [instructions Imports (espace de noms XML)](../statements/imports-statement-xml-namespace.md).

Conformément aux règles de portée pour les espaces de noms XML, les préfixes locaux sont prioritaires sur les préfixes globaux. Toutefois, si un littéral XML définit un espace de noms XML, cet espace de noms n’est pas disponible pour les expressions qui apparaissent dans une expression incorporée. L’expression incorporée ne peut accéder qu’à l’espace de noms XML global.

Le compilateur Visual Basic convertit chaque espace de noms XML global utilisé par un littéral XML en une définition d’espace de noms locale dans le code généré. Les espaces de noms XML globaux qui ne sont pas utilisés n’apparaissent pas dans le code généré.

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer un élément XML simple qui a deux éléments vides imbriqués.

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

L’exemple affiche le texte suivant. Notez que le littéral conserve la structure des éléments vides.

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser des expressions incorporées pour nommer un élément et créer des attributs.

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

Ce code affiche le texte suivant :

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a>Exemple

L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML. Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et affiche le formulaire final de l’élément.

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

Ce code affiche le texte suivant :

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

Notez que le compilateur a converti le préfixe de l’espace de noms XML global en une définition de préfixe pour l’espace de noms XML. L' \<ns:middle> élément redéfinit le préfixe d’espace de noms XML pour l' \<ns:inner1> élément. Toutefois, l' \<ns:inner2> élément utilise l’espace de noms défini par l' `Imports` instruction.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- [Nom des attributs et des éléments XML déclarés](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [Littéral de commentaires XML](xml-comment-literal.md)
- [Littéral CDATA XML](xml-cdata-literal.md)
- [Littéraux XML](index.md)
- [Création de code XML dans Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Expressions incorporées en XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports, instruction (espace de noms XML)](../statements/imports-statement-xml-namespace.md)
