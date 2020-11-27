---
title: Implémenter des fournisseurs UI Automation dans une application cliente
description: Consultez un exemple d’implémentation d’un fournisseur UI Automation côté client dans une application. Notez qu’il s’agit d’un scénario rare.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: 486e05f9080b686c48454dfcfceaaa666fa57f67
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269585"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Implémenter des fournisseurs UI Automation dans une application cliente

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique contient un exemple de code qui montre comment implémenter un fournisseur UI Automation côté client dans une application.  
  
 Il s’agit d’un scénario rare. La plupart du temps, une application de client UI Automation utilise des fournisseurs côté serveur ou des fournisseurs côté client qui résident dans une DLL.  
  
## <a name="example"></a> Exemple  

 L’exemple de code suivant implémente un fournisseur simple pour une fenêtre de console. Le code ne dispose pas de fonctionnalités utiles, mais il est destiné à présenter les étapes de base de l’installation d’un fournisseur dans le code client et de son inscription à l’aide de <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des fournisseurs UI Automation](ui-automation-providers-overview.md)
- [Inscrire un assembly de fournisseur côté client](register-a-client-side-provider-assembly.md)
- [Créer un fournisseur UI Automation côté client](create-a-client-side-ui-automation-provider.md)
- [Implémentation de fournisseur UI Automation côté client](client-side-ui-automation-provider-implementation.md)
