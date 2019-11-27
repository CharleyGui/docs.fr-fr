---
title: Espaces blancs dans les littéraux XML
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 56ededeb12d07e979bc86b03924e1ae0f0432822
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336005"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>Espaces blancs dans les littéraux XML (Visual Basic)
Le compilateur Visual Basic incorpore uniquement les espaces significatifs d’un littéral XML lorsqu’il crée un objet [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Les caractères d’espace blanc non significatifs ne sont pas incorporés.  
  
## <a name="significant-and-insignificant-white-space"></a>Espace blanc significatif et non significatif  
 Les caractères d’espace blanc dans les littéraux XML ne sont significatifs que dans trois domaines :  
  
- Lorsqu’ils sont dans une valeur d’attribut.  
  
- Lorsqu’elles font partie du contenu textuel d’un élément et que le texte contient également d’autres caractères.  
  
- Lorsqu’ils se trouvent dans une expression incorporée pour le contenu de texte d’un élément.  
  
 Sinon, le compilateur traite les caractères d’espace blanc comme non significatifs et n’inclut pas dans l’objet [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour le littéral.  
  
 Pour inclure des espaces non significatifs dans un littéral XML, utilisez une expression incorporée qui contient un littéral de chaîne avec l’espace blanc.  
  
> [!NOTE]
> Si l’attribut `xml:space` apparaît dans un littéral d’élément XML, le compilateur Visual Basic comprend l’attribut dans l’objet <xref:System.Xml.Linq.XElement>, mais l’ajout de cet attribut ne change pas la manière dont le compilateur traite les espaces blancs.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant contient deux éléments XML, externes et internes. Les deux éléments contiennent un espace blanc dans leur contenu de texte. L’espace blanc dans l’élément externe est insignifiante, car il ne contient que des espaces blancs et un élément XML. L’espace blanc dans l’élément interne est significatif, car il contient des espaces blancs et du texte.  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 Lors de l’exécution, ce code affiche le texte suivant.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
