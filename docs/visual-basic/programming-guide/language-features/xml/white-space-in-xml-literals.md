---
title: Espaces blancs dans les littéraux XML
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 5db8f92117e77d96eab34f28758546393e2afca0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91099097"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>Espaces blancs dans les littéraux XML (Visual Basic)

Le compilateur Visual Basic incorpore uniquement les espaces significatifs d’un littéral XML lorsqu’il crée un [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objet. Les caractères d’espace blanc non significatifs ne sont pas incorporés.  
  
## <a name="significant-and-insignificant-white-space"></a>Espace blanc significatif et non significatif  

 Les caractères d’espace blanc dans les littéraux XML ne sont significatifs que dans trois domaines :  
  
- Lorsqu’ils sont dans une valeur d’attribut.  
  
- Lorsqu’elles font partie du contenu textuel d’un élément et que le texte contient également d’autres caractères.  
  
- Lorsqu’ils se trouvent dans une expression incorporée pour le contenu de texte d’un élément.  
  
 Sinon, le compilateur traite les caractères d’espace blanc comme non significatifs et n’inclut pas dans l' [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objet pour le littéral.  
  
 Pour inclure des espaces non significatifs dans un littéral XML, utilisez une expression incorporée qui contient un littéral de chaîne avec l’espace blanc.  
  
> [!NOTE]
> Si l' `xml:space` attribut apparaît dans un littéral d’élément XML, le compilateur Visual Basic comprend l’attribut dans l' <xref:System.Xml.Linq.XElement> objet, mais l’ajout de cet attribut ne change pas la manière dont le compilateur traite les espaces blancs.  
  
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

- [Création de code XML dans Visual Basic](creating-xml.md)
