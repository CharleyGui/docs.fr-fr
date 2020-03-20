---
title: Isolement réseau pour les applications du Windows Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 390a0281f03b08322cc1bee469b601fd5a1547c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802162"
---
# <a name="network-isolation-for-windows-store-apps"></a>Isolement réseau pour les applications du Windows Store

Les cours <xref:System.Net> <xref:System.Net.Http>dans <xref:System.Net.Http.Headers> les espaces de noms et les espaces de nom peuvent être utilisés pour développer des applications Windows Store ou des applications de bureau. Lorsqu’elles sont utilisées dans une application Windows Store, les cours dans ces espaces nominaux sont affectés par l’isolement du réseau, une partie du modèle de sécurité des applications utilisé par Windows 8. Les fonctionnalités réseau appropriées doivent être activées dans le manifeste d’une application du Windows Store pour que le système autorise l’accès réseau.  
  
## <a name="checklist-for-network-isolation"></a>Liste de vérification pour l’isolement réseau  

Utilisez cette liste de vérification pour vérifier que l’isolement réseau est configuré pour votre application du Windows Store.  
  
1. Déterminez la direction des requêtes d’accès réseau dont a besoin l’application. Il peut s’agir de requêtes sortantes lancées par le client, de requêtes entrantes non sollicitées, ou d’une combinaison de ces deux types de requêtes réseau.  
  
2. Déterminez le type de ressources réseau avec lesquelles l’application va communiquer. Une application peut avoir besoin de communiquer avec des ressources approuvées appartenant à un réseau domestique ou d’entreprise. Une application peut avoir besoin de communiquer avec des ressources Internet. Une application peut avoir besoin d’accéder à ces deux types de ressources réseau.  
  
3. Configurez les fonctionnalités d’isolement réseau minimales dans le manifeste d’application.  
  
4. Déployez et exécutez votre application pour la tester à l’aide des outils d’isolement réseau fournis pour la résolution des problèmes.  
  
Pour obtenir des informations plus détaillées sur la façon de configurer les capacités réseau et les outils d’isolement utilisés pour dépanner l’isolement du réseau, voir comment configurer les [capacités d’isolation réseau](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10)) dans la documentation des développeurs Windows 8.x Store.
  
## <a name="see-also"></a>Voir aussi

- [Se connecter à un service web](https://docs.microsoft.com/previous-versions/windows/apps/hh761504(v=win.10))
- [Recommandations et liste de contrôle de l’isolement réseau](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10))
- [Démarrage rapide : connexion avec HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781239(v=win.10))
- [Guide pratique pour utiliser les gestionnaires HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781241(v=win.10))
- [Guide pratique pour sécuriser les connexions HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781240(v=win.10))
- [Exemple HttpClient](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
