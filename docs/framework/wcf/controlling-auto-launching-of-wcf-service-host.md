---
title: Contrôle de l'auto-lancement de l'hôte de service WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 7f21cd7ea600277461146387b962a89ea0a8472b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320626"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Contrôle de l'auto-lancement de l'hôte de service WCF
Vous pouvez contrôler la capacité de lancement automatique de Windows Communication Foundation hôte de service (WcfSvcHost. exe) pour un projet de bibliothèque de service WCF, lorsque vous déboguez un autre projet dans la même solution Visual Studio contenant plusieurs projets.  
  
 Pour ce faire, cliquez avec le bouton droit sur le projet de service WCF dans **Explorateur de solutions**, choisissez **Propriétés**, puis cliquez sur l’onglet **options WCF** . La case à cocher **Démarrer l’hôte de service WCF lors du débogage d’un autre projet dans la même solution** est activée par défaut. Vous pouvez décocher la case pour que l’hôte de service WCF pour ce projet spécifique ne démarre pas lorsqu’un autre projet est débogué dans la même solution.  
  
 Ce comportement n'affecte pas le débogage F5 ni les fonctionnalités d'ajout d'une référence de service pour ce projet.  
  
 Cette option est disponible dans le cadre des projets suivants :  
  
- Projet de bibliothèque du service WCF.  
  
- Projet de la bibliothèque du service du workflow séquentiel  
  
- Projet de la bibliothèque du service de workflow d'ordinateur d'état  
  
- Projet de la bibliothèque du service de syndication  
  
## <a name="see-also"></a>Voir aussi

- [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
