---
title: Ordre des événements
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 618ac5a6a6a32ae1a53fc60ac80700d7648c81a7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734861"
---
# <a name="order-of-events-in-windows-forms"></a>Ordre des événements dans les Windows Forms
L'ordre dans lequel les événements sont déclenchés dans les applications Windows Forms est particulièrement intéressant pour les développeurs soucieux de gérer chacun de ces événements tour à tour. Quand une situation nécessite une gestion méticuleuse des événements, par exemple quand vous redessinez certaines parties du formulaire, une connaissance de l'ordre exact dans lequel les événements sont déclenchés au moment de l'exécution est nécessaire. Cette rubrique fournit des détails sur l'ordre des événements durant plusieurs phases importantes de la durée de vie des applications et des contrôles. Pour plus d’informations sur l’ordre des événements d’entrée de souris, consultez [événements de souris dans Windows Forms](mouse-events-in-windows-forms.md). Pour obtenir une vue d’ensemble des événements dans Windows Forms, consultez [vue d’ensemble des événements](events-overview-windows-forms.md). Pour plus d’informations sur la composition de gestionnaires d’événements, consultez [vue d’ensemble des gestionnaires d’événements](event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Événements de démarrage et d'arrêt des applications  
 Les classes <xref:System.Windows.Forms.Form> et <xref:System.Windows.Forms.Control> exposent un ensemble d'événements liés au démarrage et à l'arrêt de l'application. Lors du démarrage d'une application Windows Forms, les événements de démarrage du formulaire principal sont déclenchés dans l'ordre suivant :  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 Lors de la fermeture d'une application, les événements d'arrêt du formulaire principal sont déclenchés dans l'ordre suivant :  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 L'événement <xref:System.Windows.Forms.Application.ApplicationExit> de la classe <xref:System.Windows.Forms.Application> est déclenché après les événements d'arrêt du formulaire principal.  
  
> [!NOTE]
> Visual Basic 2005 fournit des événements d'application supplémentaires, tels que <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> et <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.  
  
## <a name="focus-and-validation-events"></a>Événements de focus et de validation  
 Quand vous modifiez le focus à l'aide du clavier (Tab, Maj+Tab, etc.) en appelant la méthode <xref:System.Windows.Forms.Control.Select%2A> ou <xref:System.Windows.Forms.Control.SelectNextControl%2A> ou en affectant le formulaire actuel comme valeur de la propriété <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A>, les événements de focus de la classe <xref:System.Windows.Forms.Control> se produisent dans l'ordre suivant :  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 Quand vous modifiez le focus à l'aide de la souris ou en appelant la méthode <xref:System.Windows.Forms.Control.Focus%2A>, les événements de focus de la classe <xref:System.Windows.Forms.Control> se produisent dans l'ordre suivant :  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Voir aussi

- [Création de gestionnaires d’événements dans les Windows Forms](creating-event-handlers-in-windows-forms.md)
