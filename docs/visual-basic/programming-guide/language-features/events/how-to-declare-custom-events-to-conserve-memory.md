---
title: 'Comment : déclarer des événements personnalisés pour économiser la mémoire'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3cc2d3ea57f1a8daf704c2c929baf3f2acf78c17
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345128"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Comment : déclarer des événements personnalisés pour économiser la mémoire (Visual Basic)
Dans certains cas, il est important qu’une application conserve son utilisation de la mémoire faible. Les événements personnalisés permettent à l’application d’utiliser uniquement la mémoire pour les événements qu’elle gère.  
  
 Par défaut, lorsqu’une classe déclare un événement, le compilateur alloue de la mémoire pour un champ afin de stocker les informations sur l’événement. Si une classe possède de nombreux événements inutilisés, ils occupent inutilement de la mémoire.  
  
 Au lieu d’utiliser l’implémentation par défaut des événements fournis par Visual Basic, vous pouvez utiliser des événements personnalisés pour gérer l’utilisation de la mémoire plus attentivement.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la classe utilise une instance de la classe <xref:System.ComponentModel.EventHandlerList>, stockée dans le champ `Events`, pour stocker des informations sur les événements en cours d’utilisation. La classe <xref:System.ComponentModel.EventHandlerList> est une classe de liste optimisée conçue pour contenir des délégués.  
  
 Tous les événements de la classe utilisent le champ `Events` pour effectuer le suivi des méthodes qui gèrent chaque événement.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.EventHandlerList>
- [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Guide pratique : déclarer des événements personnalisés pour éviter les blocages](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
