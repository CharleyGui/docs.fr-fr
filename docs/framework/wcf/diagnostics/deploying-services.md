---
title: Déploiement de services
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 07bd2a3938f238336dc00fa2e0826a28a9363a4a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294805"
---
# <a name="deploying-services"></a>Déploiement de services

Cette rubrique décrit comment vous pouvez déployer une application Windows Communication Foundation (WCF) dans un environnement d’exécution.  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a>Choix de l'environnement d'hébergement de votre application  

 Les services WCF sont conçus pour s’exécuter dans n’importe quel processus Windows qui prend en charge le code managé. Pour devenir actif, un service doit être hébergé dans un environnement d'exécution qui le crée et contrôle son contexte et sa durée de vie. Les options d'hébergement vont de l'exécution à l'intérieur de l'application console la plus simple à une exécution dans des environnements serveur comme un service Windows et les services Internet (IIS) ou dans un processus de travail géré par WAS (Windows Activation Services). Pour passer en revue les différentes options d’hébergement pour votre application WCF, consultez [services d’hébergement](../hosting-services.md).  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement](../feature-details/hosting.md)
- [Hébergement de services](../hosting-services.md)
