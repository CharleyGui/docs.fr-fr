---
title: Implémentation du modèle de contrôle ScrollItem d’UI Automation
description: Passez en revue les recommandations et les conventions d’implémentation du modèle de contrôle ScrollItem dans UI Automation. Consultez les membres requis pour l’interface IScrollItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: a548eb25280d9a8feddc4633a1ba3e7dc022af36
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163577"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>Implémentation du modèle de contrôle ScrollItem d’UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique présente les conventions et directives à respecter pour implémenter <xref:System.Windows.Automation.Provider.IScrollItemProvider>, notamment les informations sur les propriétés, les méthodes et les événements. Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.ScrollItemPattern> est utilisé pour prendre en charge les contrôles enfants individuels des conteneurs qui implémentent <xref:System.Windows.Automation.Provider.IScrollProvider>. Ce modèle de contrôle agit comme un canal de communication entre un contrôle enfant et son conteneur pour garantir que le conteneur est en mesure de modifier le contenu (ou la zone) actuellement visible dans sa fenêtre d’affichage pour afficher le contrôle enfant. Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Conventions et directives d'implémentation  
 Quand vous implémentez le modèle de contrôle Scroll Item, notez les conventions et recommandations suivantes :  
  
- Les éléments contenus dans un contrôle Window ou Canvas ne sont pas tenus d’implémenter l’interface IScrollItemProvider. Cependant, comme alternative, ils doivent exposer un emplacement valide pour <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>. Ainsi, une application cliente UI Automation peut utiliser les méthodes de modèle de contrôle <xref:System.Windows.Automation.ScrollPattern> sur le conteneur pour afficher l’élément enfant.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>
## <a name="required-members-for-iscrollitemprovider"></a>Membres requis pour IScrollItemProvider  
 La méthode suivante est requise pour l’implémentation de l’interface IScrollProvider.  
  
|Membres nécessaires|Type de membre|Notes|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-Méthode|None|  
  
 Ce modèle de contrôle n’est associé à aucune propriété ni à aucun événement.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d’exception|Condition|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Si un élément ne peut pas être l’objet d’un défilement dans la vue :<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des modèles de contrôle UI Automation](ui-automation-control-patterns-overview.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](support-control-patterns-in-a-ui-automation-provider.md)
- [Modèles de contrôle UI Automation pour les clients](ui-automation-control-patterns-for-clients.md)
- [Vue d’ensemble de l’arborescence UI Automation](ui-automation-tree-overview.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
