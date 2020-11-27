---
title: Obtenir les propriétés d'éléments UI Automation
description: Consultez les instructions et un exemple qui montre comment récupérer les propriétés actuelles ou mises en cache d’un élément UI Automation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 34a42355acce0beafbb9658baf6032e4e7e19fcb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276423"
---
# <a name="get-ui-automation-element-properties"></a>Obtenir les propriétés d'éléments UI Automation

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique montre comment récupérer les propriétés d’un [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] élément.  
  
### <a name="get-a-current-property-value"></a>Obtenir une valeur de propriété actuelle  
  
1. Obtenez le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété.  
  
2. Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ou récupérez la <xref:System.Windows.Automation.AutomationElement.Current%2A> structure de propriété et récupérez la valeur de l’un de ses membres.  
  
### <a name="get-a-cached-property-value"></a>Obtenir une valeur de propriété mise en cache  
  
1. Obtenez le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété. La propriété doit avoir été spécifiée dans le <xref:System.Windows.Automation.CacheRequest> .  
  
2. Appelez <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> ou récupérez la <xref:System.Windows.Automation.AutomationElement.Cached%2A> structure de propriété et récupérez la valeur de l’un de ses membres.  
  
## <a name="example"></a> Exemple  

 L’exemple suivant montre différentes façons de récupérer les propriétés actuelles d’un <xref:System.Windows.Automation.AutomationElement> .  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Voir aussi

- [Propriétés UI Automation pour les clients](ui-automation-properties-for-clients.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
- [Mise en cache dans les clients UI Automation](caching-in-ui-automation-clients.md)
