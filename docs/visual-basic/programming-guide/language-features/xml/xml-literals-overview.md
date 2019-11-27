---
title: Vue d'ensemble des littéraux XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: e5d2465d145f4059600121c6cef30bb2c74a8c1c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346199"
---
# <a name="xml-literals-overview-visual-basic"></a>Vue d'ensemble des littéraux XML (Visual Basic)
Un *littéral XML* vous permet d’incorporer du code XML directement dans votre code Visual Basic. La syntaxe de littéral XML représente [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objets et est similaire à la syntaxe XML 1,0. Il est ainsi plus facile de créer des éléments et des documents XML par programmation, car votre code a la même structure que le XML final.  
  
 Visual Basic compile des littéraux XML en objets [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit un modèle d’objet simple pour la création et la manipulation de XML, et ce modèle s’intègre parfaitement à [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Pour plus d'informations, consultez <xref:System.Xml.Linq.XElement>.  
  
 Vous pouvez incorporer une expression Visual Basic dans un littéral XML. Au moment de l’exécution, votre application crée un objet [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour chaque littéral, en incorporant les valeurs des expressions incorporées. Cela vous permet de spécifier un contenu dynamique dans un littéral XML. Pour plus d’informations, consultez [expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Pour plus d’informations sur les différences entre la syntaxe de littéral XML et la syntaxe XML 1,0, consultez [littéraux XML et spécification xml 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Littéraux simples  
 Vous pouvez créer un objet [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dans votre code Visual Basic en tapant ou en collant des données XML valides. Un littéral d’élément XML retourne un objet <xref:System.Xml.Linq.XElement>. Pour plus d’informations, consultez [littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et [littéraux XML et spécification XML 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). L’exemple suivant crée un élément XML qui a plusieurs éléments enfants.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Vous pouvez créer un document XML en démarrant un littéral XML avec `<?xml version="1.0"?>`, comme illustré dans l’exemple suivant. Un littéral de document XML retourne un objet <xref:System.Xml.Linq.XDocument>. Pour plus d’informations, consultez [littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> La syntaxe du littéral XML dans Visual Basic n’est pas identique à la syntaxe de la spécification XML 1,0. Pour plus d’informations, consultez [littéraux XML et spécification xml 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Continuation de ligne  
 Un littéral XML peut s’étendre sur plusieurs lignes sans utiliser de caractères de continuation de ligne (séquence-trait de soulignement-entrée). Cela facilite la comparaison des littéraux XML dans le code avec des documents XML.  
  
 Le compilateur traite les caractères de continuation de ligne dans le cadre d’un littéral XML. Par conséquent, vous devez utiliser la séquence espace-trait de soulignement-entrée uniquement lorsqu’elle appartient à l’objet [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Toutefois, vous avez besoin de caractères de continuation de ligne si vous avez une expression multiligne dans une expression incorporée. Pour plus d’informations, consultez [expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Incorporation de requêtes dans des littéraux XML  
 Vous pouvez utiliser une requête dans une expression incorporée. Lorsque vous effectuez cette opération, les éléments retournés par la requête sont ajoutés à l’élément XML. Cela vous permet d’ajouter du contenu dynamique, tel que le résultat de la requête d’un utilisateur, à un littéral XML.  
  
 Par exemple, le code suivant utilise une requête incorporée pour créer des éléments XML à partir des membres du tableau `phoneNumbers2`, puis ajouter ces éléments en tant qu’enfants de `contact2`.  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Comment le compilateur crée des objets à partir de littéraux XML  
 Le compilateur de Visual Basic traduit les littéraux XML en appels aux constructeurs [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] équivalents pour générer l’objet [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Par exemple, le compilateur Visual Basic traduira l’exemple de code suivant en un appel au constructeur <xref:System.Xml.Linq.XProcessingInstruction> pour l’instruction de version XML, les appels au constructeur <xref:System.Xml.Linq.XElement> pour les éléments `<contact>`, `<name>`et `<phone>`, et les appels au constructeur <xref:System.Xml.Linq.XAttribute> pour l’attribut `type`. En particulier, étant donné les attributs de l’exemple suivant, le compilateur Visual Basic appellera deux fois le constructeur <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>. Le premier passera la valeur `type` pour le paramètre `name` et la valeur `home` pour le paramètre `value`. La deuxième passe également la valeur `type` pour le paramètre `name`, mais la valeur `work` pour le paramètre `value`.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md)
