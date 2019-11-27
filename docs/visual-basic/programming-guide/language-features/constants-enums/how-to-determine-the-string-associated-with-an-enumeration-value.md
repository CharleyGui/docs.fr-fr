---
title: "Comment : déterminer la chaîne associée à une valeur d'énumération"
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: c396a4e2ebe973f5be65c3fab5f22cdedb29be1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351132"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Comment : déterminer la chaîne associée à une valeur d'énumération (Visual Basic)
Les méthodes <xref:System.Enum.GetValues%2A> et <xref:System.Enum.GetNames%2A> vous permettent de déterminer les chaînes et les valeurs associées aux membres de l’énumération.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Pour déterminer la chaîne associée à une énumération  
  
- Utilisez la méthode <xref:System.Enum.GetNames%2A> pour récupérer les chaînes associées aux membres de l’énumération. Cet exemple déclare une énumération, `flavorEnum`, puis utilise la méthode <xref:System.Enum.GetNames%2A> pour afficher les chaînes associées à chaque membre.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Guide pratique : faire référence à un membre d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Énumérations et qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Comment : itérer au sein d’une énumération dans Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Quand utiliser une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Enum (instruction)](../../../../visual-basic/language-reference/statements/enum-statement.md)
