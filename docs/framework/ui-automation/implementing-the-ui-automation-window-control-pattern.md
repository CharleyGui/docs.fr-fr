---
title: Implémentation du modèle de contrôle Window d’UI Automation
description: Passez en revue les recommandations et les conventions pour implémenter le modèle de contrôle Window dans UI Automation. Connaître les membres requis pour l’interface IWindowProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: b43884393974e6f2863da6a4a5ca8f305e5a160c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286095"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="6bf56-104">Implémentation du modèle de contrôle Window d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="6bf56-104">Implementing the UI Automation Window Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="6bf56-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="6bf56-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6bf56-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="6bf56-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="6bf56-107">Cette rubrique présente des conventions et des directives pour implémenter <xref:System.Windows.Automation.Provider.IWindowProvider>, notamment des informations sur les propriétés, méthodes et événements <xref:System.Windows.Automation.WindowPattern> .</span><span class="sxs-lookup"><span data-stu-id="6bf56-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="6bf56-108">Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="6bf56-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="6bf56-109">Le <xref:System.Windows.Automation.WindowPattern> modèle de contrôle est utilisé pour prendre en charge des contrôles qui fournissent des fonctionnalités fondamentales basées sur les fenêtres dans une interface graphique utilisateur (GUI) traditionnelle.</span><span class="sxs-lookup"><span data-stu-id="6bf56-109">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI).</span></span> <span data-ttu-id="6bf56-110">Voici des exemples de contrôles qui doivent implémenter ce modèle de contrôle : les fenêtres d’application de niveau supérieur, les fenêtres enfants de l’interface multidocument (MDI), les contrôles de volet de fractionnement redimensionnables, les boîtes de dialogue modales et les fenêtres d’aide de bulle.</span><span class="sxs-lookup"><span data-stu-id="6bf56-110">Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="6bf56-111">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="6bf56-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="6bf56-112">Quand vous implémentez le modèle de contrôle Window, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6bf56-112">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="6bf56-113">Pour prendre en charge la possibilité de modifier la taille de la fenêtre et la position de l’écran à l’aide d’UI Automation, un contrôle doit implémenter <xref:System.Windows.Automation.Provider.ITransformProvider> en plus de <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="6bf56-113">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="6bf56-114">Les contrôles qui contiennent des barres de titre et des éléments de barre de titre qui permettent de déplacer, redimensionner, agrandir, réduire ou fermer le contrôle sont généralement obligatoires pour implémenter <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="6bf56-114">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="6bf56-115">En général, les contrôles tels que les info-bulles contextuelles, les zones de liste modifiable ou les menus déroulants n’implémentent pas <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="6bf56-115">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="6bf56-116">Les fenêtres d’info-bulle se distinguent des info-bulles contextuelles de base par un bouton Fermer identique à celui des fenêtres.</span><span class="sxs-lookup"><span data-stu-id="6bf56-116">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
- <span data-ttu-id="6bf56-117">Le mode plein écran n’est pas pris en charge par IWindowProvider, car il est propre à la fonctionnalité d’une application et n’est pas un comportement standard de fenêtre.</span><span class="sxs-lookup"><span data-stu-id="6bf56-117">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>

## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="6bf56-118">Membres obligatoires pour IWindowProvider</span><span class="sxs-lookup"><span data-stu-id="6bf56-118">Required Members for IWindowProvider</span></span>  

 <span data-ttu-id="6bf56-119">Les propriétés, méthodes et événements suivants sont obligatoires pour l’interface IWindowProvider.</span><span class="sxs-lookup"><span data-stu-id="6bf56-119">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="6bf56-120">Membre obligatoire</span><span class="sxs-lookup"><span data-stu-id="6bf56-120">Required member</span></span>|<span data-ttu-id="6bf56-121">Type de membre</span><span class="sxs-lookup"><span data-stu-id="6bf56-121">Member type</span></span>|<span data-ttu-id="6bf56-122">Notes</span><span class="sxs-lookup"><span data-stu-id="6bf56-122">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="6bf56-123">Propriété</span><span class="sxs-lookup"><span data-stu-id="6bf56-123">Property</span></span>|<span data-ttu-id="6bf56-124">None</span><span class="sxs-lookup"><span data-stu-id="6bf56-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="6bf56-125">Propriété</span><span class="sxs-lookup"><span data-stu-id="6bf56-125">Property</span></span>|<span data-ttu-id="6bf56-126">None</span><span class="sxs-lookup"><span data-stu-id="6bf56-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="6bf56-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="6bf56-127">Property</span></span>|<span data-ttu-id="6bf56-128">None</span><span class="sxs-lookup"><span data-stu-id="6bf56-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="6bf56-129">Propriété</span><span class="sxs-lookup"><span data-stu-id="6bf56-129">Property</span></span>|<span data-ttu-id="6bf56-130">None</span><span class="sxs-lookup"><span data-stu-id="6bf56-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="6bf56-131">Propriété</span><span class="sxs-lookup"><span data-stu-id="6bf56-131">Property</span></span>|<span data-ttu-id="6bf56-132">None</span><span class="sxs-lookup"><span data-stu-id="6bf56-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="6bf56-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="6bf56-133">Property</span></span>|<span data-ttu-id="6bf56-134">None</span><span class="sxs-lookup"><span data-stu-id="6bf56-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="6bf56-135">Méthode</span><span class="sxs-lookup"><span data-stu-id="6bf56-135">Method</span></span>|<span data-ttu-id="6bf56-136">None</span><span class="sxs-lookup"><span data-stu-id="6bf56-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="6bf56-137">Méthode</span><span class="sxs-lookup"><span data-stu-id="6bf56-137">Method</span></span>|<span data-ttu-id="6bf56-138">None</span><span class="sxs-lookup"><span data-stu-id="6bf56-138">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="6bf56-139">Méthode</span><span class="sxs-lookup"><span data-stu-id="6bf56-139">Method</span></span>|<span data-ttu-id="6bf56-140">None</span><span class="sxs-lookup"><span data-stu-id="6bf56-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="6bf56-141">Événement</span><span class="sxs-lookup"><span data-stu-id="6bf56-141">Event</span></span>|<span data-ttu-id="6bf56-142">None</span><span class="sxs-lookup"><span data-stu-id="6bf56-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="6bf56-143">Événement</span><span class="sxs-lookup"><span data-stu-id="6bf56-143">Event</span></span>|<span data-ttu-id="6bf56-144">None</span><span class="sxs-lookup"><span data-stu-id="6bf56-144">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="6bf56-145">Événement</span><span class="sxs-lookup"><span data-stu-id="6bf56-145">Event</span></span>|<span data-ttu-id="6bf56-146">N’est pas nécessairement défini sur <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="6bf56-146">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="6bf56-147">Exceptions</span><span class="sxs-lookup"><span data-stu-id="6bf56-147">Exceptions</span></span>  

 <span data-ttu-id="6bf56-148">Les fournisseurs doivent lever les exceptions suivantes.</span><span class="sxs-lookup"><span data-stu-id="6bf56-148">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="6bf56-149">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="6bf56-149">Exception type</span></span>|<span data-ttu-id="6bf56-150">Condition</span><span class="sxs-lookup"><span data-stu-id="6bf56-150">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="6bf56-151">-Lorsqu’un contrôle ne prend pas en charge un comportement demandé.</span><span class="sxs-lookup"><span data-stu-id="6bf56-151">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="6bf56-152">-Lorsque le paramètre n’est pas un nombre valide.</span><span class="sxs-lookup"><span data-stu-id="6bf56-152">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6bf56-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bf56-153">See also</span></span>

- [<span data-ttu-id="6bf56-154">Vue d'ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="6bf56-154">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="6bf56-155">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="6bf56-155">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="6bf56-156">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="6bf56-156">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="6bf56-157">Vue d’ensemble de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="6bf56-157">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="6bf56-158">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="6bf56-158">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
