---
title: Problèmes liés aux threads UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: f4820d2db6275e3c1ae9b55754b8cb6fec6fcc56
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954063"
---
# <a name="ui-automation-threading-issues"></a>Problèmes liés aux threads UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 En raison de la façon dont [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] utilise les messages Windows, des conflits peuvent se produire quand une application cliente tente d’interagir avec sa propre [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] sur le thread d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Ces conflits peuvent nuire considérablement aux performances voire empêcher l’application de répondre.  
  
 Si votre application cliente est destinée à interagir avec tous les éléments du bureau, y compris sa propre [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], vous avez tout intérêt à effectuer tous les appels [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sur un thread distinct. Cela passe notamment par la localisation des éléments (par exemple, en utilisant <xref:System.Windows.Automation.TreeWalker> ou la méthode <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ) et l’utilisation de modèles de contrôle.  
  
 Il est possible d’effectuer des appels [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dans un gestionnaire d’événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , car il est toujours appelé sur un thread autre qu’un thread d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Cependant, quand vous vous abonnez à des événements susceptibles de provenir de l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]de votre application cliente, vous devez effectuer l’appel vers <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, ou une méthode associée, sur un thread autre qu’un thread d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Supprimez les gestionnaires d’événements situés sur un même thread.
