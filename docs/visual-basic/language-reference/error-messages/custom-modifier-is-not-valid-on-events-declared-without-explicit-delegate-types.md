---
title: Le modificateur 'Custom' n'est pas valide pour les événements déclarés sans types délégués explicites
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 0c5a4188fedf9685afdd1cde4c1de93a0b43b919
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409779"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>Le modificateur 'Custom' n'est pas valide pour les événements déclarés sans types délégués explicites
Contrairement à un événement non personnalisé, une `Custom Event` déclaration requiert une `As` clause qui suit le nom de l’événement qui spécifie explicitement le type délégué de l’événement.  
  
 Les événements non personnalisés peuvent être définis à l’aide d’une `As` clause et d’un type délégué explicite, ou avec une liste de paramètres qui suit immédiatement le nom de l’événement.  
  
 **ID d’erreur :** BC31122  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Définissez un délégué avec la même liste de paramètres que l’événement personnalisé.  
  
     Par exemple, si le `Custom Event` a été défini par `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` , le délégué correspondant est le suivant.  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. Remplacez la liste de paramètres de l’événement personnalisé par une `As` clause qui spécifie le type délégué.  
  
     Pour continuer avec l’exemple, la `Custom Event` déclaration est réécrite comme suit.  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a>Exemple  
 Cet exemple déclare un `Custom Event` et spécifie la `As` clause requise avec un type délégué.  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Event, instruction](../statements/event-statement.md)
- [Delegate, instruction](../statements/delegate-statement.md)
- [Événements](../../programming-guide/language-features/events/index.md)
