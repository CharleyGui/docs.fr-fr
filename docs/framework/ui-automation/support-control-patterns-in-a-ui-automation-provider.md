---
title: Prendre en charge des modèles de contrôle dans un fournisseur UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: 1200ebd42884220d2611729b87f4bf51e7a903a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446822"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>Prendre en charge des modèles de contrôle dans un fournisseur UI Automation

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).

Cette rubrique montre comment implémenter un ou plusieurs modèles de contrôle sur un fournisseur UI Automation de sorte que les applications clientes puissent manipuler les contrôles et en obtenir les données.

## <a name="support-control-patterns"></a>Prendre en charge les modèles de contrôle

1. Implémentez les interfaces appropriées pour les modèles de contrôle que l’élément doit prendre en charge, telles que <xref:System.Windows.Automation.Provider.IInvokeProvider> pour <xref:System.Windows.Automation.InvokePattern>.

2. Retournez l’objet contenant votre implémentation de chaque interface de contrôle dans votre implémentation de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>.

## <a name="example"></a>Exemple

L’exemple suivant illustre une implémentation de <xref:System.Windows.Automation.Provider.ISelectionProvider> pour une zone de liste personnalisée à sélection unique. Elle retourne trois propriétés et obtient l’élément sélectionné.

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a>Exemple

L’exemple suivant illustre une implémentation de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> qui retourne la classe implémentant <xref:System.Windows.Automation.Provider.ISelectionProvider>. Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des fournisseurs UI Automation](ui-automation-providers-overview.md)
- [Implémentation de fournisseur UI Automation côté serveur](server-side-ui-automation-provider-implementation.md)
