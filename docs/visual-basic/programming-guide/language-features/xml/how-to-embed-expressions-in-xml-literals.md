---
title: 'Comment : incorporer des expressions dans des littéraux XML'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 59ba03be6e132203523427d3b7af5a163b6f05ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392312"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Comment : incorporer des expressions dans des littéraux XML (Visual Basic)
Vous pouvez combiner des littéraux XML avec des expressions incorporées pour créer un document XML, un fragment ou un élément qui contient le contenu créé au moment de l’exécution. Les exemples suivants montrent comment utiliser des expressions incorporées pour remplir le contenu d’un élément, les attributs et les noms d’éléments au moment de l’exécution.  
  
 La syntaxe d’une expression incorporée est `<%=` `exp` `%>` , qui est la même syntaxe que celle utilisée par ASP.net. Pour plus d’informations, consultez [expressions incorporées en XML](embedded-expressions-in-xml.md).  
  
 Vous pouvez également utiliser les [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API pour créer des [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objets. Pour plus d’informations, consultez <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-insert-text-as-element-content"></a>Pour insérer du texte en tant que contenu d’élément  
  
- L’exemple suivant montre comment insérer le texte contenu dans la `contactName` variable entre les éléments de nom d’ouverture et de fermeture.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     Cet exemple produit la sortie suivante :  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Pour insérer du texte en tant que valeur d’attribut  
  
- L’exemple suivant montre comment insérer le texte contenu dans la `phoneType` variable en tant que valeur de l' `type` attribut.  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     Cet exemple produit la sortie suivante :  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Pour insérer du texte pour un nom d’élément  
  
- L’exemple suivant montre comment insérer le texte contenu dans la `elementName` variable en tant que nom d’un élément.  
  
     Lorsque vous créez des éléments à l’aide de cette technique, vous devez les fermer avec la \</> balise.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     Cet exemple produit la sortie suivante :  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Comment : créer des littéraux XML](how-to-create-xml-literals.md)
- [Expressions incorporées en XML](embedded-expressions-in-xml.md)
- [Création de code XML dans Visual Basic](creating-xml.md)
- [XML](index.md)
