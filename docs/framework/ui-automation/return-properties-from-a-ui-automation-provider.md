---
title: Retourner les propriétés d'un fournisseur UI Automation
description: Découvrez comment un fournisseur UI Automation peut retourner les propriétés d’un élément aux applications clientes dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
ms.openlocfilehash: 8269d7d04a67c2a89a28160c0a8bc82bd627749f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250474"
---
# <a name="return-properties-from-a-ui-automation-provider"></a>Retourner les propriétés d'un fournisseur UI Automation

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique contient un exemple de code qui montre comment un fournisseur UI Automation peut retourner les propriétés d’un élément aux applications clientes.  
  
 Pour toute propriété qu’il ne prend pas explicitement en charge, le fournisseur doit retourner `null` (`Nothing` en Visual Basic). Cela garantit qu’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tente d’obtenir la propriété à partir d’une autre source, telle que le fournisseur de fenêtre hôte.  
  
## <a name="example"></a>Exemple  

 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des fournisseurs UI Automation](ui-automation-providers-overview.md)
- [Implémentation de fournisseur UI Automation côté serveur](server-side-ui-automation-provider-implementation.md)
