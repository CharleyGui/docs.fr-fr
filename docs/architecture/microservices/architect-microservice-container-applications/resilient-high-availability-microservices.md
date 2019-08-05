---
title: Résilience et haute disponibilité dans les microservices
description: Les microservices doivent être conçus pour gérer les pannes de dépendances et de réseau temporaires auxquelles ils doivent être résilients pour assurer une haute disponibilité.
ms.date: 09/20/2018
ms.openlocfilehash: bb1bef0c9cc08e43aed80a29effe89587fb296f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675056"
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Résilience et haute disponibilité dans les microservices

Le traitement des erreurs inattendues est un des problèmes les plus difficiles à résoudre, en particulier dans un système distribué. Une grande partie du code que les développeurs écrivent implique la gestion des exceptions, et c’est aussi là où les tests prennent le plus de temps. Le problème est plus complexe que simplement écrire du code pour gérer les erreurs. Que se passe-t-il en cas de défaillance de la machine sur laquelle le microservice s’exécute ? Non seulement devez-vous détecter cette défaillance du microservice (un problème difficile en soi), mais vous avez aussi besoin de quelque chose pour redémarrer votre microservice.

Un microservice doit être résilient en cas de défaillance et pouvoir redémarrer souvent sur une autre machine pour assurer sa disponibilité. Cette résilience s’applique également à l’état qui a été enregistré pour le compte du microservice, où le microservice peut récupérer cet état, et si le microservice peut redémarrer correctement. En d’autres termes, il doit exister une résilience de la capacité de traitement (le processus peut redémarrer à tout moment), ainsi qu’une résilience de l’état ou des données (pas de perte de données, et les données doivent rester cohérentes).

Les problèmes de résilience peuvent être aggravés dans d’autres scénarios, comme quand des erreurs se produisent pendant la mise à niveau d’une application. Le microservice, en combinaison avec le système de déploiement, doit déterminer s’il peut continuer le processus de passage à la version plus récente ou s’il doit au contraire revenir à une version antérieure pour maintenir un état cohérent. Des questions telles que celles-ci doivent être considérées : y a-t-il suffisamment de machines disponibles pour poursuivre avec la mise à niveau et comment récupérer les versions précédentes du microservice. Ceci implique que le microservice émette des informations sur son intégrité, afin que l’application globale et l’orchestrateur puissent prendre ces décisions.

De plus, la résilience est liée à la façon dont les systèmes basés sur le cloud doivent se comporter. Comme mentionné, un système basé sur le cloud doit traiter les défaillances et essayer de récupérer automatiquement quand elles surviennent. Par exemple, en cas de défaillances du réseau ou d’un conteneur, les applications clientes ou les services clients doivent avoir une stratégie de nouvelles tentatives d’envoi des messages ou pour les demandes, car dans de nombreux cas, les défaillances dans le cloud sont partielles. La section [Implémentation d’applications résilientes](../implement-resilient-applications/index.md) de ce guide explique comment gérer une défaillance partielle. Elle décrit des techniques comme les nouvelles tentatives avec interruption exponentielle ou le modèle de disjoncteur dans .NET Core avec des bibliothèques comme [Polly](https://github.com/App-vNext/Polly), qui offre une grande variété de stratégies pour traiter cette question.

## <a name="health-management-and-diagnostics-in-microservices"></a>Gestion de l’intégrité et diagnostics dans les microservices

Un microservice doit communiquer son intégrité et ses diagnostics. Cela peut sembler évident, mais ce point est souvent négligé. Sinon, peu d’informations ressortent des opérations. Mettre en corrélation des événements de diagnostic sur un ensemble de services indépendants et traiter les horodatages disparates des machines pour trouver la logique de l’ordonnancement des événements peut être difficile. De la même façon que vous interagissez avec un microservice via des protocoles et des formats de données convenus, il est nécessaire de standardiser la journalisation de l’intégrité et des événements de diagnostic, qui sont au final stockés dans un magasin d’événements pour être interrogés et consultés. Dans une approche par microservices, il est important que les différentes équipes s’accordent sur un même format de journalisation. Il est nécessaire d’avoir une approche cohérente pour consulter les événements de diagnostic de l’application.

### <a name="health-checks"></a>Contrôles d’intégrité

L’intégrité diffère des diagnostics. L’intégrité concerne la communication de son état par le microservice, qui vous permet de prendre les mesures appropriées. Un bon exemple est l’utilisation des mécanismes de mise à niveau et de déploiement pour conserver la disponibilité. Bien qu’un service puisse être défectueux à un instant donné en raison du blocage d’un processus ou du redémarrage de l’ordinateur, le service peut néanmoins rester opérationnel. La dernière chose à faire est d’aggraver la situation en effectuant une mise à niveau. La meilleure approche consiste à d’abord investiguer ou à attendre que le microservice récupère. Les événements d’intégrité provenant d’un microservice nous aident à prendre des décisions avisées et à créer des services qui se restaurent eux-mêmes.

Dans la section [Implémentation de vérifications d’intégrité dans les services ASP.NET Core](../implement-resilient-applications/monitor-app-health.md#implement-health-checks-in-aspnet-core-services) de ce guide, nous expliquons comment utiliser la nouvelle bibliothèque HealthChecks d’ASP.NET dans vos microservices pour que ceux-ci puissent communiquer leur état à un service de supervision qui prendra les mesures appropriées.

Vous avez aussi la possibilité d’utiliser une excellente bibliothèque open source appelée Beat Pulse, disponible sur [GitHub](https://github.com/Xabaril/BeatPulse) et comme [package NuGet](https://www.nuget.org/packages/BeatPulse/). Cette bibliothèque effectue également des vérifications d’intégrité et gère étonnamment deux types de vérifications :

- **Fonctionnement** : vérifie si le microservice fonctionne, c’est-à-dire s’il est capable d’accepter des requêtes et d’y répondre. 
- **Préparation** : vérifie si les dépendances du microservice (base de données, services de file d’attente, etc.) sont elles-mêmes prêtes pour que le microservice puisse faire ce qu’il est supposé faire. 

### <a name="using-diagnostics-and-logs-event-streams"></a>Utilisation des diagnostics et des flux d’événements des journaux

Les journaux fournissent des informations sur la façon dont une application ou un service s’exécute, notamment les exceptions, les avertissements et les simples messages d’information. En règle générale, chaque journal est au format texte, avec une ligne par événement, bien que les exceptions s’accompagnent souvent de la trace de pile sur plusieurs lignes.

Dans les applications serveur monolithiques, vous pouvez simplement écrire les journaux dans un fichier sur disque (un fichier journal), puis les analyser avec n’importe quel outil. Comme l’exécution de l’application est limitée à un serveur ou une machine virtuelle fixe, il n’est généralement pas trop complexe d’analyser le flux des événements. Cependant, dans une application distribuée où plusieurs services sont exécutés sur de nombreux nœuds d’un cluster orchestrateur, mettre en corrélation les événements distribués peut être difficile.

Une application basée sur des microservices ne doit pas tenter de stocker elle-même le flux de sortie des événements ou des fichiers journaux, ni même tenter de gérer le routage des événements vers un emplacement central. Ce doit être transparent, ce qui signifie que chaque processus doit simplement écrire son flux d’événements vers une sortie standard, qui sera collectée plus tard par l’infrastructure de l’environnement d’exécution où il s’exécute. [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow) est un exemple de ces routeurs de flux d’événements, qui collecte les flux d’événements provenant de plusieurs sources et les publie sur des systèmes de sortie. Ces systèmes peuvent être des sorties standard simples pour un environnement de développement, ou des systèmes cloud comme [Azure Monitor](https://azure.microsoft.com/services/monitor//) et [Diagnostics Azure](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostics-extension-overview). Il existe également des plateformes et des outils de tiers performants pour l’analyse des journaux, qui permettent de rechercher, alerter, communiquer et surveiller les journaux, même en temps réel, comme [Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Orchestrateurs gérant les informations d’intégrité et de diagnostic

Quand vous créez une application basée sur des microservices, vous devez gérer la complexité. Bien sûr, s’il est simple de traiter avec un seul microservice, le problème est bien complexe avec des dizaines ou des centaines de types de microservices, et des milliers d’instances de microservices. Il ne s’agit pas seulement de créer l’architecture de vos microservices : vous avez aussi besoin d’une haute disponibilité, d’adressabilité, de résilience, d’intégrité et de diagnostics si vous voulez avoir d’un système stable et cohésif.

![Les orchestrateurs fournissent une plateforme de prise en charge pour exécuter vos microservices.](./media/image22.png)

**Figure 4-22**. Une plateforme de microservices est essentielle pour la gestion de l’intégrité d’une application

Les problèmes complexes montrés dans la figure 4-22 sont très difficiles à résoudre par vous-même. Les équipes de développement doivent se concentrer sur la résolution des problèmes métier et sur la création d’applications personnalisées avec des approches basées sur les microservices. Elles ne doivent pas se concentrer sur la résolution des problèmes d’infrastructure complexes ; si elles le font, le coût des applications basées sur des microservices serait énorme. Pour cette raison, il existe des plateformes orientée microservices, appelées orchestrateurs ou clusters de microservices, qui tentent de résoudre les difficiles problèmes de l’efficacité de la création et de l’exécution d’un service, et de l’utilisation des ressources de l’infrastructure. Ceci réduit la complexité de la création d’applications qui utilisent une approche par microservices.

Les différents orchestrateurs peuvent sembler similaires, mais les diagnostics et les vérifications d’intégrité offerts par chacun d’eux diffèrent par leurs fonctionnalités et leur état de maturité, parfois en fonction de la plateforme du système d’exploitation, comme expliqué dans la section suivante.

## <a name="additional-resources"></a>Ressources supplémentaires

- **The Twelve-Factor App. XI. Journaux : traiter les journaux sous forme de flux d’événements** \
  <https://12factor.net/logs>

- Dépôt GitHub **Microsoft Diagnostic EventFlow Library**. \
  <https://github.com/Azure/diagnostics-eventflow>

- **Présentation de Diagnostics Azure** \
  <https://docs.microsoft.com/azure/azure-diagnostics>

- **Connecter des ordinateurs Windows au service Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows>

- **Journalisation sémantique : utilisation du bloc applicatif de journalisation sémantique** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn440729(v=pandp.60)>

- Site officiel de **Splunk**. \
  <https://www.splunk.com/>

- **Classe EventSource** API pour le suivi d’événements pour Windows (ETW) \
  [https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource](xref:System.Diagnostics.Tracing.EventSource)

>[!div class="step-by-step"]
>[Précédent](microservice-based-composite-ui-shape-layout.md)
>[Suivant](scalable-available-multi-container-microservice-applications.md)
