---
title: 'Comment : déclarer des événements personnalisés pour éviter les blocages'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 8d73d9c4590afb33e7176f647069cafcb3a9d7d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345146"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Comment : déclarer des événements personnalisés pour éviter les blocages (Visual Basic)
Dans certains cas, il est important qu’un gestionnaire d’événements ne bloque pas les gestionnaires d’événements suivants. Les événements personnalisés permettent à l’événement d’appeler ses gestionnaires d’événements de façon asynchrone.  
  
 Par défaut, le champ de magasin de stockage d’une déclaration d’événement est un délégué multicast qui combine en série tous les gestionnaires d’événements. Cela signifie que si un gestionnaire prend beaucoup de temps pour s’exécuter, il bloque les autres gestionnaires jusqu’à ce qu’il se termine. (Les gestionnaires d’événements de comportement correct ne doivent jamais exécuter des opérations longues ou potentiellement bloquantes.)  
  
 Au lieu d’utiliser l’implémentation par défaut des événements fournis par Visual Basic, vous pouvez utiliser un événement personnalisé pour exécuter les gestionnaires d’événements de façon asynchrone.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, l’accesseur `AddHandler` ajoute le délégué pour chaque gestionnaire de l’événement `Click` à un <xref:System.Collections.ArrayList> stocké dans le champ `EventHandlerList`.  
  
 Lorsque le code déclenche l’événement `Click`, l’accesseur `RaiseEvent` appelle tous les délégués de gestionnaires d’événements de façon asynchrone à l’aide de la méthode <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>. Cette méthode appelle chaque gestionnaire sur un thread de travail et retourne immédiatement, de sorte que les gestionnaires ne peuvent pas s’interfacer mutuellement.  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Guide pratique : déclarer des événements personnalisés pour économiser la mémoire](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
