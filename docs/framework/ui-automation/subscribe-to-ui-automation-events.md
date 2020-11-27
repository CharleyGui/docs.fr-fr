---
title: S'abonner à des événements UI Automation
description: Consultez Comment s’abonner aux événements déclenchés par les fournisseurs UI Automation. L’exemple de code inscrit un gestionnaire d’événements pour l’événement déclenché quand un contrôle est appelé.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
ms.openlocfilehash: 9005139be69621e83efc592721a238c28ea1f6e9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252301"
---
# <a name="subscribe-to-ui-automation-events"></a>S'abonner à des événements UI Automation

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique montre comment s’abonner à des événements déclenchés par des fournisseurs UI Automation.  
  
## <a name="example"></a> Exemple  

 L’exemple de code suivant inscrit un gestionnaire d’événements pour l’événement qui est déclenché quand un contrôle tel qu’un bouton est appelé, et le supprime à la fermeture du formulaire d’application. L’événement est identifié par un <xref:System.Windows.Automation.AutomationEvent> passé comme paramètre à <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a> Exemple  

 L’exemple suivant montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour s’abonner à un événement déclenché quand le focus est modifié. L’inscription du gestionnaire d’événements est annulée dans une méthode qui peut être appelée à l’arrêt de l’application, ou quand la notification d’événements d’interface utilisateur n’est plus obligatoire.  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [Vue d'ensemble des événements UI Automation](ui-automation-events-overview.md)
