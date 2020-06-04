---
title: "'<eventname>' est un événement. Il ne peut donc pas être appelé directement"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 510fff5370e63a31ee271421c0ab6f154518899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409593"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a>'\<eventname>' est un événement. Il ne peut donc pas être appelé directement
' <`eventname`> 'est un événement et ne peut donc pas être appelé directement. Utilisez une `RaiseEvent` instruction pour déclencher un événement.  
  
 Un appel de procédure spécifie un événement pour le nom de la procédure. Un gestionnaire d’événements est une procédure, mais l’événement lui-même est un appareil de signalisation, qui doit être déclenché et géré.  
  
 **ID d’erreur :** BC32022  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Utilisez une `RaiseEvent` instruction pour signaler un événement et appeler la ou les procédures qui le gèrent.  
  
## <a name="see-also"></a>Voir aussi

- [RaiseEvent, instruction](../statements/raiseevent-statement.md)
