---
title: Vue d'ensemble des littéraux XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: 4024f4ad2b2aa8cb1897e83d87a7a00b1ba25e67
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964708"
---
# <a name="xml-literals-overview-visual-basic"></a>Vue d'ensemble des littéraux XML (Visual Basic)
Un *littéral XML* vous permet d’incorporer du code XML directement dans votre code Visual Basic. La syntaxe de littéral XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] représente des objets et est similaire à la syntaxe XML 1,0. Il est ainsi plus facile de créer des éléments et des documents XML par programmation, car votre code a la même structure que le XML final.  
  
 Visual Basic compile des littéraux XML en [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objets. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]fournit un modèle d’objet simple pour la création et la manipulation de XML, et ce modèle s' [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]intègre parfaitement à. Pour plus d'informations, consultez <xref:System.Xml.Linq.XElement>.  
  
 Vous pouvez incorporer une expression Visual Basic dans un littéral XML. Au moment de l’exécution, votre application [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] crée un objet pour chaque littéral, en incorporant les valeurs des expressions incorporées. Cela vous permet de spécifier un contenu dynamique dans un littéral XML. Pour plus d’informations, consultez [expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Pour plus d’informations sur les différences entre la syntaxe de littéral XML et la syntaxe XML 1,0, consultez [littéraux XML et spécification xml 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Littéraux simples  
 Vous pouvez créer un [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objet dans votre code Visual Basic en tapant ou en collant des données XML valides. Un littéral d’élément XML retourne <xref:System.Xml.Linq.XElement> un objet. Pour plus d’informations, consultez [littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et [littéraux XML et spécification XML 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). L’exemple suivant crée un élément XML qui a plusieurs éléments enfants.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Vous pouvez créer un document XML en démarrant un littéral XML `<?xml version="1.0"?>`avec, comme illustré dans l’exemple suivant. Un littéral de document XML retourne <xref:System.Xml.Linq.XDocument> un objet. Pour plus d’informations, consultez [littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> La syntaxe du littéral XML dans Visual Basic n’est pas identique à la syntaxe de la spécification XML 1,0. Pour plus d’informations, consultez [littéraux XML et spécification xml 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Continuation de ligne  
 Un littéral XML peut s’étendre sur plusieurs lignes sans utiliser de caractères de continuation de ligne (séquence-trait de soulignement-entrée). Cela facilite la comparaison des littéraux XML dans le code avec des documents XML.  
  
 Le compilateur traite les caractères de continuation de ligne dans le cadre d’un littéral XML. Par conséquent, vous devez utiliser la séquence espace-trait de soulignement-entrée uniquement lorsqu' [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] elle appartient à l’objet.  
  
 Toutefois, vous avez besoin de caractères de continuation de ligne si vous avez une expression multiligne dans une expression incorporée. Pour plus d’informations, consultez [expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Incorporation de requêtes dans des littéraux XML  
 Vous pouvez utiliser une requête dans une expression incorporée. Lorsque vous effectuez cette opération, les éléments retournés par la requête sont ajoutés à l’élément XML. Cela vous permet d’ajouter du contenu dynamique, tel que le résultat de la requête d’un utilisateur, à un littéral XML.  
  
 Par exemple, le code suivant utilise une requête incorporée pour créer des éléments XML à partir des `phoneNumbers2` membres du tableau, puis ajouter ces éléments en `contact2`tant qu’enfants de.  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Comment le compilateur crée des objets à partir de littéraux XML  
 Le compilateur de Visual Basic traduit les littéraux XML en appels aux constructeurs équivalents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour générer l' [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objet. Par exemple, le compilateur Visual Basic traduira l’exemple de code suivant en un appel au <xref:System.Xml.Linq.XProcessingInstruction> constructeur pour l’instruction de version XML, les appels <xref:System.Xml.Linq.XElement> au constructeur pour `<contact>`, `<name>`et `<phone>` les éléments et les appels au <xref:System.Xml.Linq.XAttribute> constructeur pour l' `type` attribut. En particulier, étant donné les attributs de l’exemple suivant, le compilateur Visual Basic appellera <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> deux fois le constructeur. La première `type` passera la valeur pour le `name` paramètre et la valeur `home` pour le `value` paramètre. La seconde passera `type` également la valeur pour le `name` paramètre, mais la valeur `work` pour le `value` paramètre.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md)
