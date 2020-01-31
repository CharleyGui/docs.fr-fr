---
title: Capture de la souris
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 10583f074831b16dce3c713b4ac9a76c7005c9f5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741017"
---
# <a name="mouse-capture-in-windows-forms"></a>Capture de la souris dans les Windows Forms
*La capture de la souris* fait référence à lorsqu’un contrôle prend la commande de toutes les entrées de la souris. Lorsqu’un contrôle a capturé la souris, il reçoit l’entrée de la souris, que le pointeur se trouve dans ses limites ou non.  
  
## <a name="setting-mouse-capture"></a>Configuration de la capture de la souris  
 Dans Windows Forms la souris est capturée par le contrôle lorsque l’utilisateur appuie sur un bouton de la souris sur un contrôle et que la souris est relâchée par le contrôle lorsque l’utilisateur relâche le bouton de la souris.  
  
 La propriété <xref:System.Windows.Forms.Control.Capture%2A> de la classe <xref:System.Windows.Forms.Control> spécifie si un contrôle a capturé la souris. Pour déterminer quand un contrôle perd la capture de la souris, gérez l’événement <xref:System.Windows.Forms.Control.MouseCaptureChanged>.  
  
 Seule la fenêtre de premier plan peut capturer la souris. Quand une fenêtre d’arrière-plan tente de capturer la souris, la fenêtre reçoit des messages uniquement pour les événements de souris qui se produisent lorsque le pointeur de la souris se trouve dans la partie visible de la fenêtre. De même, même si la fenêtre de premier plan a capturé la souris, l’utilisateur peut toujours cliquer sur une autre fenêtre, en l’amenant au premier plan. Lorsque la souris est capturée, les touches de raccourci ne fonctionnent pas.  
  
## <a name="see-also"></a>Voir aussi

- [Entrée de la souris dans une application Windows Forms](mouse-input-in-a-windows-forms-application.md)
