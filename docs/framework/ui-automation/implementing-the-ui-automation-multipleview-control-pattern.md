---
title: Implémentation du modèle de contrôle MultipleView d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: c9199e0ea1971c22bfc1f6334b9d2d9d73bb048c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435059"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>Implémentation du modèle de contrôle MultipleView d’UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, notamment des informations sur les événements et les propriétés. Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.MultipleViewPattern> permet de prendre en charge des contrôles qui fournissent plusieurs représentations du même ensemble d’informations ou de contrôles enfants, et permettent de basculer entre elles.  
  
 Les exemples de contrôles qui peuvent présenter plusieurs affichages sont le mode liste (qui peut afficher son contenu sous forme de miniatures, de vignettes, d’icônes ou de détails), les graphiques Microsoft Excel (secteurs, courbes, barres, valeurs de cellule avec une formule), les documents Microsoft Word (normal, page Web, imprimer). disposition, lecture, disposition, plan), calendrier Microsoft Outlook (année, mois, semaine, jour) et habillages du lecteur Microsoft Windows Media. Les vues prises en charge sont déterminées par le développeur de contrôle et sont spécifiques à chaque contrôle.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et directives d'implémentation  
 Quand vous implémentez le modèle de contrôle Multiple View, notez les conventions et recommandations suivantes :  
  
- <xref:System.Windows.Automation.Provider.IMultipleViewProvider> doit également être implémenté sur un conteneur qui gère la vue actuelle s’il est différent d’un contrôle qui fournit la vue actuelle. Par exemple, l’Explorateur Windows contient un contrôle List pour le contenu du dossier actuel, tandis que la vue du contrôle est gérée à partir de l’application de l’Explorateur Windows.  
  
- Un contrôle qui est en mesure de trier son contenu n’est pas censé prendre en charge plusieurs vues.  
  
- La collection de vues doit être identique sur l’ensemble des instances.  
  
- Les noms des vues doivent pouvoir être utilisés dans le cadre de la synthèse vocale, de l’écriture en Braille et dans d’autres applications lisibles par l’utilisateur.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a>Membres requis pour IMultipleViewProvider  
 Les propriétés et méthodes suivantes sont requises pour implémenter IMultipleViewProvider.  
  
|Membres nécessaires|Type de membre|Remarques|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Propriété|Aucune|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Méthode|Aucune|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Méthode|Aucune|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Méthode|Aucune|  
  
 Aucun événement n’est associé à ce modèle de contrôle.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Le fournisseur doit lever les exceptions suivantes.  
  
|Type d’exception|Condition|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Quand la méthode <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> ou <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> est appelée avec un paramètre qui n’est pas membre de la collection de vues prises en charge.|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des modèles de contrôle UI Automation](ui-automation-control-patterns-overview.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](support-control-patterns-in-a-ui-automation-provider.md)
- [UI Automation Control Patterns for Clients](ui-automation-control-patterns-for-clients.md)
- [Présentation de l’arborescence UI Automation](ui-automation-tree-overview.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
