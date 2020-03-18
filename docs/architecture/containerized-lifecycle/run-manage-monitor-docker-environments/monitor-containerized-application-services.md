---
title: Superviser des services d’application conteneurisée
description: Découvrir certains aspects essentiels de la supervision des architectures de conteneur
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68673456"
---
# <a name="monitor-containerized-application-services"></a>Superviser des services d’application conteneurisée

Il est essentiel pour les applications divisées en plusieurs conteneurs et microservices de disposer d’un moyen de superviser et d’analyser le comportement de l’ensemble de l’application.

## <a name="azure-monitor"></a>Azure Monitor

[Azure Monitor](https://azure.microsoft.com/services/monitor/) est un service d’analyse extensible qui supervise votre application dynamique. Il vous permet de détecter et de diagnostiquer les problèmes de performances, et de comprendre ce que font les utilisateurs avec votre application. Il est conçu pour les développeurs, avec l’intention de vous aider à améliorer en permanence les performances et la facilité d’utilisation de vos services ou applications. Azure Monitor fonctionne à la fois avec le web/les services et les applications autonomes sur un large éventail de plateformes comme .NET, Java, Node.js et de nombreuses autres plateformes, hébergées localement ou dans le cloud.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Vue d’ensemble du moniteur Azure** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **Qu’est-ce que Les aperçus d’applications?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Que sont les métriques Azure Monitor ?** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Solution de surveillance des conteneurs dans Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>Services de sécurité et de sauvegarde

Il existe de nombreuses tâches d’assistance très détaillées que vous devez gérer afin de garantir que vos applications et votre infrastructure sont de haute qualité pour prendre en charge les besoins de l’entreprise. Comme la situation se complique dans le domaine des microservices, vous devez pouvoir disposer de vues aussi bien générales que détaillées quand vous devez prendre des mesures.

Azure propose les outils nécessaires pour gérer et fournir une vue unifiée des quatre aspects essentiels de vos ressources cloud et locales :

- **Sécurité**. Avec [Azure Security Center](https://azure.microsoft.com/services/security-center/).
  - Obtenir une visibilité et un contrôle intégraux sur la sécurité de vos machines virtuelles, applications et charges de travail.
  - Centraliser la gestion de vos stratégies de sécurité et intégrer des outils et processus existants.
  - Détecter les menaces réelles avec l’analytique avancée.

- **Sauvegarde**. Avec la [Sauvegarde Azure](https://azure.microsoft.com/services/backup/).
  - Éviter les interruptions d’activité coûteuses, répondre aux objectifs de conformité et protéger vos données contre les ransomwares et les erreurs humaines.
  - Garder vos données de sauvegarde chiffrées pendant le transit et au repos.
  - Garantir l’accès en fonction de l’authentification multifacteur pour empêcher toute utilisation non autorisée.

- **Ressources sur place**. Avec [un cloud hybride véritablement cohérent](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).

>[!div class="step-by-step"]
>[Suivant précédent](manage-production-docker-environments.md)
>[Next](../key-takeaways/index.md)
