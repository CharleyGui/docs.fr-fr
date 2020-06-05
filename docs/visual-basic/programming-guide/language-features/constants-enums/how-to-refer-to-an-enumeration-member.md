---
title: "Comment : faire référence à un membre d'énumération"
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 66c527bd4ba4721065de8fca8534fe652d0139be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414412"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a>Comment : faire référence à un membre d'énumération (Visual Basic)
Les énumérations offrent un moyen pratique d’utiliser des ensembles de constantes associées et d’associer des valeurs constantes à des noms. Par exemple, vous pouvez déclarer une énumération pour un ensemble de constantes entières associées aux jours de la semaine puis utiliser les noms des jours au lieu de leur valeur entière dans votre code.  
  
 Vous pouvez éviter d’utiliser des noms qualifiés complets avec l' `Imports` instruction. Pour plus d’informations, consultez [énumérations et qualification de nom](enumerations-and-name-qualification.md).  
  
### <a name="to-refer-to-an-enumeration-member"></a>Pour faire référence à un membre d’énumération  
  
- Qualifiez le nom de membre avec l’énumération. Par exemple, l’exemple suivant affecte le `Saturday` membre de l' `FirstDayOfWeek` énumération à la variable `DayValue` .  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a>Voir aussi

- [How to: Declare an, énumération](how-to-declare-enumerations.md)
- [Énumérations et qualification de noms](enumerations-and-name-qualification.md)
- [Comment : itérer au sein d'une énumération dans Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Comment : déterminer la chaîne associée à une valeur d'énumération](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Quand utiliser une énumération](when-to-use-an-enumeration.md)
