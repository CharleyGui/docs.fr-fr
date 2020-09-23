---
title: 'Comment : accéder à des éléments descendants XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: dcbaf1f9022d86f40a90ef6a1e0033f627caeef2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058207"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Comment : accéder à des éléments descendants XML (Visual Basic)

Cet exemple montre comment utiliser une propriété d’axe descendant pour accéder à tous les éléments XML portant un nom spécifié et contenus sous un élément XML. En particulier, elle utilise la `Value` propriété pour récupérer la valeur du premier élément de la collection que la propriété de l' `name` axe descendant retourne. La `name` propriété d’axe descendant obtient tous les éléments nommés `name` qui sont contenus dans l' `contacts` objet. Cet exemple utilise également la `phone` propriété de l’axe descendant pour accéder à tous les descendants nommés `phone` qui sont contenus dans l' `contacts` objet.  
  
## <a name="example"></a>Exemple  

 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a>Compiler le code  

 Cet exemple nécessite :  
  
- une référence à l'espace de noms <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [XML Descendant Axis Property](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [Propriété de valeur XML](../../../language-reference/xml-axis/xml-value-property.md)
- [Accès au code XML dans Visual Basic](accessing-xml.md)
- [XML](index.md)
