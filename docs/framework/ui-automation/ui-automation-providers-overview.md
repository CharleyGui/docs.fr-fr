---
title: Vue d'ensemble des fournisseurs UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 1ffb8101ba0182c8ff11667f59d9bc10c5ffe670
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629557"
---
# <a name="ui-automation-providers-overview"></a>Vue d'ensemble des fournisseurs UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Les fournisseurs UI Automation permettent aux contrôles de communiquer avec les applications clientes UI Automation. En général, chaque contrôle ou autre élément distinct d’une [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] est représenté par un fournisseur. Le fournisseur expose des informations sur l’élément et peut implémenter des modèles de contrôle pour permettre à l’application cliente d’interagir avec le contrôle.  
  
 Les applications clientes n’ont généralement pas besoin de travailler directement avec des fournisseurs. La plupart des contrôles standard dans les applications qui utilisent les infrastructures [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]ou [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] sont automatiquement exposés au système [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Les applications qui implémentent des contrôles personnalisés peuvent également implémenter des fournisseurs [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour ces contrôles, et les applications clientes n’ont pas à utiliser de procédures spéciales pour y accéder.  
  
 Cette rubrique fournit une vue d’ensemble de la manière dont les développeurs de contrôles implémentent des fournisseurs [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , en particulier pour les contrôles des fenêtres [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] .  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Types de fournisseurs  
 Les fournisseurs UI Automation sont divisés en deux catégories : les fournisseurs côté client et les fournisseurs côté serveur.  
  
### <a name="client-side-providers"></a>Fournisseurs côté client  
 Les fournisseurs côté client sont implémentés par les clients UI Automation pour communiquer avec une application qui ne prend pas en charge, ou ne prend pas entièrement en charge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Les fournisseurs côté client communiquent généralement avec le serveur à travers la limite de processus en envoyant et en recevant des messages Windows.  
  
 Étant donné que les fournisseurs UI Automation [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]pour les contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] , Windows Forms ou les applications sont fournis dans le cadre du système d’exploitation, les applications clientes doivent rarement implémenter leurs propres fournisseurs, et cette vue d’ensemble ne les couvre pas nouveau.  
  
### <a name="server-side-providers"></a>Fournisseurs côté serveur  
 Les fournisseurs côté serveur sont implémentés par des contrôles personnalisés ou par des applications basées sur une infrastructure d’interface [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]utilisateur autre que, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]Windows Forms ou.  
  
 Les fournisseurs côté serveur communiquent avec les applications clientes à travers la limite de processus en exposant des interfaces au système de base [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui, à son tour, prend en charge les demandes des clients.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Concepts de fournisseur UI Automation  
 Cette section fournit de brèves explications sur certains concepts clés que vous devez comprendre pour pouvoir implémenter des fournisseurs UI Automation.  
  
### <a name="elements"></a>Éléments  
 Les éléments[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sont des éléments de l’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] visibles par les clients UI Automation. Les fenêtres d’application, les volets, les boutons, les info-bulles, les zones de liste et les éléments de liste en sont des exemples.  
  
### <a name="navigation"></a>Navigation  
 Les éléments[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sont exposés aux clients sous la forme d’une arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] construit l’arborescence en naviguant d’un élément à l’autre. La navigation est activée par les fournisseurs pour chaque élément, chacun pouvant pointer vers un parent, des frères ou des enfants.  
  
 Pour plus d’informations sur la vue client de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
### <a name="views"></a>Affichages  
 Un client peut consulter l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dans trois vues principales, telles que répertoriées dans le tableau suivant.  
  
|||  
|-|-|  
|Affichage brut|Contient tous les éléments.|  
|Vue de contrôle|Contient les éléments qui sont des contrôles.|  
|Vue de contenu|Contient les éléments disposant d’un contenu.|  
  
 Pour plus d’informations sur les vues client de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 Il incombe à l’implémentation du fournisseur de définir un élément comme élément de contenu ou élément de contrôle. Les éléments de contrôle peuvent être ou non également des éléments de contenu, mais tous les éléments de contenu sont des éléments de contrôle.  
  
### <a name="frameworks"></a>Infrastructures  
 Une infrastructure est un composant qui gère les contrôles enfants, les tests de positionnement et le rendu dans une zone de l’écran. Par exemple, une fenêtre [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] , souvent appelée HWND, peut servir d’infrastructure contenant plusieurs éléments [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , tels qu’une barre de menus, une barre d’état et des boutons.  
  
 Les contrôles conteneurs[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] , tels que les zones de liste et les arborescences, sont considérés comme des infrastructures, car ils contiennent leur propre code pour restituer des éléments enfants et effectuer des tests de positionnement sur ces derniers. En revanche, une zone de liste [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] n’est pas une infrastructure, car le rendu et les tests de positionnement sont gérés par la fenêtre [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] contenante.  
  
 L’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] d’une application peut être composée de différentes infrastructures. Par exemple, une fenêtre d’application HWND peut contenir du HTML dynamique (DHTML) qui contient à son tour un composant tel qu’une zone de liste déroulante dans un HWND.  
  
### <a name="fragments"></a>Fragments  
 Un fragment est une sous-arborescence complète d’éléments issus d’une infrastructure particulière. L’élément au niveau du nœud racine de la sous-arborescence est appelé racine de fragment. Une racine de fragment n’a pas de parent, mais elle est hébergée au sein d’une autre infrastructure, habituellement une fenêtre [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] (HWND).  
  
### <a name="hosts"></a>Hôtes  
 Le nœud racine de chaque fragment doit être hébergé dans un élément, généralement une fenêtre [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] (HWND). Le bureau est une exception et il n’est hébergé dans aucun autre élément. L’hôte d’un contrôle personnalisé est le HWND du contrôle lui-même, et non pas la fenêtre d’application ni aucune autre fenêtre susceptible de contenir des groupes de contrôles de niveau supérieur.  
  
 L’hôte d’un fragment joue un rôle important dans l’offre des services [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Il permet la navigation vers la racine de fragment et fournit des propriétés par défaut afin que le fournisseur personnalisé n’ait pas à les implémenter.  
  
## <a name="see-also"></a>Voir aussi

- [Implémentation de fournisseur UI Automation côté serveur](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
