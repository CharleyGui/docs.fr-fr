---
title: Littéral d'élément XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6d900ca6868cfffe6b0e5b349321a79c5716c46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347025"
---
# <a name="xml-element-literal-visual-basic"></a>Littéral d'élément XML (Visual Basic)

Littéral qui représente un objet <xref:System.Xml.Linq.XElement>.

## <a name="syntax"></a>Syntaxe

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a>Composants

- `<`

  Requis. Ouvre la balise d’élément de départ.

- `name`

  Requis. Nom de l'élément. Le format est l’un des éléments suivants :

  - Texte littéral pour le nom d’élément, sous la forme `[ePrefix:]eName`, où :

    |Élément|Description|
    |---|---|
    |`ePrefix`|Ce paramètre est facultatif. Préfixe d’espace de noms XML pour l’élément. Doit être un espace de noms XML global défini avec une `Imports` instruction dans le fichier ou au niveau du projet, ou un espace de noms XML local défini dans cet élément ou un élément parent.|
    |`eName`|Requis. Nom de l'élément. Le format est l’un des éléments suivants :<br /><br /> -Texte littéral. Consultez [les noms des éléments et attributs XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Expression incorporée de la `<%= eNameExp %>`de formulaire. Le type de `eNameExp` doit être `String` ou un type implicitement convertible en <xref:System.Xml.Linq.XName>.|

  - Expression incorporée de la `<%= nameExp %>`de formulaire. Le type de `nameExp` doit être `String` ou un type implicitement convertible en <xref:System.Xml.Linq.XName>. Une expression incorporée n’est pas autorisée dans une balise de fermeture d’un élément.

- `attributeList`

  Ce paramètre est facultatif. Liste des attributs déclarés dans le littéral.

  `attribute [ attribute ... ]`

  Chaque `attribute` a l’une des syntaxes suivantes :

  - Assignation d’attribut, de la forme `[aPrefix:]aName=aValue`, où :

    |Élément|Description|
    |---|---|
    |`aPrefix`|Ce paramètre est facultatif. Préfixe d’espace de noms XML pour l’attribut. Doit être un espace de noms XML global défini à l’aide d’une instruction `Imports` ou d’un espace de noms XML local défini dans cet élément ou un élément parent.|
    |`aName`|Requis. Nom de l'attribut. Le format est l’un des éléments suivants :<br /><br /> -Texte littéral. Consultez [les noms des éléments et attributs XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Expression incorporée de la `<%= aNameExp %>`de formulaire. Le type de `aNameExp` doit être `String` ou un type implicitement convertible en <xref:System.Xml.Linq.XName>.|
    |`aValue`|Ce paramètre est facultatif. Valeur de l’attribut. Le format est l’un des éléments suivants :<br /><br /> -Texte littéral, placé entre guillemets.<br />-Expression incorporée de la `<%= aValueExp %>`de formulaire. N’importe quel type est autorisé.|

  - Expression incorporée de la `<%= aExp %>`de formulaire.

- `/>`

  Ce paramètre est facultatif. Indique que l’élément est un élément vide, sans contenu.

- `>`

  Requis. Termine la balise d’élément de début ou vide.

- `elementContents`

  Ce paramètre est facultatif. Contenu de l’élément.

  `content [ content ... ]`

  Chaque `content` peut être l’une des suivantes :

  - Texte littéral. Tous les espaces blancs dans `elementContents` deviennent significatifs s’il existe un texte littéral.

  - Expression incorporée de la `<%= contentExp %>`de formulaire.

  - Littéral d’élément XML.

  - Littéral de commentaire XML. Consultez [littéral de commentaire XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).

  - Littéral d’instruction de traitement XML. Consultez [littéral d’instruction de traitement XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).

  - Littéral CDATA XML. Consultez [LITTÉRAL CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).

- `</[name]>`

  Ce paramètre est facultatif. Représente la balise de fermeture de l’élément. Le paramètre facultatif `name` n’est pas autorisé lorsqu’il est le résultat d’une expression incorporée.

## <a name="return-value"></a>Valeur de retour

Objet <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Notes

Vous pouvez utiliser la syntaxe de littéral d’élément XML pour créer des <xref:System.Xml.Linq.XElement> des objets dans votre code.

> [!NOTE]
> Un littéral XML peut s’étendre sur plusieurs lignes sans utiliser de caractères de continuation de ligne. Cette fonctionnalité vous permet de copier le contenu d’un document XML et de le coller directement dans un programme de Visual Basic.

Les expressions incorporées de la forme `<%= exp %>` vous permettent d’ajouter des informations dynamiques à un littéral d’élément XML. Pour plus d’informations, consultez [expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).

Le compilateur Visual Basic convertit le littéral d’élément XML en appels au constructeur <xref:System.Xml.Linq.XElement.%23ctor%2A> et, si nécessaire, le constructeur <xref:System.Xml.Linq.XAttribute.%23ctor%2A>.

## <a name="xml-namespaces"></a>Espaces de noms XML

Les préfixes d’espaces de noms XML sont utiles quand vous devez créer des littéraux XML avec des éléments du même espace de noms de nombreuses fois dans le code. Vous pouvez utiliser des préfixes d’espaces de noms XML globaux, que vous définissez à l’aide de l’instruction `Imports` ou de préfixes locaux, que vous définissez à l’aide de la syntaxe d’attribut `xmlns:xmlPrefix="xmlNamespace"`. Pour plus d’informations, consultez [instructions Imports (espace de noms XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

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

Notez que le compilateur a converti le préfixe de l’espace de noms XML global en une définition de préfixe pour l’espace de noms XML. L’élément \<NS : Middle > redéfinit le préfixe d’espace de noms XML pour l’élément \<NS : inner1 >. Toutefois, l' \<NS : inner2 > élément utilise l’espace de noms défini par l’instruction `Imports`.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [Littéraux de commentaires XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [Littéral CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports (instruction) (espace de noms XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
