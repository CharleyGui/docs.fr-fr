---
title: 'Comment : créer des littéraux XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: e3af5185d2c2106e6a696a6569ef59897d0f1fe1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333002"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Comment : créer des littéraux XML (Visual Basic)
Vous pouvez créer un document XML, un fragment ou un élément directement dans le code à l’aide d’un littéral XML. Les exemples de cette rubrique montrent comment créer un élément XML qui a trois éléments enfants et comment créer un document XML.  
  
 Vous pouvez également utiliser les API [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour créer des objets [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Pour plus d'informations, consultez <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Pour créer un élément XML  
  
- Créez le XML inline à l’aide de la syntaxe de littéral XML, qui est la même que la syntaxe XML réelle.  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     Exécutez le code. Le résultat de ce code est le suivant :  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Pour créer un document XML  
  
- Créez le document XML en ligne. Le code suivant crée un document XML qui a une syntaxe littérale, une déclaration XML, une instruction de traitement, un commentaire et un élément qui contient un autre élément.  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     Exécutez le code. Le résultat de ce code est le suivant :  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Voir aussi

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
