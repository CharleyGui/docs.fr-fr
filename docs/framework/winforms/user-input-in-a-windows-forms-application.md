---
title: Entrée d’utilisateur dans une application Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 8e82276f14519c4ef54948744c93014232bdff52
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734810"
---
# <a name="user-input-in-a-windows-forms-application"></a>Entrée d'utilisateur dans une application Windows Forms
Dans Windows Forms, l’entrée utilisateur est envoyée aux applications sous la forme de messages Windows. Une série de méthodes substituables traite ces messages au niveau de l’application, du formulaire et du contrôle. Lorsque ces méthodes reçoivent des messages de souris et de clavier, elles déclenchent des événements qui peuvent être gérés pour obtenir des informations sur la souris ou l’entrée au clavier. Dans de nombreux cas, Windows Forms applications peuvent traiter toutes les entrées utilisateur simplement en gérant ces événements. Dans d’autres cas, une application peut avoir besoin de substituer l’une des méthodes qui traitent les messages pour intercepter un message particulier avant qu’il ne soit reçu par l’application, le formulaire ou le contrôle.  
  
## <a name="mouse-and-keyboard-events"></a>Événements de souris et de clavier  
 Tous les contrôles Windows Forms héritent d’un ensemble d’événements liés à l’entrée de la souris et du clavier. Par exemple, un contrôle peut gérer l’événement <xref:System.Windows.Forms.Control.KeyPress> pour déterminer le code de caractère d’une touche qui a été enfoncée, ou un contrôle peut gérer l’événement <xref:System.Windows.Forms.Control.MouseClick> pour déterminer l’emplacement d’un clic de souris. Pour plus d’informations sur les événements de souris et de clavier, consultez [utilisation des événements de clavier](using-keyboard-events.md) et des [événements de souris dans Windows Forms](mouse-events-in-windows-forms.md).  
  
## <a name="methods-that-process-user-input-messages"></a>Méthodes qui traitent les messages d’entrée utilisateur  
 Les formulaires et les contrôles ont accès à l’interface <xref:System.Windows.Forms.IMessageFilter> et à un ensemble de méthodes substituables qui traitent les messages Windows à différents moments de la file d’attente de messages. Ces méthodes ont toutes un paramètre <xref:System.Windows.Forms.Message>, qui encapsule les détails de bas niveau des messages Windows. Vous pouvez implémenter ou substituer ces méthodes pour examiner le message, puis utiliser le message ou le passer au consommateur suivant dans la file d’attente de messages. Le tableau suivant présente les méthodes qui traitent tous les messages Windows dans Windows Forms.  
  
|Méthode|Remarques|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Cette méthode intercepte les messages Windows mis en file d’attente (également appelés) au niveau de l’application.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Cette méthode intercepte les messages Windows au niveau du formulaire et du contrôle avant qu’ils aient été traités.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Cette méthode traite les messages Windows au niveau du formulaire et du contrôle.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Cette méthode effectue le traitement par défaut des messages Windows au niveau du formulaire et du contrôle. Cela fournit les fonctionnalités minimales d’une fenêtre.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Cette méthode intercepte les messages au niveau du formulaire et du contrôle, une fois qu’ils ont été traités. Le bit de style de <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage> doit être défini pour que cette méthode soit appelée.|  
  
 Les messages du clavier et de la souris sont également traités par un ensemble supplémentaire de méthodes substituables qui sont spécifiques à ces types de messages. Pour plus d’informations, consultez fonctionnement de [l’entrée au clavier](how-keyboard-input-works.md) et fonctionnement [de l’entrée de la souris dans Windows Forms](how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Voir aussi

- [Entrées d’utilisateur dans les Windows Forms](user-input-in-windows-forms.md)
- [Entrée au clavier dans une application Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Entrée de la souris dans une application Windows Forms](mouse-input-in-a-windows-forms-application.md)
