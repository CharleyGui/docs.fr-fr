---
title: Obtenir l'état bascule d'une case à cocher à l'aide d'UI Automation
description: Consultez un exemple de code qui montre comment obtenir l’État bascule d’un contrôle (par exemple, une case à cocher) à l’aide de Microsoft UI Automation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, getting toggle states of check boxes
- check boxes, getting toggle states of
- getting, toggle states of check boxes
ms.assetid: 84fc31a3-175f-4e93-90a0-dd29d89b77ce
ms.openlocfilehash: 36ec205a572fd6c9e52eec9d2c3e0618ddb0a07b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164139"
---
# <a name="get-the-toggle-state-of-a-check-box-using-ui-automation"></a>Obtenir l'état bascule d'une case à cocher à l'aide d'UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour obtenir l’État bascule d’un contrôle.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> méthode de la <xref:System.Windows.Automation.AutomationElement> classe pour obtenir un <xref:System.Windows.Automation.TogglePattern> objet à partir d’un contrôle et retourner sa <xref:System.Windows.Automation.ToggleState> propriété.  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]
