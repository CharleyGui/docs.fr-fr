---
title: Événements dans les contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: c60713917b9c84aa7fad50fb1c81fc9252149ad6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745753"
---
# <a name="events-in-windows-forms-controls"></a>Événements dans les contrôles Windows Forms
Un contrôle de Windows Forms hérite de plus de 60 événements de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Celles-ci incluent l’événement <xref:System.Windows.Forms.Control.Paint>, qui provoque le dessin d’un contrôle, les événements liés à l’affichage d’une fenêtre, tels que les événements <xref:System.Windows.Forms.Control.Resize> et <xref:System.Windows.Forms.Control.Layout>, ainsi que les événements de souris et de clavier de bas niveau. Certains événements de bas niveau sont synthétisés par <xref:System.Windows.Forms.Control> en événements sémantiques, tels que les <xref:System.Windows.Forms.Control.Click> et les <xref:System.Windows.Forms.Control.DoubleClick>. Pour plus d’informations sur les événements hérités, consultez <xref:System.Windows.Forms.Control>.  
  
 Si votre contrôle personnalisé doit remplacer des fonctionnalités d’événements héritées, remplacez la méthode `On`*EventName* plutôt que d’attacher un délégué. Si le modèle d’événement dans le .NET Framework ne vous est pas familier, consultez la page [Déclencher des événements à partir d’un composant](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
## <a name="see-also"></a>Voir aussi

- [Remplacer la méthode OnPaint](overriding-the-onpaint-method.md)
- [Gestion des entrées utilisateur](handling-user-input.md)
- [Définition d’un événement](defining-an-event-in-windows-forms-controls.md)
- [Événements](../../../standard/events/index.md)
