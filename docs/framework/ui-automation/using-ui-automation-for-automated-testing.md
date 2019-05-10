---
title: Utilisation d'UI Automation pour des tests automatisés
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
ms.openlocfilehash: 0e5e2252225c824dfbc9d799b29a16ab6206eb3c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630663"
---
# <a name="using-ui-automation-for-automated-testing"></a>Utilisation d'UI Automation pour des tests automatisés
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [Windows Automation API : UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette présentation explique comment [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] peut être utile en tant qu’infrastructure pour l’accès par programmation aux scénarios de tests automatisés.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fournit un modèle objet unifié qui permet à toutes les infrastructures d’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] d’exposer des fonctionnalités complexes et riches de manière accessible et facilement automatisée.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a été développé pour succéder à [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] est une infrastructure existante conçue pour fournir une solution permettant de rendre les contrôles et les applications accessibles. La technologie[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] n’a pas été conçue avec l’automation des tests à l’esprit, même si elle a évolué vers ce rôle en raison d’exigences très similaires en matière d’accessibilité et d’automation. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], en plus de fournir des solutions plus raffinées pour l’accessibilité, est également conçu pour fournir des fonctionnalités robustes pour les tests automatisés. Par exemple, [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] s’appuie sur une seule interface pour exposer des informations sur l’interface utilisateur, et collecter les informations nécessaires aux produits AT. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sépare les deux modèles.  
  
 Un fournisseur et un client sont nécessaires pour implémenter [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , et l’utiliser comme outil de test automatisé. Les fournisseurs UI Automation sont des applications telles que Microsoft Word, Excel et d’autres applications ou contrôles tiers basés sur le système d’exploitation [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] . Les clients UI Automation incluent des scripts de tests automatisés et des applications de technologie d’assistance.  
  
> [!NOTE]
>  L’objectif de cette vue d’ensemble est de présenter les nouvelles fonctionnalités de tests automatisés de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], et celles qui ont été améliorées. Cette vue d’ensemble n’est pas destinée à fournir des informations sur les fonctionnalités d’accessibilité, ni à traiter de l’accessibilité en dehors du cadre nécessaire.  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>UI Automation dans un fournisseur  
 Pour qu’une [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] soit automatisée, le développeur d’une application ou d’un contrôle doit déterminer quelles sont les actions standard qu’un utilisateur final peut effectuer sur l’objet d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] à l’aide du clavier et de la souris.  
  
 Une fois ces actions clés identifiées, les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] correspondants (autrement dit, les modèles de contrôle qui reflètent les fonctionnalités et le comportement de l’élément d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ) doivent être implémentés dans le contrôle. Par exemple, l’interaction d’un utilisateur avec un contrôle zone de liste modifiable (par exemple la boîte de dialogue Exécuter) implique généralement le développement et la réduction de la zone de liste modifiable pour masquer ou afficher une liste d’éléments, la sélection d’un élément dans cette liste, ou l’ajout d’une nouvelle valeur via l’entrée au clavier.  
  
> [!NOTE]
>  Avec d’autres modèles d’accessibilité, les développeurs doivent rassembler les informations directement à partir des boutons, menus ou autres contrôles individuels. Malheureusement, chaque type de contrôle implique des dizaines de variations mineures. En d’autres termes, même si dix variations d’un bouton de commande fonctionnent de la même manière et exécutent la même fonction, elles doivent toutes être traitées comme des contrôles uniques. Il n’existe aucun moyen de savoir si ces contrôles sont équivalents d’un point de vue fonctionnel. Les modèles de contrôle ont été développés pour représenter ces comportements de contrôles communs. Pour plus d'informations, consultez [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>Implémentation d’UI Automation  
 Comme mentionné précédemment, sans le modèle unifié fourni par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], les outils de test et les développeurs doivent connaître les informations spécifiques à l’infrastructure pour exposer les propriétés et les comportements des contrôles dans cette infrastructure. Dans la mesure où il peut y avoir plusieurs différentes infrastructures d’interface utilisateur à tout moment dans les systèmes d’exploitation Windows, y compris [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], et Windows Presentation Foundation (WPF), il peut être difficile de tester plusieurs applications avec contrôles apparemment similaires. Par exemple, le tableau suivant présente les noms de propriétés spécifiques à l’infrastructure, et qui sont nécessaires pour récupérer le nom (ou le texte) associé à un contrôle bouton. En outre, il indique la seule propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] équivalente.  
  
|Type de contrôle UI Automation|Infrastructure d’interface utilisateur|Propriété spécifique à l’infrastructure|Propriété UI Automation|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Bouton|Windows Presentation Foundation|Contenu|NameProperty|  
|Bouton|Win32|Légende|NameProperty|  
|Image|HTML|alt|NameProperty|  
  
 Les fournisseurs UI Automation sont chargés de mapper les propriétés spécifiques à l’infrastructure de leurs contrôles aux propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] équivalentes.  
  
 Pour plus d’informations sur l’implémentation d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dans un fournisseur, consultez [UI Automation Providers for Managed Code](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md). Les informations relatives à l’implémentation des modèles de contrôle sont disponibles sur [UI Automation Control Patterns](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) et [UI Automation Text Pattern](../../../docs/framework/ui-automation/ui-automation-text-pattern.md).  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>UI Automation dans un client  
 L’objectif de nombreux scénarios et outils de test automatisé est de permettre la manipulation cohérente et répétitive de l’interface utilisateur. Cela peut aller du test unitaire de contrôles spécifiques à l’enregistrement et la lecture de scripts de test qui itèrent au sein d’une série d’actions génériques dans un groupe de contrôles.  
  
 L’une des complications issues des applications automatisées est la difficulté à synchroniser un test avec une cible dynamique. C’est le cas, par exemple, pour un contrôle de zone de liste contenu dans le Gestionnaire des tâches Windows, qui affiche une liste des applications en cours d’exécution. Étant donné que les éléments de la zone de liste sont mis à jour dynamiquement en dehors du contrôle de l’application de test, il est impossible de répéter la sélection d’un élément spécifique dans la zone de liste avec cohérence. Des problèmes similaires peuvent également survenir quand vous tentez de répéter des changements de focus simples dans une [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] située hors du contrôle de l’application de test.  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>Accès par programmation  
 L’accès par programmation permet d’imiter, avec du code, les interactions et les expériences produites par les entrées classiques au clavier et à la souris. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] permet l’accès par programmation via cinq composants :  
  
- L’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] facilite la navigation dans la structure de l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. L’arborescence est créée à partir de la collection de hWnd. Pour plus d'informations, consultez [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
  
- Les éléments Automation sont des composants individuels dans l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Ceux-ci peuvent être souvent plus précis qu’un hWnd. Pour plus d'informations, consultez [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
- Les propriétés Automation fournissent des informations spécifiques sur les éléments d’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Pour plus d'informations, consultez [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
- Les modèles de contrôle définissent un aspect particulier des fonctionnalités d’un contrôle. Il peut s’agir d’informations sur les propriétés, les méthodes, les événements et les structures. Pour plus d'informations, consultez [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
- Les événements Automation fournissent des informations et des notifications d’événements. Pour plus d'informations, consultez [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>Propriétés principales pour l’automatisation des tests  
 La capacité à identifier de manière unique, puis à localiser un contrôle dans l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , est à la base du fonctionnement des applications de tests automatisés dans cette [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Il existe plusieurs propriétés [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] utilisées par les clients et les fournisseurs pour faciliter cette opération.  
  
#### <a name="automationid"></a>AutomationID  
 Identifie de manière unique un élément Automation parmi ses frères. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> n’est pas localisé, contrairement à une propriété comme <xref:System.Windows.Automation.AutomationElement.NameProperty> , qui est généralement localisé si un produit est disponible dans plusieurs langues. Consultez [Use the AutomationID Property](../../../docs/framework/ui-automation/use-the-automationid-property.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> ne garantit pas une identité unique dans l’arborescence Automation. Par exemple, une application peut contenir un contrôle de menu avec plusieurs éléments de menu de niveau supérieur qui, à leur tour, contiennent plusieurs éléments enfants. Ces éléments de menu secondaires peuvent être identifiés par un schéma générique tel que « Item1, Item 2, Item3, etc. », qui autorise les identificateurs dupliqués pour les enfants dans l’ensemble des éléments de menu de niveau supérieur.  
  
#### <a name="controltype"></a>ControlType  
 Identifie le type de contrôle représenté par un élément Automation. Des informations importantes peuvent être déduites à partir de la connaissance du type de contrôle. Consultez [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Il s’agit d’une chaîne de texte qui identifie ou explique un contrôle. <xref:System.Windows.Automation.AutomationElement.NameProperty> doit être utilisé avec précaution, car il peut être localisé. Consultez [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>Implémentation d’UI Automation dans une application de test  
  
|||  
|-|-|  
|Ajouter les références UI Automation|Les DLL [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires aux clients UI Automation sont répertoriées ici.<br /><br /> -UIAutomationClient.dll fournit l’accès à la [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API côté client.<br />-UIAutomationClientSideProvider.dll permet d’automatiser [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] contrôles. Consultez [UI Automation Support for Standard Controls](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes.dll fournit l’accès aux types spécifiques définis dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Ajouter l’espace de noms <xref:System.Windows.Automation>|Cet espace de noms contient tout ce dont les clients UI Automation ont besoin pour tirer parti des fonctionnalités [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , à l’exception de la gestion du texte.|  
|Ajouter l’espace de noms <xref:System.Windows.Automation.Text>|Cet espace de noms contient tout ce dont les clients UI Automation ont besoin pour tirer parti des fonctionnalités de gestion de texte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|Rechercher les contrôles intéressants|Les scripts de tests automatisés localisent les éléments UI Automation qui représentent des contrôles intéressants dans l’arborescence Automation.<br /><br /> Il existe plusieurs façons d’obtenir des éléments UI Automation avec du code.<br /><br /> -Permet d’interroger le [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] à l’aide un <xref:System.Windows.Automation.Condition> instruction. Il s’agit généralement du cas où le <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> indépendant de la langue est utilisé. **Remarque :**  Un <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> peut être obtenu à l’aide d’un outil tel que Inspect.exe est en mesure de détailler le [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriétés d’un contrôle. <br /><br /> -Utilisez le <xref:System.Windows.Automation.TreeWalker> classe pour parcourir l’ensemble [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] arborescence ou une de ses sous-ensembles.<br />-Suivez le focus.<br />-Utilisez le hWnd du contrôle.<br />-Utilisez l’emplacement de l’écran, tels que l’emplacement du pointeur de souris.<br /><br /> Voir [Obtaining UI Automation Elements](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)|  
|Obtenir des modèles de contrôle|Les modèles de contrôle exposent les comportements usuels des contrôles similaires d’un point de vue fonctionnel.<br /><br /> Après avoir localisé les contrôles nécessitant un test, les scripts de tests automatisés obtiennent les modèles de contrôle intéressants via ces éléments UI Automation. C’est le cas, par exemple, du modèle de contrôle <xref:System.Windows.Automation.InvokePattern> pour les fonctionnalités de bouton classiques, ou du modèle de contrôle <xref:System.Windows.Automation.WindowPattern> pour les fonctionnalités relatives aux fenêtres.<br /><br /> Consultez [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).|  
|Automatiser l’interface utilisateur|Les scripts de tests automatisés peuvent désormais contrôler toute [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] intéressante d’une infrastructure [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , à l’aide des informations et fonctionnalités exposées par les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>Outils et technologies associés  
 Plusieurs outils et technologies associés prennent en charge les tests automatisés avec [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
- Inspect.exe est un [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)] application qui peut être utilisée pour recueillir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informations pour le développement de fournisseur et le client et le débogage. Inspect.exe est inclus dans le [!INCLUDE[TLA#tla_winfxsdk](../../../includes/tlasharptla-winfxsdk-md.md)].  
  
- MSAABridge expose des informations [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] aux clients [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] . La liaison d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] à [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] a pour objectif principal de permettre aux clients [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] existants d’interagir avec une infrastructure ayant implémenté [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Security"></a>   
## <a name="security"></a>Sécurité  
 Pour plus d’informations sur la sécurité, consultez [UI Automation Security Overview](../../../docs/framework/ui-automation/ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Notions de base d’UI Automation](../../../docs/framework/ui-automation/index.md)
