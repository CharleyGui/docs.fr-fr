---
title: 'Comment : accéder à des éléments enfants XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 32bdb1ba476a954bdad1f23c3ecc6129c90ccaac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347172"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Comment : accéder à des éléments enfants XML (Visual Basic)
Cet exemple montre comment utiliser une propriété d’axe enfant pour accéder à tous les éléments enfants XML portant un nom spécifié dans un élément XML. En particulier, elle utilise la propriété <xref:System.Xml.Linq.XElement.Value%2A> pour récupérer la valeur du premier élément de la collection retournée par la propriété d’axe enfant `name`. La propriété d’axe enfant `name` obtient tous les éléments enfants nommés `phone` dans l’objet `contact`. Cet exemple utilise également la propriété d’axe enfant `phone` pour accéder à tous les éléments enfants nommés `phone` qui sont contenus dans l’objet `contact`.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple nécessite :  
  
- une référence à l'espace de noms <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [Propriété d’axe enfant XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Propriété de valeur XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Accès au code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
