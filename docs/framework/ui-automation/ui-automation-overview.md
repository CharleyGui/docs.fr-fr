---
title: Vue d'ensemble d'UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: a914f2c54e5e5b368533b686b1926f7f7ef2e12a
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237334"
---
# <a name="ui-automation-overview"></a>Vue d'ensemble d'UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [Windows Automation API : UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] est la nouvelle infrastructure d’accessibilité pour [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], disponible sur tous les systèmes d’exploitation qui prennent en charge [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fournit un accès par programmation à la plupart des éléments d’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] du bureau, permettant ainsi aux produits de technologie d’assistance tels que les lecteurs d’écran de fournir aux utilisateurs finaux des informations sur l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] et de manipuler l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] par d’autres moyens que l’entrée standard. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] permet également aux scripts de test automatisés d’interagir avec l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] n’active pas la communication entre les processus démarrés par différents utilisateurs via la commande **Exécuter en tant que** .  
  
 Les applications clientes UI Automation peuvent être écrites avec l’assurance qu’elles fonctionneront sur plusieurs infrastructures. Le noyau [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] masque toute les différences des infrastructures sous-jacentes à plusieurs parties de l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Par exemple, la propriété `Content` d’un bouton [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] , la propriété `Caption` d’un bouton [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] et la propriété `ALT` d’une image HTML sont toutes mappées à une seule propriété, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, dans la vue [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fournit des fonctionnalités complètes dans [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)]et [!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)].  
  
 Fournisseurs UI Automation offrent une prise en charge pour les applications clientes Microsoft Active Accessibility, via un service de liaison intégré.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Fournisseurs et clients  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] possède quatre composants principaux, répertoriés dans le tableau suivant.  
  
|Composant|Description|  
|---------------|-----------------|  
|Fournisseur (UIAutomationProvider.dll et UIAutomationTypes.dll)|Ensemble de définitions d’interface qui sont implémentées par des fournisseurs UI Automation, objets qui fournissent des informations sur les éléments d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] et qui répondent à l’entrée de programmation.|  
|API client (UIAutomationClient.dll et UIAutomationTypes.dll)|Ensemble de types destinés au code managé qui permet aux applications clientes UI Automation d’obtenir des informations sur l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] et d’envoyer l’entrée aux contrôles.|  
|UiAutomationCore.dll|Code sous-jacent (parfois appelé noyau [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ) qui gère la communication entre fournisseurs et clients.|  
|UIAutomationClientsideProviders.dll|Ensemble de fournisseurs UI Automation pour les contrôles hérités standard. (Les contrôles [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bénéficient d’une prise en charge native pour [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].) Cette prise en charge est automatiquement disponible aux applications clientes.|  
  
 Du point de vue des développeurs de logiciels, il existe deux façons d’utiliser [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: pour créer une prise en charge pour les contrôles personnalisés (à l’aide de l’API fournisseur) et pour créer des applications qui utilisent le noyau [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour communiquer avec les éléments d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] (à l’aide de l’API client). Selon votre objectif, reportez-vous à différentes parties de cette documentation. Les sections suivantes vous permettront d’approfondir les concepts et d’obtenir des connaissances pratiques.  
  
|Section|Sujet|Audience|  
|-------------|--------------------|--------------|  
|[Notions de base UI Automation](../../../docs/framework/ui-automation/index.md) (cette section)|Présentation générale des concepts.|Tout le monde.|  
|[Fournisseurs UI Automation pour le code managé](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)|Présentations et rubriques « Comment » destinées à vous aider à utiliser l’API du fournisseur.|Développeurs de contrôles.|  
|[Clients UI Automation pour le code managé](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md)|Présentations et rubriques « Comment » destinées à vous aider à utiliser l’API client.|Développeurs d’applications clientes|  
|[Modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)|Informations sur la façon dont les fournisseurs doivent implémenter les modèles de contrôle et sur les fonctionnalités disponibles aux clients.|Tout le monde.|  
|[Modèle de texte UI Automation](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)|Informations sur la façon dont les fournisseurs doivent implémenter le modèle de contrôle Text et sur les fonctionnalités disponibles aux clients.|Tout le monde.|  
|[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)|Informations sur les propriétés et les modèles de contrôle pris en charge par les différents types de contrôle.|Tout le monde.|  
  
 Le tableau suivant répertorie les espaces de noms [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les DLL qui les contiennent et le public qui les utilise.  
  
|Espace de noms|DLL référencées|Public|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Développeurs de clients UI Automation ; permettent de rechercher des objets <xref:System.Windows.Automation.AutomationElement> , de s’inscrire pour des événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et d’utiliser des modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Développeurs de fournisseurs UI Automation pour des infrastructures autres que [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Développeurs de fournisseurs UI Automation pour des infrastructures autres que [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; permettent d’implémenter le modèle de contrôle TextPattern.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Développeurs de fournisseurs UI Automation pour [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>Modèle UI Automation  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] expose chaque partie de l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aux applications clientes en tant qu’élément <xref:System.Windows.Automation.AutomationElement>. Les éléments sont contenus dans une arborescence, avec le bureau comme élément racine. Les clients peuvent filtrer l’affichage brut de l’arborescence sous la forme d’une vue de contrôle ou d’une vue de contenu. Les applications peuvent également créer des vues personnalisées.  
  
 Les objets<xref:System.Windows.Automation.AutomationElement> exposent les propriétés communes des éléments d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] qu’ils représentent. L’une de ces propriétés est le type de contrôle, qui définit son apparence et ses fonctionnalités de base comme une entité reconnaissable unique : par exemple, un bouton ou une case à cocher.  
  
 En outre, les éléments exposent des modèles de contrôle qui fournissent des propriétés spécifiques à leurs types de contrôle. Les modèles de contrôle exposent également des méthodes qui permettent aux clients d’obtenir des informations supplémentaires sur l’élément et de fournir une entrée.  
  
> [!NOTE]
>  Il n’existe pas de correspondance bijective entre les types de contrôle et les modèles de contrôle. Un modèle de contrôle peut être pris en charge par plusieurs types de contrôle, et un contrôle peut prendre en charge plusieurs modèles de contrôle, dont chacun expose différents aspects de son comportement. Par exemple, une zone de liste déroulante possède au moins deux modèles de contrôle : un qui représente sa capacité de développement et de réduction, et l’autre qui représente le mécanisme de sélection. Pour découvrir les caractéristiques spécifiques, consultez [UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fournit également des informations aux applications clientes via des événements. Contrairement à [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)], les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ne reposent pas sur un mécanisme de diffusion. Les clients[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’inscrivent pour des notifications d’événements spécifiques et peuvent demander que des propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] spécifiques et des informations de modèle de contrôle soient passées à leurs gestionnaires d’événements. En outre, un événement [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] contient une référence à l’élément qui l’a déclenché. Les fournisseurs peuvent améliorer les performances en déclenchant des événements de manière sélective, selon que des clients les écoutent ou non.  
  
## <a name="see-also"></a>Voir aussi

- [Présentation de l’arborescence UI Automation](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Vue d’ensemble des modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Vue d’ensemble des propriétés UI Automation](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)
- [Vue d’ensemble des événements UI Automation](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
- [Vue d’ensemble de la sécurité UI Automation](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
