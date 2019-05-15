---
title: Exécution d'applications intranet de confiance totale
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7608ed964313774b806ba6f1bb4d8f0d322c361
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592767"
---
# <a name="running-intranet-applications-in-full-trust"></a>Exécution d'applications intranet de confiance totale
À compter du .NET Framework version 3.5 Service Pack 1 (SP1), les applications et leurs assemblys de bibliothèque peuvent être exécutés comme des assemblys de confiance totale à partir d’un partage réseau. La preuve de zone <xref:System.Security.SecurityZone.MyComputer> est ajoutée automatiquement aux assemblys chargés sur l’intranet à partir d’un partage. Cette preuve fournit à ces assemblys le même jeu accordé (qui est généralement de confiance totale) qu’aux assemblys qui résident sur l’ordinateur. Cette fonctionnalité ne s’applique pas aux applications ClickOnce ou aux applications conçues pour s’exécuter sur un hôte.  
  
## <a name="rules-for-library-assemblies"></a>Règles relatives aux assemblys de bibliothèque  
 Les règles suivantes s’appliquent aux assemblys chargés par un exécutable sur un partage réseau :  
  
- Les assemblys de bibliothèque doivent résider dans le même dossier que l’assembly exécutable. Les assemblys qui résident dans un sous-dossier ou qui sont référencés sur un autre chemin ne se voient pas accorder une confiance totale.  
  
- Si l’exécutable charge un assembly en différé, il doit utiliser le même chemin que pour le lancement de l’exécutable. Par exemple, si le partage \\\\*ordinateur-réseau*\\*partage* est associé à une lettre de lecteur et que l’exécutable est lancé à partir de ce chemin, les assemblys chargés par l’exécutable à l’aide du chemin réseau ne se voient pas accorder une confiance totale. Pour charger un assembly en différé dans la zone <xref:System.Security.SecurityZone.MyComputer>, l’exécutable doit utiliser le chemin de la lettre de lecteur.  
  
## <a name="restoring-the-former-intranet-policy"></a>Restauration de l’ancienne stratégie d’intranet  
 Dans les versions antérieures du .NET Framework, une preuve de zone <xref:System.Security.SecurityZone.Intranet> était accordée aux assemblys partagés. Vous deviez spécifier la stratégie de sécurité d’accès du code pour accorder une confiance totale à un assembly sur un partage.  
  
 Ce nouveau comportement est le appliqué par défaut aux assemblys intranet. Vous pouvez revenir au comportement antérieur qui consiste à fournir une preuve <xref:System.Security.SecurityZone.Intranet> en définissant une clé de Registre qui s’applique à toutes les applications de l’ordinateur. Ce processus diffère pour les ordinateurs 32 bits et 64 bits :  
  
- Sur les ordinateurs 32 bits, créez une sous-clé sous la clé HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework dans le Registre système. Utilisez le nom de clé LegacyMyComputerZone avec une valeur DWORD égale à 1.  
  
- Sur les ordinateurs 64 bits, créez une sous-clé sous la clé HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework dans le Registre système. Utilisez le nom de clé LegacyMyComputerZone avec une valeur DWORD égale à 1. Créez la même sous-clé sous la clé HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework.  
  
## <a name="see-also"></a>Voir aussi

- [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)
