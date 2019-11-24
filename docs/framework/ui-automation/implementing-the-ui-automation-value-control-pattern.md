---
title: Implémentation du modèle de contrôle Value d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: c178283b18aaf2c406292d9ab7e12a24c882c102
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447045"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implémentation du modèle de contrôle Value d’UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IValueProvider>, notamment des informations sur les événements et les propriétés. Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.ValuePattern> est utilisé pour prendre en charge les contrôles qui ont une valeur intrinsèque ne couvrant pas de plage et qui peuvent être représentés sous forme de chaîne. Cette chaîne peut être modifiée, en fonction du contrôle et de ses paramètres. Pour obtenir des exemples de contrôles implémentant ce modèle, consultez [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et directives d'implémentation  
 Quand vous implémentez le modèle de contrôle Value, notez les conventions et recommandations suivantes :  
  
- Les contrôles tels que <xref:System.Windows.Automation.ControlType.ListItem> et <xref:System.Windows.Automation.ControlType.TreeItem> doivent prendre en charge <xref:System.Windows.Automation.ValuePattern> si la valeur d’un des éléments est modifiable, indépendamment du mode d’édition actuel du contrôle. Le contrôle parent doit également prendre en charge <xref:System.Windows.Automation.ValuePattern> si les éléments enfants sont modifiables.  
  
 ![Editable list item.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Exemple d’élément de liste modifiable  
  
- Les contrôles d’édition sur une ligne prennent en charge l’accès par programmation à leur contenu en implémentant <xref:System.Windows.Automation.Provider.IValueProvider>. Toutefois, les contrôles d’édition multilignes n’implémentent pas <xref:System.Windows.Automation.Provider.IValueProvider>. Ils fournissent plutôt un accès à leur contenu en implémentant <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
- Pour récupérer le contenu textuel d’un contrôle d’édition multiligne, le contrôle doit implémenter <xref:System.Windows.Automation.Provider.ITextProvider>. Toutefois, <xref:System.Windows.Automation.Provider.ITextProvider> ne prend pas en charge la définition de la valeur d’un contrôle.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> ne prend pas en charge la récupération des informations de mise en forme ou des valeurs d’une sous-chaîne. Implémentez <xref:System.Windows.Automation.Provider.ITextProvider> dans ces scénarios.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> must be implemented by controls such as the **Color Picker** selection control from Microsoft Word (illustrated below), which supports string mapping between a color value (for example, "yellow") and an equivalent internal RGB structure.  
  
 ![Color picker with yellow highlighted.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Exemple de mappage d’une chaîne d’échantillons de couleurs  
  
- Un contrôle doit avoir <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> défini sur `true` et <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> défini sur `false` avant d’autoriser un appel à <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Membres obligatoires pour IValueProvider  
 Les propriétés et méthodes suivantes sont nécessaires à l'implémentation d' <xref:System.Windows.Automation.Provider.IValueProvider>.  
  
|Membres nécessaires|Type de membre|Notes|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Property|aucune.|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Property|aucune.|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Méthode|aucune.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -   If locale-specific information is passed to a control in an incorrect format such as an incorrectly formatted date.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -   If a new value cannot be converted from a string to a format the control recognizes.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -   When an attempt is made to manipulate a control that is not enabled.|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des modèles de contrôle UI Automation](ui-automation-control-patterns-overview.md)
- [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](support-control-patterns-in-a-ui-automation-provider.md)
- [Modèles de contrôle UI Automation pour les clients](ui-automation-control-patterns-for-clients.md)
- [ValuePattern Insert Text Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Présentation de l’arborescence UI Automation](ui-automation-tree-overview.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
