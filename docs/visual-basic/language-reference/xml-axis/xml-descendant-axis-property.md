---
title: XML Descendant Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400251"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Propriété d'axe descendant XML (Visual Basic)

Fournit l’accès aux descendants des éléments suivants : un <xref:System.Xml.Linq.XElement> objet, un <xref:System.Xml.Linq.XDocument> objet, une collection d' <xref:System.Xml.Linq.XElement> objets ou une collection d' <xref:System.Xml.Linq.XDocument> objets.

## <a name="syntax"></a>Syntaxe

```vb
object...<descendant>
```

## <a name="parts"></a>Éléments

`object` Obligatoire. Un objet <xref:System.Xml.Linq.XElement>, un objet <xref:System.Xml.Linq.XDocument>, une collection d’objets <xref:System.Xml.Linq.XElement> ou une collection d’objets <xref:System.Xml.Linq.XDocument>.

`...<` Obligatoire. Indique le début d’une propriété d’axe descendant.

`descendant` Obligatoire. Nom des nœuds descendants auxquels accéder, sous la forme [ `prefix:]name` .

|Élément|Description|
|----------|-----------------|
|`prefix`|facultatif. Préfixe d’espace de noms XML pour le nœud descendant. Doit être un espace de noms XML global défini à l’aide d’une `Imports` instruction.|
|`name`|Obligatoire. Nom local du nœud descendant. Consultez [les noms des éléments et attributs XML déclarés](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|

`>` Obligatoire. Indique la fin d’une propriété d’axe descendant.

## <a name="return-value"></a>Valeur renvoyée

Collection d’objets <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Notes

Vous pouvez utiliser une propriété d’axe descendant XML pour accéder aux nœuds descendants par nom à partir d’un <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objet ou, ou d’une collection d' <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objets ou. Utilisez la `Value` propriété XML pour accéder à la valeur du premier nœud descendant dans la collection retournée. Pour plus d’informations, consultez [propriété de valeur XML](xml-value-property.md).

Le compilateur Visual Basic convertit les propriétés de l’axe descendant en appels à la <xref:System.Xml.Linq.XContainer.Descendants%2A> méthode.

## <a name="xml-namespaces"></a>Espaces de noms XML

Le nom dans une propriété d’axe descendante ne peut utiliser que des espaces de noms XML déclarés globalement avec l' `Imports` instruction. Elle ne peut pas utiliser les espaces de noms XML déclarés localement dans des littéraux d’élément XML. Pour plus d’informations, consultez [instructions Imports (espace de noms XML)](../statements/imports-statement-xml-namespace.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment accéder à la valeur du premier nœud descendant nommé `name` et aux valeurs de tous les nœuds descendants nommés `phone` à partir de l' `contacts` objet.

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

Ce code affiche le texte suivant :

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>Exemple

L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML. Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et accéder à la valeur du premier nœud enfant avec le nom qualifié `ns:name` .

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

Ce code affiche le texte suivant :

`Name: Patrick Hines`

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- [Propriétés d'axe XML](index.md)
- [Littéraux XML](../xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Nom des attributs et des éléments XML déclarés](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
