---
title: Discovery WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 176e9760d98f9640bd9d1c7b059287dc29c0d666
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289358"
---
# <a name="wcf-discovery"></a>Discovery WCF

Windows Communication Foundation (WCF) fournit la prise en charge pour permettre aux services d’être détectables au moment de l’exécution d’une manière interopérable à l’aide du protocole WS-Discovery. Les services WCF peuvent annoncer leur disponibilité au réseau à l’aide d’un message de multidiffusion ou d’un serveur proxy de découverte. Les applications clientes peuvent rechercher sur le réseau ou dans un serveur proxy de découverte des services qui répondent à un jeu de critères. Les rubriques de cette section donnent une vue d’ensemble et décrivent en détail le modèle de programmation pour cette fonctionnalité.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Vue d'ensemble de la découverte WCF](wcf-discovery-overview.md)  
 Fournit une vue d’ensemble de la prise en charge de WS-Discovery fournie par WCF.  
  
 [Modèle objet de découverte WCF](wcf-discovery-object-model.md)  
 Décrit les classes du modèle objet et l'extensibilité de la prise en charge de WS-Discovery.  
  
 [Procédure : ajouter par programmation la détectabilité à un service et un client WCF](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 Montre comment rendre un service Windows Communication Foundation (WCF) détectable.  
  
 [Implémentation d'un proxy de découverte](implementing-a-discovery-proxy.md)  
 Décrit les étapes nécessaires pour implémenter un proxy de découverte, un service détectable qui s'enregistre avec le proxy de découverte et un client qui utilise le proxy de découverte pour rechercher le service détectable.  
  
 [Contrôle des versions de découverte](discovery-versioning.md)  
 Donne une vue d'ensemble d'une implémentation prototype de nouvelles fonctionnalités de découverte. Elle donne également une vue d'ensemble de la manière de sélectionner la version de découverte à utiliser.  
  
 [Configuration de la découverte dans un fichier de configuration](configuring-discovery-in-a-configuration-file.md)  
 Indique comment configurer la découverte dans la configuration.  
  
 [Utilisation du canal client de découverte](using-the-discovery-client-channel.md)  
 Montre comment utiliser un canal client de découverte lors de l’écriture d’une application cliente WCF.
