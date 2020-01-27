---
title: Limitations de la propriété intervalle du composant Timer
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 15626a53f0541ff79e2098377d9dfdb4626ac155
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745234"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a>Restrictions relatives à la propriété Interval du composant Timer Windows Forms
Le composant Windows Forms <xref:System.Windows.Forms.Timer> a une propriété <xref:System.Windows.Forms.Timer.Interval%2A> qui spécifie le nombre de millisecondes qui passent entre un événement de minuterie et le suivant. À moins que le composant ne soit désactivé, un minuteur continue de recevoir l’événement <xref:System.Windows.Forms.Timer.Tick> à des intervalles de temps à peu près égaux.  
  
 Ce composant est conçu pour un environnement Windows Forms. Si vous avez besoin d’un minuteur adapté à un environnement de serveur, consultez l’article [Introduction aux minuteurs serveur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="the-interval-property"></a>La propriété Interval  
 La propriété <xref:System.Windows.Forms.Timer.Interval%2A> présente quelques limitations à prendre en compte lors de la programmation d’un composant <xref:System.Windows.Forms.Timer> :  
  
- Si votre application ou une autre application fait des demandes importantes sur le système (par exemple, des boucles longues, des calculs intensifs ou un accès à un lecteur, un réseau ou un port), votre application peut ne pas recevoir d’événements de minuteur aussi souvent que la propriété <xref:System.Windows.Forms.Timer.Interval%2A> spécifie.  
  
- Il n’est pas garanti que l’intervalle s’écoule exactement dans le temps. Pour garantir la précision, la minuterie doit vérifier l’horloge système si nécessaire, plutôt que d’essayer d’effectuer le suivi du temps accumulé en interne.  
  
- La précision de la propriété de <xref:System.Windows.Forms.Timer.Interval%2A> est exprimée en millisecondes. Certains ordinateurs fournissent un compteur haute résolution dont la résolution est supérieure à millisecondes. La disponibilité d’un tel compteur dépend du matériel du processeur de votre ordinateur.
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Timer>
- [Timer, composant](timer-component-windows-forms.md)
- [Vue d’ensemble du composant Timer](timer-component-overview-windows-forms.md)
