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
ms.openlocfilehash: b2bf524214fa8ecca215d50c198b23d127e3b400
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349448"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Propriété d'axe descendant XML (Visual Basic)

Permet d’accéder aux descendants des éléments suivants : un objet <xref:System.Xml.Linq.XElement>, un objet <xref:System.Xml.Linq.XDocument>, une collection d’objets <xref:System.Xml.Linq.XElement> ou une collection d’objets <xref:System.Xml.Linq.XDocument>.

## <a name="syntax"></a>Syntaxe

```vb
object...<descendant>
```

## <a name="parts"></a>Composants

`object` (obligatoire). Un objet <xref:System.Xml.Linq.XElement>, un objet <xref:System.Xml.Linq.XDocument>, une collection d’objets <xref:System.Xml.Linq.XElement> ou une collection d’objets <xref:System.Xml.Linq.XDocument>.

`...<` (obligatoire). Indique le début d’une propriété d’axe descendant.

`descendant` (obligatoire). Nom des nœuds descendants auxquels accéder, sous la forme [`prefix:]name`.

|Élément|Description|
|----------|-----------------|
|`prefix`|Ce paramètre est facultatif. Préfixe d’espace de noms XML pour le nœud descendant. Doit être un espace de noms XML global défini à l’aide d’une instruction `Imports`.|
|`name`|Requis. Nom local du nœud descendant. Consultez [les noms des éléments et attributs XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|

`>` (obligatoire). Indique la fin d’une propriété d’axe descendant.

## <a name="return-value"></a>Valeur de retour

Collection d'objets <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Notes

Vous pouvez utiliser une propriété d’axe descendant XML pour accéder aux nœuds descendants par nom à partir d’un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>, ou à partir d’une collection d’objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>. Utilisez la propriété `Value` XML pour accéder à la valeur du premier nœud descendant dans la collection retournée. Pour plus d’informations, consultez [propriété de valeur XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).

Le compilateur de Visual Basic convertit les propriétés de l’axe descendant en appels à la méthode <xref:System.Xml.Linq.XContainer.Descendants%2A>.

## <a name="xml-namespaces"></a>Espaces de noms XML

Le nom dans une propriété d’axe descendante ne peut utiliser que des espaces de noms XML déclarés globalement avec l’instruction `Imports`. Elle ne peut pas utiliser les espaces de noms XML déclarés localement dans des littéraux d’élément XML. Pour plus d’informations, consultez [instructions Imports (espace de noms XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment accéder à la valeur du premier nœud descendant nommé `name` et aux valeurs de tous les nœuds descendants nommés `phone` à partir de l’objet `contacts`.

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

Ce code affiche le texte suivant :

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>Exemple

L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML. Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et accéder à la valeur du premier nœud enfant avec le nom qualifié `ns:name`.

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

Ce code affiche le texte suivant :

`Name: Patrick Hines`

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
