---
title: "Comment : déterminer la chaîne associée à une valeur d'énumération"
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 4138759bfbb049b77406fc536219b40d3ed9e2a5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058767"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Comment : déterminer la chaîne associée à une valeur d'énumération (Visual Basic)

Les <xref:System.Enum.GetValues%2A> <xref:System.Enum.GetNames%2A> méthodes et vous permettent de déterminer les chaînes et les valeurs associées aux membres de l’énumération.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Pour déterminer la chaîne associée à une énumération  
  
- Utilisez la <xref:System.Enum.GetNames%2A> méthode pour récupérer les chaînes associées aux membres de l’énumération. Cet exemple déclare une énumération, `flavorEnum` , puis utilise la <xref:System.Enum.GetNames%2A> méthode pour afficher les chaînes associées à chaque membre.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [How to: Declare an, énumération](how-to-declare-enumerations.md)
- [Comment : faire référence à un membre d'énumération](how-to-refer-to-an-enumeration-member.md)
- [Énumérations et qualification de noms](enumerations-and-name-qualification.md)
- [Comment : itérer au sein d'une énumération dans Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Quand utiliser une énumération](when-to-use-an-enumeration.md)
- [Enum (instruction)](../../../language-reference/statements/enum-statement.md)
