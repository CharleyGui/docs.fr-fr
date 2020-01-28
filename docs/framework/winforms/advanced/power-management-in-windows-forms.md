---
title: Gestion de l’alimentation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 9ac39df43a08f62e50116c61c4bdeda4cd1c8281
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746855"
---
# <a name="power-management-in-windows-forms"></a>Gestion de l'alimentation dans Windows Forms
Vos applications Windows Forms peuvent tirer parti des fonctionnalités de gestion de l’alimentation dans le système d’exploitation Windows. Vos applications peuvent surveiller l’état d’alimentation d’un ordinateur et agir lorsqu’un changement d’État se produit. Par exemple, si votre application s’exécute sur un ordinateur portable, vous souhaiterez peut-être désactiver certaines fonctionnalités de votre application lorsque la charge de la batterie de l’ordinateur tombe sous un certain niveau.  
  
 L' .NET Framework fournit un événement <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> qui se produit chaque fois qu’une modification de l’état de l’alimentation est effectuée, par exemple lorsqu’un utilisateur interrompt ou reprend le système d’exploitation, ou lorsque l’état de la batterie ou de l’alimentation secteur change. La propriété <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> de la classe <xref:System.Windows.Forms.SystemInformation> peut être utilisée pour interroger l’état actuel, comme indiqué dans l’exemple de code suivant.  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Outre les énumérations <xref:System.Windows.Forms.BatteryChargeStatus>, la propriété <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> contient également des énumérations pour déterminer la capacité de la batterie (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) et le pourcentage de charge de la batterie (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 Vous pouvez utiliser la méthode <xref:System.Windows.Forms.Application.SetSuspendState%2A> de la <xref:System.Windows.Forms.Application> pour mettre un ordinateur en veille prolongée ou en mode de suspension. Si l’argument `force` est défini sur `false`, le système d’exploitation diffuse un événement à toutes les applications qui demandent l’autorisation de s’interrompre. Si l’argument `disableWakeEvent` est défini sur `true`, le système d’exploitation désactive tous les événements de mise en éveil.  
  
 L’exemple de code suivant montre comment mettre un ordinateur en veille prolongée.  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
