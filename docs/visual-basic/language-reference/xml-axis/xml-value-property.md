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
ms.openlocfilehash: 9edf95c7cedced55ab2441baf51b7c2052e4654c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942981"
---
# <a name="xml-value-property-visual-basic"></a>Propriété de valeur XML (Visual Basic)
Fournit l’accès à la valeur du premier élément d’une collection d' <xref:System.Xml.Linq.XElement> objets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
object.Value  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`object`|Requis. Collection d'objets <xref:System.Xml.Linq.XElement>.|  
  
## <a name="return-value"></a>Valeur de retour  
 Qui contient la valeur du premier élément de la collection ou `Nothing` si la collection est vide. `String`  
  
## <a name="remarks"></a>Notes  
 La <xref:System.Xml.Linq.XElement.Value%2A> propriété permet d’accéder facilement à la valeur du premier élément d’une collection d' <xref:System.Xml.Linq.XElement> objets. Cette propriété vérifie d’abord si la collection contient au moins un objet. Si la collection est vide, cette propriété retourne `Nothing`. Sinon, cette propriété retourne la valeur de la <xref:System.Xml.Linq.XElement.Value%2A> propriété du premier élément de la collection.  
  
> [!NOTE]
> Lorsque vous accédez à la valeur d’un attribut XML à l'\@aide de l’identificateur «», la valeur de l' `String` attribut est retournée en tant que et vous <xref:System.Xml.Linq.XAttribute.Value%2A> n’avez pas besoin de spécifier explicitement la propriété.  
  
 Pour accéder à d’autres éléments dans une collection, vous pouvez utiliser la propriété d’indexeur d’extension XML. Pour plus d’informations, consultez propriété d’indexeur d' [extension](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Héritage  
 La plupart des utilisateurs n’auront pas <xref:System.Collections.Generic.IEnumerable%601>à implémenter et peuvent donc ignorer cette section.  
  
 La <xref:System.Xml.Linq.XElement.Value%2A> propriété est une propriété d’extension pour les types `IEnumerable(Of XElement)`qui implémentent. La liaison de cette propriété d’extension est semblable à la liaison de méthodes d’extension: si un type implémente l’une des interfaces et définit une propriété qui porte le nom «value», cette propriété a la priorité sur la propriété d’extension. En d’autres termes, <xref:System.Xml.Linq.XElement.Value%2A> cette propriété peut être substituée en définissant une nouvelle propriété dans une classe qui `IEnumerable(Of XElement)`implémente.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la <xref:System.Xml.Linq.XElement.Value%2A> propriété pour accéder au premier nœud d’une collection d' <xref:System.Xml.Linq.XElement> objets. L’exemple utilise la propriété d’axe enfant pour récupérer la collection de tous les nœuds enfants nommés `phone` qui se trouvent dans l' `contact` objet.  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 Ce code affiche le texte suivant :  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment obtenir la valeur d’un attribut XML à partir d’une collection <xref:System.Xml.Linq.XAttribute> d’objets. L’exemple utilise la propriété d’axe d’attribut pour afficher la valeur `type` de l’attribut pour tous `phone` les éléments.  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 Ce code affiche le texte suivant :  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Méthodes d’extension](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Propriété d’indexeur d’extension](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [Propriété d’axe enfant XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Propriété d’axe d’attribut XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
