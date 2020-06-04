---
title: 'Guide pratique : itérer au sein d’une énumération'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: fb6fbdd45ca0e84ccb9fc55296d78e3867d5fe25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414425"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Comment : itérer au sein d'une énumération dans Visual Basic
Les énumérations offrent un moyen pratique de travailler avec des ensembles de constantes connexes et d’associer des valeurs de constantes à des noms. Pour itérer au sein d’une énumération, vous pouvez la déplacer dans un tableau à l’aide de la <xref:System.Enum.GetValues%2A> méthode. Vous pouvez également itérer au sein d’une énumération à l’aide d’une `For...Each` instruction, en utilisant la <xref:System.Enum.GetNames%2A> <xref:System.Enum.GetValues%2A> méthode ou pour extraire la chaîne ou la valeur numérique.  
  
### <a name="to-iterate-through-an-enumeration"></a>Pour itérer au sein d’une énumération  
  
- Déclarez un tableau et convertissez-le en l’énumération avec la <xref:System.Enum.GetValues%2A> méthode avant de passer le tableau comme vous le feriez pour toute autre variable. L’exemple suivant affiche chaque membre de l’énumération au <xref:Microsoft.VisualBasic.FirstDayOfWeek> fur et à mesure qu’il itère au sein de l’énumération.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des énumérations](enumerations-overview.md)
- [How to: Declare an, énumération](how-to-declare-enumerations.md)
- [Quand utiliser une énumération](when-to-use-an-enumeration.md)
- [Comment : déterminer la chaîne associée à une valeur d'énumération](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Comment : faire référence à un membre d'énumération](how-to-refer-to-an-enumeration-member.md)
- [Énumérations et qualification de noms](enumerations-and-name-qualification.md)
- [Tableaux](../arrays/index.md)
