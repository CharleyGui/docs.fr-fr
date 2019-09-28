---
title: Propriété de valeur XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 46f81e39686da30270cd67edeb4c9f2d43e048b3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592006"
---
# <a name="xml-value-property-visual-basic"></a>Propriété de valeur XML (Visual Basic)

Fournit l’accès à la valeur du premier élément d’une collection d’objets <xref:System.Xml.Linq.XElement>.

## <a name="syntax"></a>Syntaxe

```vb
object.Value
```

## <a name="parts"></a>Composants

|Terme|Définition|  
|---|---|  
|`object`|Obligatoire. Collection d'objets <xref:System.Xml.Linq.XElement>.|  

## <a name="return-value"></a>Valeur de retour

 @No__t-0 qui contient la valeur du premier élément de la collection, ou `Nothing` si la collection est vide.

## <a name="remarks"></a>Notes

 La propriété <xref:System.Xml.Linq.XElement.Value%2A> facilite l’accès à la valeur du premier élément d’une collection d’objets <xref:System.Xml.Linq.XElement>. Cette propriété vérifie d’abord si la collection contient au moins un objet. Si la collection est vide, cette propriété retourne `Nothing`. Sinon, cette propriété retourne la valeur de la propriété <xref:System.Xml.Linq.XElement.Value%2A> du premier élément de la collection.

> [!NOTE]
> Lorsque vous accédez à la valeur d’un attribut XML à l’aide de l’identificateur « \@ », la valeur de l’attribut est retournée en tant que `String` et vous n’avez pas besoin de spécifier explicitement la propriété <xref:System.Xml.Linq.XAttribute.Value%2A>.

 Pour accéder à d’autres éléments dans une collection, vous pouvez utiliser la propriété d’indexeur d’extension XML. Pour plus d’informations, consultez [propriété d’indexeur d’extension](extension-indexer-property.md).

## <a name="inheritance"></a>Héritage

 La plupart des utilisateurs n’auront pas à implémenter <xref:System.Collections.Generic.IEnumerable%601> et peuvent donc ignorer cette section.

 La propriété <xref:System.Xml.Linq.XElement.Value%2A> est une propriété d’extension pour les types qui implémentent `IEnumerable(Of XElement)`. La liaison de cette propriété d’extension est semblable à la liaison de méthodes d’extension : si un type implémente l’une des interfaces et définit une propriété qui porte le nom « value », cette propriété a la priorité sur la propriété d’extension. En d’autres termes, cette propriété <xref:System.Xml.Linq.XElement.Value%2A> peut être substituée en définissant une nouvelle propriété dans une classe qui implémente `IEnumerable(Of XElement)`.

## <a name="example"></a>Exemple

 L’exemple suivant montre comment utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A> pour accéder au premier nœud d’une collection d’objets <xref:System.Xml.Linq.XElement>. L’exemple utilise la propriété d’axe enfant pour récupérer la collection de tous les nœuds enfants nommés `phone` qui se trouvent dans l’objet `contact`.

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 Ce code affiche le texte suivant :

 `Phone number: 206-555-0144`

## <a name="example"></a>Exemple

 L’exemple suivant montre comment obtenir la valeur d’un attribut XML à partir d’une collection d’objets <xref:System.Xml.Linq.XAttribute>. L’exemple utilise la propriété d’axe d’attribut pour afficher la valeur de l’attribut `type` pour tous les éléments `phone`.

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 Ce code affiche le texte suivant :

 ```console
 home
 work
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [Propriétés d’axe XML](index.md)
- [Littéraux XML](../xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Méthodes d’extension](../../programming-guide/language-features/procedures/extension-methods.md)
- [Propriété d’indexeur d’extension](extension-indexer-property.md)
- [Propriété d’axe enfant XML](xml-child-axis-property.md)
- [Propriété d’axe d’attribut XML](xml-attribute-axis-property.md)
