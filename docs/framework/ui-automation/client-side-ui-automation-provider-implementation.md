---
title: Implémentation de fournisseur UI Automation côté client
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 03df282022c39673a7e160dd5d79bdadd0c7adda
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433990"
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implémentation de fournisseur UI Automation côté client
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Several different [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] frameworks are in use within Microsoft operating systems, including [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], and [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] expose aux clients des informations sur les éléments d’interface utilisateur. Toutefois, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] n’a pas connaissance des différents types de contrôle qui existent dans ces infrastructures, ni des techniques nécessaires pour en extraire les informations. En revanche, cette tâche est affectée aux objets appelés fournisseurs. Un fournisseur extrait des informations d’un contrôle spécifique, et les transmet à [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], qui les présente ensuite au client de façon cohérente.  
  
 Les fournisseurs peuvent exister côté serveur ou côté client. Un fournisseur côté serveur est implémenté par le contrôle lui-même. Les éléments[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] implémentent des fournisseurs, comme tout contrôle tiers écrit avec [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] à l’esprit.  
  
 Toutefois, les contrôles plus anciens tels que ceux de [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] et [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ne prennent pas directement en charge [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. En effet, ces contrôles sont traités par des fournisseurs qui existent dans le processus client et obtiennent des informations sur les contrôles à l’aide de la communication entre processus. C’est le cas, par exemple, avec la surveillance des messages de fenêtres à destination et en provenance des contrôles. Ces fournisseurs côté client sont parfois appelés des proxies.  
  
 Windows Vista supplies providers for standard [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] and Windows Forms controls. In addition, a fallback provider gives partial [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] support to any control that is not served by another server-side provider or proxy but has a Microsoft Active Accessibility implementation. Tous ces fournisseurs sont automatiquement chargés et disponibles pour les applications clientes.  
  
 For more information on support for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] and Windows Forms controls, see [UI Automation Support for Standard Controls](ui-automation-support-for-standard-controls.md).  
  
 Les applications peuvent également inscrire d’autres fournisseurs côté client.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>Distribution des fournisseurs côté client  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’attend à trouver des fournisseurs côté client dans un assembly de code managé. L’espace de noms de cet assembly doit avoir le même nom que l’assembly. Par exemple, un assembly appelé ContosoProxies.dll doit contenir l’espace de noms ContosoProxies. Dans l’espace de noms, créez une classe <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> . Dans l’implémentation du champ <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> statique, créez un tableau de structures <xref:System.Windows.Automation.ClientSideProviderDescription> décrivant les fournisseurs.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Inscription et configuration des fournisseurs côté client  
 Client-side providers in a dynamic-link library (DLL) are loaded by calling <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>. Aucune action supplémentaire n’est nécessaire de la part de l’application cliente pour utiliser les fournisseurs.  
  
 Les fournisseurs implémentés dans le propre code du client sont inscrits à l’aide de <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>. Cette méthode utilise comme argument un tableau de structures <xref:System.Windows.Automation.ClientSideProviderDescription> , qui spécifient chacune les propriétés suivantes :  
  
- une fonction de rappel qui crée l’objet fournisseur ;  
  
- le nom de la classe des contrôles que le fournisseur doit traiter ;  
  
- le nom d’image de l’application (généralement le nom complet du fichier exécutable) que le fournisseur doit traiter ;  
  
- les indicateurs qui déterminent la comparaison du nom de la classe aux classes de fenêtres trouvées dans l’application cible.  
  
 Les deux derniers paramètres sont facultatifs. Le client peut spécifier le nom d’image de l’application cible quand il souhaite utiliser différents fournisseurs pour différentes applications. Par exemple, le client peut utiliser un fournisseur pour un contrôle ListView [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] dans une application connue prenant en charge le modèle MultipleView, et un autre fournisseur pour un contrôle similaire dans une autre application connue n’assurant pas cette prise en charge.  
  
## <a name="see-also"></a>Voir aussi

- [Créer un fournisseur UI Automation côté client](create-a-client-side-ui-automation-provider.md)
- [Implémenter des fournisseurs UI Automation dans une application cliente](implement-ui-automation-providers-in-a-client-application.md)
