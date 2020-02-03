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
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="c4482-102">Ordre des événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c4482-102">Order of Events in Windows Forms</span></span>
<span data-ttu-id="c4482-103">L'ordre dans lequel les événements sont déclenchés dans les applications Windows Forms est particulièrement intéressant pour les développeurs soucieux de gérer chacun de ces événements tour à tour.</span><span class="sxs-lookup"><span data-stu-id="c4482-103">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="c4482-104">Quand une situation nécessite une gestion méticuleuse des événements, par exemple quand vous redessinez certaines parties du formulaire, une connaissance de l'ordre exact dans lequel les événements sont déclenchés au moment de l'exécution est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c4482-104">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="c4482-105">Cette rubrique fournit des détails sur l'ordre des événements durant plusieurs phases importantes de la durée de vie des applications et des contrôles.</span><span class="sxs-lookup"><span data-stu-id="c4482-105">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="c4482-106">Pour plus d’informations sur l’ordre des événements d’entrée de souris, consultez [événements de souris dans Windows Forms](mouse-events-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c4482-106">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="c4482-107">Pour obtenir une vue d’ensemble des événements dans Windows Forms, consultez [vue d’ensemble des événements](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c4482-107">For an overview of events in Windows Forms, see [Events Overview](events-overview-windows-forms.md).</span></span> <span data-ttu-id="c4482-108">Pour plus d’informations sur la composition de gestionnaires d’événements, consultez [vue d’ensemble des gestionnaires d’événements](event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c4482-108">For details about the makeup of event handlers, see [Event Handlers Overview](event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="c4482-109">Événements de démarrage et d'arrêt des applications</span><span class="sxs-lookup"><span data-stu-id="c4482-109">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="c4482-110">Les classes <xref:System.Windows.Forms.Form> et <xref:System.Windows.Forms.Control> exposent un ensemble d'événements liés au démarrage et à l'arrêt de l'application.</span><span class="sxs-lookup"><span data-stu-id="c4482-110">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="c4482-111">Lors du démarrage d'une application Windows Forms, les événements de démarrage du formulaire principal sont déclenchés dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="c4482-111">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="c4482-112">Lors de la fermeture d'une application, les événements d'arrêt du formulaire principal sont déclenchés dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="c4482-112">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="c4482-113">L'événement <xref:System.Windows.Forms.Application.ApplicationExit> de la classe <xref:System.Windows.Forms.Application> est déclenché après les événements d'arrêt du formulaire principal.</span><span class="sxs-lookup"><span data-stu-id="c4482-113">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4482-114">Visual Basic 2005 fournit des événements d'application supplémentaires, tels que <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> et <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4482-114">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="c4482-115">Événements de focus et de validation</span><span class="sxs-lookup"><span data-stu-id="c4482-115">Focus and Validation Events</span></span>  
 <span data-ttu-id="c4482-116">Quand vous modifiez le focus à l'aide du clavier (Tab, Maj+Tab, etc.) en appelant la méthode <xref:System.Windows.Forms.Control.Select%2A> ou <xref:System.Windows.Forms.Control.SelectNextControl%2A> ou en affectant le formulaire actuel comme valeur de la propriété <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A>, les événements de focus de la classe <xref:System.Windows.Forms.Control> se produisent dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="c4482-116">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="c4482-117">Quand vous modifiez le focus à l'aide de la souris ou en appelant la méthode <xref:System.Windows.Forms.Control.Focus%2A>, les événements de focus de la classe <xref:System.Windows.Forms.Control> se produisent dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="c4482-117">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="c4482-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4482-118">See also</span></span>

- [<span data-ttu-id="c4482-119">Création de gestionnaires d’événements dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c4482-119">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
