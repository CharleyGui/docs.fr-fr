---
title: Implémenter des fournisseurs UI Automation dans une application cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: a60253e62f814e9e3ea7ed4c5720e98e470d7f79
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043606"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Implémenter des fournisseurs UI Automation dans une application cliente
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient un exemple de code qui montre comment implémenter un fournisseur UI Automation côté client dans une application.  
  
 Il s’agit d’un scénario rare. La plupart du temps, une application de client UI Automation utilise des fournisseurs côté serveur ou des fournisseurs côté client qui résident dans une DLL.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant implémente un fournisseur simple pour une fenêtre de console. Le code ne dispose pas de fonctionnalités utiles, mais il est destiné à présenter les étapes de base de l’installation d’un fournisseur dans le code client et de son inscription à l’aide de <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des fournisseurs UI Automation](ui-automation-providers-overview.md)
- [Inscrire un assembly de fournisseur côté client](register-a-client-side-provider-assembly.md)
- [Créer un fournisseur UI Automation côté client](create-a-client-side-ui-automation-provider.md)
- [Implémentation de fournisseur UI Automation côté client](client-side-ui-automation-provider-implementation.md)
