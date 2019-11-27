---
title: "Comment : faire référence à un membre d'énumération"
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 01db5b84783eda45cd7867dc8fea8a69fc18b98a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354000"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a>Comment : faire référence à un membre d'énumération (Visual Basic)
Les énumérations offrent un moyen pratique d’utiliser des ensembles de constantes associées et d’associer des valeurs constantes à des noms. Par exemple, vous pouvez déclarer une énumération pour un ensemble de constantes entières associées aux jours de la semaine puis utiliser les noms des jours au lieu de leur valeur entière dans votre code.  
  
 Vous pouvez éviter d’utiliser des noms qualifiés complets avec l’instruction `Imports`. Pour plus d’informations, consultez [énumérations et qualification de nom](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-refer-to-an-enumeration-member"></a>Pour faire référence à un membre d’énumération  
  
- Qualifiez le nom de membre avec l’énumération. Par exemple, l’exemple suivant affecte le membre `Saturday` de l’énumération `FirstDayOfWeek` à la variable `DayValue`.  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a>Voir aussi

- [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Énumérations et qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Comment : itérer au sein d’une énumération dans Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Guide pratique : déterminer la chaîne associée à une valeur d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Quand utiliser une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
