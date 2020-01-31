---
title: Vue d'ensemble du composant Timer
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 83b52d395cdc3e3357bcf83517eab258a5c8ae08
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742773"
---
# <a name="timer-component-overview-windows-forms"></a>Vue d'ensemble du composant Timer (Windows Forms)
<xref:System.Windows.Forms.Timer> est un composant Windows Forms qui déclenche un événement à intervalles réguliers. Ce composant est conçu pour un environnement Windows Forms. Si vous avez besoin d’un minuteur adapté à un environnement de serveur, consultez l’article [Introduction aux minuteurs serveur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="key-properties-methods-and-events"></a>Propriétés, méthodes et événements de clé  
 La longueur des intervalles est définie par la propriété <xref:System.Windows.Forms.Timer.Interval%2A>, dont la valeur est exprimée en millisecondes. Lorsque le composant est activé, l’événement <xref:System.Windows.Forms.Timer.Tick> est déclenché à chaque intervalle. C’est là que vous ajoutez le code à exécuter. Pour plus d’informations, consultez [Comment : exécuter des procédures à intervalles définis à l’aide du composant Timer Windows Forms](run-procedures-at-set-intervals-with-wf-timer-component.md). Les principales méthodes du composant <xref:System.Windows.Forms.Timer> sont <xref:System.Windows.Forms.Timer.Start%2A> et <xref:System.Windows.Forms.Timer.Stop%2A>, qui activent ou désactivent le minuteur. Lorsque la minuterie est désactivée, elle est rétablie ; Il n’existe aucun moyen de suspendre un composant <xref:System.Windows.Forms.Timer>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Timer>
- [Timer, composant](timer-component-windows-forms.md)
- [Restrictions relatives à la propriété Interval du composant Timer Windows Forms](limitations-of-the-timer-component-interval-property.md)
