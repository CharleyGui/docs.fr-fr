---
title: Interfaces d'hébergement du CLR et coclasses déconseillées
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 814f148b39045ad5454a23dfce8e7f9441f69041
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616409"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a>Interfaces d'hébergement du CLR et coclasses déconseillées
Cette section décrit les interfaces que les hôtes non gérés peuvent utiliser pour intégrer le common language runtime (CLR) dans les versions .NET Framework 1,0 et 1,1 dans leurs applications. Ces interfaces fournissent des méthodes permettant à un hôte de configurer et de charger le runtime dans un processus.  
  
## <a name="in-this-section"></a>Dans cette section  
 IAppDomainSetup  
 Fournit des méthodes pour que l’hôte configure un <xref:System.AppDomain> .  
  
 [ICeeFileGen, classe](iceefilegen-class.md)  
 Déconseillé Fournit des fonctionnalités pour la création d’un fichier exécutable portable (PE) natif.  
  
 [ICorRuntimeHost, interface](icorruntimehost-interface.md)  
 Fournit des méthodes pour que l’hôte configure des paramètres CLR.  
  
## <a name="related-sections"></a>Sections connexes  
 [Interfaces d'hébergement du CLR](clr-hosting-interfaces.md)  
 Contient des rubriques qui décrivent les interfaces d’hébergement fournies avec le .NET Framework version 2,0 et les versions ultérieures.
