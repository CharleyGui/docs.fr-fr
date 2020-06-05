---
title: 'Comment : accéder à des éléments enfants XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 994249801eecc2984947efac9712df0047f076a4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392816"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Comment : accéder à des éléments enfants XML (Visual Basic)
Cet exemple montre comment utiliser une propriété d’axe enfant pour accéder à tous les éléments enfants XML portant un nom spécifié dans un élément XML. En particulier, elle utilise la <xref:System.Xml.Linq.XElement.Value%2A> propriété pour récupérer la valeur du premier élément de la collection retourné par la `name` propriété d’axe enfant. La `name` propriété d’axe enfant obtient tous les éléments enfants nommés `phone` dans l' `contact` objet. Cet exemple utilise également la `phone` propriété d’axe enfant pour accéder à tous les éléments enfants nommés `phone` qui sont contenus dans l' `contact` objet.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple nécessite :  
  
- une référence à l'espace de noms <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [XML Child Axis Property](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [Propriété de valeur XML](../../../language-reference/xml-axis/xml-value-property.md)
- [Accès au code XML dans Visual Basic](accessing-xml.md)
- [XML](index.md)
