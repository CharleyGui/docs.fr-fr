---
title: Littéral CDATA XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 72e899e7bd30f2edf0e88207bb3b75bdf36fa11c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349433"
---
# <a name="xml-cdata-literal-visual-basic"></a>Littéral CDATA XML (Visual Basic)
Littéral représentant un objet <xref:System.Xml.Linq.XCData>.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Composants  
 `<![CDATA[`  
 Requis. Indique le début de la section CDATA XML.  
  
 `content`  
 Requis. Contenu de texte à afficher dans la section CDATA XML.  
  
 `]]>`  
 Requis. Indique la fin de la section.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet <xref:System.Xml.Linq.XCData>.  
  
## <a name="remarks"></a>Notes  
 Les sections CDATA XML contiennent du texte brut qui doit être inclus, mais pas analysé, avec le code XML qui le contient. Une section CDATA XML peut contenir n’importe quel texte. Cela comprend les caractères XML réservés. La section CDATA XML se termine par la séquence « ]] > ». Cela implique les points suivants :  
  
- Vous ne pouvez pas utiliser une expression incorporée dans un littéral CDATA XML, car les délimiteurs d’expressions incorporées sont du contenu CDATA XML valide.  
  
- Les sections CDATA XML ne peuvent pas être imbriquées, car `content` ne peut pas contenir la valeur « ]] > ».  
  
 Vous pouvez assigner un littéral CDATA XML à une variable ou l’inclure dans un littéral d’élément XML.  
  
> [!NOTE]
> Un littéral XML peut s’étendre sur plusieurs lignes, mais n’utilise pas de caractères de continuation de ligne. Cela vous permet de copier le contenu d’un document XML et de le coller directement dans un programme de Visual Basic.  
  
 Le compilateur Visual Basic convertit le littéral CDATA XML en un appel au constructeur <xref:System.Xml.Linq.XCData.%23ctor%2A>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une section CDATA qui contient le texte « peut contenir des balises \<XML > ».  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XCData>
- [Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
