---
title: Implémentation d'un proxy de découverte
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: ae003c89bb0f14623c5d31a1596533d821380336
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268298"
---
# <a name="implementing-a-discovery-proxy"></a>Implémentation d'un proxy de découverte

Cette section décrit les étapes nécessaires pour implémenter un proxy de découverte. Un proxy de découverte est un service autonome qui contient un référentiel de services. Les clients peuvent interroger un proxy de découverte pour trouver les services détectables que le proxy connaît. La manière dont un proxy est rempli avec des services incombe à l'implémenteur. Par exemple, un proxy de découverte peut se connecter à un référentiel de services existants et rendre cette information détectable, un administrateur peut utiliser une API de gestion pour ajouter des services détectables à un proxy, ou un proxy de découverte peut utiliser les fonctionnalités d'annonce pour mettre à jour son cache interne.  
  
 L'implémentation WCF fournit des classes de base qui vous permettent de générer facilement un proxy. Vous pouvez utiliser ces API pour générer un en-tête du proxy de découverte sur votre base de données de référentiel existante.  
  
 Le proxy de découverte implémenté dans cet exemple est identique à n'importe quel autre service WCF, en ce sens que vous pouvez également rendre le proxy de découverte détectable et faire localiser ses points de terminaison par les clients.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Procédure : implémenter un proxy de détection](how-to-implement-a-discovery-proxy.md)  
 Décrit comment implémenter un proxy de découverte.  
  
 [Procédure : implémenter un service détectable qui s’enregistre auprès du proxy de détection](discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Décrit comment implémenter un service WCF détectable qui s’inscrit auprès du proxy de découverte.  
  
 [Procédure : implémenter une application cliente qui utilise le proxy de détection pour rechercher un service](client-app-discovery-proxy-to-find-a-service.md)  
 Décrit comment implémenter une application cliente WCF qui utilise le proxy de découverte pour rechercher un service.  
  
 [Procédure : tester le proxy de détection](how-to-test-the-discovery-proxy.md)  
 Décrit comment tester le code écrit dans les trois rubriques précédentes.  
  
## <a name="see-also"></a>Voir aussi

- [Discovery WCF](wcf-discovery.md)
- [Procédure : ajouter par programmation la détectabilité à un service et un client WCF](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
