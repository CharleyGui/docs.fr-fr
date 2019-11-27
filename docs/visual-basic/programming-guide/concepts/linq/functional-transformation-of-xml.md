---
title: Transformation fonctionnelle de données XML
ms.date: 07/20/2015
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
ms.openlocfilehash: 7e029fd562ae3f221a8aaef40f332a1e3fa896eb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353426"
---
# <a name="functional-transformation-of-xml-visual-basic"></a>Transformation fonctionnelle de XML (Visual Basic)
Cette rubrique traite de l'approche de transformation fonctionnelle pure permettant de modifier des documents XML et l'oppose à une approche procédurale.  
  
## <a name="modifying-an-xml-document"></a>Modification d'un document XML  
 L'une des tâches les plus courantes pour un programmeur XML consiste à transformer du code XML d'une forme en une autre. La forme d'un document XML est la structure du document, qui inclut les éléments suivants :  
  
- la hiérarchie exprimée par le document ;  
  
- les noms des éléments et des attributs ;  
  
- les types de données des éléments et attributs.  
  
 En général, l'approche la plus efficace pour transformer du code XML d'une forme en une autre consiste à utiliser la transformation fonctionnelle pure. Avec cette approche, la principale tâche du programmeur est de créer une transformation qui est appliquée à l'ensemble du document XML (ou à un ou plusieurs nœuds strictement définis). La transformation fonctionnelle offre sans aucun doute la plus grande facilité de codage (une fois que le programmeur s'est familiarisé avec cette approche) et la plus grande facilité de maintenance du code, et elle est souvent plus compacte que les autres approches.  
  
### <a name="xml-functional-transformational-technologies"></a>Technologies de transformation fonctionnelle XML  
 Microsoft propose deux technologies de transformation fonctionnelle pour une utilisation sur des documents XML : XSLT et LINQ to XML. XSLT est pris en charge dans l'espace de noms managé <xref:System.Xml.Xsl> et dans l'implémentation COM native de MSXML. Bien que XSLT soit une technologie robuste pour la manipulation de documents XML, elle requiert un savoir-faire dans un domaine spécialisé, à savoir le langage XSLT et ses API de prise en charge.  
  
 LINQ to XML procure les outils nécessaires pour coder des transformations fonctionnelles pures de manière expressive et puissante, dans du code C# ou Visual Basic. Par exemple, bon nombre des exemples dans la documentation LINQ to XML utilisent une approche fonctionnelle pure. En outre, dans le didacticiel [: manipulation de contenu dans un document WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) , nous utilisons LINQ to XML dans une approche fonctionnelle pour manipuler des informations dans un document Microsoft Word.  
  
 Pour une comparaison plus complète des LINQ to XML avec d’autres technologies XML Microsoft, consultez [LINQ to XML différences par rapport à d’autres technologies XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 XSLT est l'outil recommandé pour les transformations centrées sur les documents lorsque le document source a une structure irrégulière. Toutefois, LINQ to XML peut également effectuer des transformations centrées sur les documents. Pour plus d’informations, consultez [Comment : utiliser des annotations pour transformer des LINQ to XML des arborescences dans un style XSLT (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Voir aussi

- [Présentation des transformations fonctionnelles pures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [LINQ to XML différences par rapport à d’autres technologies XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
