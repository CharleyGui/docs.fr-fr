---
title: Contrôle de l'auto-lancement de l'hôte de service WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 2033e693003d0b50bcdada428e4a5f451b3ad67e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255076"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Contrôle de l'auto-lancement de l'hôte de service WCF

Vous pouvez contrôler la capacité de lancement automatique de l’hôte de service (WCF) de Windows Communication Foundation (WcfSvcHost.exe) pour un projet de bibliothèque de service WCF, lorsque vous déboguez un autre projet dans la même solution Visual Studio contenant plusieurs projets.  
  
 Pour ce faire, cliquez avec le bouton droit sur le projet de service WCF dans **Explorateur de solutions**, choisissez **Propriétés**, puis cliquez sur l’onglet **options WCF** . La case à cocher **Démarrer l’hôte de service WCF lors du débogage d’un autre projet dans la même solution** est activée par défaut. Vous pouvez décocher la case pour que l’hôte de service WCF pour ce projet spécifique ne démarre pas lorsqu’un autre projet est débogué dans la même solution.  
  
 Ce comportement n'affecte pas le débogage F5 ni les fonctionnalités d'ajout d'une référence de service pour ce projet.  
  
 Cette option est disponible dans le cadre des projets suivants :  
  
- Projet de bibliothèque du service WCF.  
  
- Projet de la bibliothèque du service du workflow séquentiel  
  
- Projet de la bibliothèque du service de workflow d'ordinateur d'état  
  
- Projet de la bibliothèque du service de syndication  
  
## <a name="see-also"></a>Voir aussi

- [Hôte de service WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
