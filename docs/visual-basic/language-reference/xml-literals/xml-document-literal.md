---
title: Littéral de document XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: bd1b2f43fce563af431d67b3817b05c7c1048314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866026"
---
# <a name="xml-document-literal-visual-basic"></a>Littéral de document XML (Visual Basic)

Littéral représentant un <xref:System.Xml.Linq.XDocument> objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`encoding`|Optionnel. Texte littéral déclarant l’encodage utilisé par le document.|  
|`standalone`|Optionnel. Texte littéral. Doit être « oui » ou « non ».|  
|`piCommentList`|Optionnel. Liste d’instructions de traitement XML et de commentaires XML. Prend le format suivant :<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Chaque `piComment` peut être l’un des éléments suivants :<br /><br /> -   [Littéral d’instruction de traitement XML](xml-processing-instruction-literal.md).<br />-   [Littéral de commentaire XML](xml-comment-literal.md).|  
|`rootElement`|Obligatoire. Élément racine du document. Le format est l’un des éléments suivants :<br /><br /> <ul><li>[Littéral d’élément XML](xml-element-literal.md).</li><li>Expression incorporée du formulaire `<%=` `elementExp` `%>` . Le `elementExp` retourne l’un des éléments suivants :<br /><br /> <ul><li>Objet <xref:System.Xml.Linq.XElement>.</li><li>Collection qui contient un <xref:System.Xml.Linq.XElement> objet et un nombre quelconque d' <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment> objets et.</li></ul></li></ul><br /> Pour plus d’informations, consultez [expressions incorporées en XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Valeur de retour  

 Objet <xref:System.Xml.Linq.XDocument>.  
  
## <a name="remarks"></a>Notes  

 Un littéral de document XML est identifié par la déclaration XML au début du littéral. Bien que chaque littéral de document XML doive avoir un seul élément XML racine, il peut contenir un nombre quelconque d’instructions de traitement XML et de commentaires XML.  
  
 Un littéral de document XML ne peut pas apparaître dans un élément XML.  
  
> [!NOTE]
> Un littéral XML peut s’étendre sur plusieurs lignes sans utiliser de caractères de continuation de ligne. Cela vous permet de copier le contenu d’un document XML et de le coller directement dans un programme de Visual Basic.  
  
 Le compilateur Visual Basic convertit le littéral de document XML en appels <xref:System.Xml.Linq.XDocument.%23ctor%2A> aux <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructeurs et.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant crée un document XML qui a une déclaration XML, une instruction de traitement, un commentaire et un élément qui contient un autre élément.  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [Littéral d’instruction de traitement XML](xml-processing-instruction-literal.md)
- [Littéral de commentaires XML](xml-comment-literal.md)
- [Littéral d’élément XML](xml-element-literal.md)
- [Littéraux XML](index.md)
- [Création de code XML dans Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Expressions incorporées en XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
