---
title: 'Comment : déclarer des événements personnalisés pour éviter les blocages'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: a9f9529d468a036d81c4e436429cbdb3207efd6e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405155"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Comment : déclarer des événements personnalisés pour éviter les blocages (Visual Basic)
Dans certains cas, il est important qu’un gestionnaire d’événements ne bloque pas les gestionnaires d’événements suivants. Les événements personnalisés permettent à l’événement d’appeler ses gestionnaires d’événements de façon asynchrone.  
  
 Par défaut, le champ de magasin de stockage d’une déclaration d’événement est un délégué multicast qui combine en série tous les gestionnaires d’événements. Cela signifie que si un gestionnaire prend beaucoup de temps pour s’exécuter, il bloque les autres gestionnaires jusqu’à ce qu’il se termine. (Les gestionnaires d’événements de comportement correct ne doivent jamais exécuter des opérations longues ou potentiellement bloquantes.)  
  
 Au lieu d’utiliser l’implémentation par défaut des événements fournis par Visual Basic, vous pouvez utiliser un événement personnalisé pour exécuter les gestionnaires d’événements de façon asynchrone.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, l' `AddHandler` accesseur ajoute le délégué pour chaque gestionnaire de l' `Click` événement à un <xref:System.Collections.ArrayList> stocké dans le `EventHandlerList` champ.  
  
 Lorsque le code déclenche l' `Click` événement, l' `RaiseEvent` accesseur appelle tous les délégués de gestionnaires d’événements de façon asynchrone à l’aide de la <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> méthode. Cette méthode appelle chaque gestionnaire sur un thread de travail et retourne immédiatement, de sorte que les gestionnaires ne peuvent pas s’interfacer mutuellement.  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [Événements](index.md)
- [Comment : déclarer des événements personnalisés pour économiser la mémoire](how-to-declare-custom-events-to-conserve-memory.md)
