---
title: Exposer un fournisseur UI Automation côté serveur
description: Affichez un exemple qui montre comment exposer un fournisseur UI Automation côté serveur, qui est hébergé dans une fenêtre System. Windows. Forms. Control.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expose a server-side UI Automation provider
- UI Automation, server-side provider, exposing
- server-side UI Automation provider, exposing
ms.assetid: 55d419c0-2201-4101-90c9-2888df4dbb47
ms.openlocfilehash: 66380c31da45b23d24b14154aea9770c6369aaf2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168447"
---
# <a name="expose-a-server-side-ui-automation-provider"></a>Exposer un fournisseur UI Automation côté serveur
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique contient un exemple de code qui montre comment exposer un fournisseur UI Automation côté serveur, qui est hébergé dans une fenêtre <xref:System.Windows.Forms.Control?displayProperty=nameWithType> .  
  
 Cet exemple substitue la procédure de fenêtre pour intercepter WM_GETOBJECT, qui est le message envoyé par le service principal [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] lorsqu’une application cliente demande des informations sur la fenêtre.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[UIAFragmentProvider_snip#116](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#116)]
 [!code-vb[UIAFragmentProvider_snip#116](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#116)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des fournisseurs UI Automation](ui-automation-providers-overview.md)
- [Implémentation de fournisseur UI Automation côté serveur](server-side-ui-automation-provider-implementation.md)
