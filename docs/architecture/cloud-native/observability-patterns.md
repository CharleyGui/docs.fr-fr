---
title: Modèles d’observabilité
description: Modèles d’observation pour les applications Cloud natives
ms.date: 09/23/2019
ms.openlocfilehash: 23320144c03278d631b8a1fcc1d1c0954e907296
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184875"
---
# <a name="observability-patterns"></a>Modèles d’observabilité

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Tout comme les modèles ont été développés pour faciliter la mise en page du code dans les applications, il existe des modèles pour les applications de fonctionnement de manière fiable. Trois modèles utiles dans la gestion des applications sont apparu : journalisation, surveillance et alertes.

## <a name="when-to-use-logging"></a>Quand utiliser la journalisation

Quelle que soit la prudence, les applications se comportent presque toujours de manière inattendue en production. Quand les utilisateurs signalent des problèmes avec une application, il est très utile de pouvoir voir ce qui se passe avec l’application lorsque le problème s’est produit. L’une des méthodes les plus éprouvées et les plus vraies pour capturer des informations sur ce que fait une application en cours d’exécution est de faire en sorte que l’application consigne ce qu’elle fait. Ce processus porte le nom de journalisation. À chaque fois que des échecs ou des problèmes surviennent en production, l’objectif doit être de reproduire les conditions dans lesquelles les défaillances se sont produites, dans un environnement hors production. Le fait de disposer d’une bonne connexion permet aux développeurs de suivre le programme afin de dupliquer les problèmes dans un environnement qui peut être testé et expérimenté.

### <a name="logging-in-cloud-native-applications"></a>Journalisation dans les applications natives du Cloud

Chaque langage de programmation dispose d’outils qui autorisent l’écriture de journaux, et la surcharge d’écriture de ces journaux est généralement faible. La plupart des bibliothèques de journalisation permettent de consigner différents types de critiques, qui peuvent être réglés au moment de l’exécution. Par exemple, la bibliothèque Serilog est une bibliothèque de journalisation structurée populaire pour .NET qui fournit les niveaux de journalisation suivants

* Verbose
* Débogage
* Information
* Avertissement
* Error
* Erreur irrécupérable

Ces différents niveaux de journalisation fournissent la granularité de la journalisation. Lorsque l’application fonctionne correctement en production, elle peut être configurée pour enregistrer uniquement les messages importants. Lorsque l’application ne fonctionne pas correctement, le niveau de journalisation peut être augmenté pour que les journaux plus détaillés soient collectés. Cela équilibre les performances par rapport à la facilité de débogage.

Les performances élevées des outils de journalisation et le tunability de commentaires doivent inciter les développeurs à se connecter fréquemment. De nombreux favorisent un modèle de journalisation de l’entrée et de la sortie de chaque méthode. Cette approche peut sembler excessive, mais il est peu fréquent que les développeurs souhaitent moins de journalisation. En fait, il n’est pas rare d’effectuer des déploiements dans le seul but d’ajouter la journalisation autour d’une méthode problématique. ERR sur le côté de la journalisation trop importante et non trop petit. Notez que certains outils peuvent être utilisés pour fournir automatiquement ce type de journalisation.

Dans les applications traditionnelles, les fichiers journaux étaient généralement stockés sur l’ordinateur local. En fait, sur les systèmes d’exploitation de type UNIX, il existe une structure de dossiers définie pour contenir tous les journaux, généralement sous `/var/log`. L’utilité de la journalisation dans un fichier plat sur un seul ordinateur est considérablement réduite dans un environnement Cloud. Les applications qui produisent des journaux peuvent ne pas avoir accès au disque local ou le disque local peut être très transitoire, car les conteneurs sont mélangés à des machines physiques.

Les applications Cloud natives développées à l’aide d’une architecture de microservices présentent également des défis pour les enregistreurs basés sur des fichiers. Les demandes de l’utilisateur peuvent maintenant s’étendre sur plusieurs services qui sont exécutés sur des ordinateurs différents et peuvent inclure des fonctions sans serveur sans accès à un système de fichiers local. Il serait très difficile de mettre en corrélation les journaux d’un utilisateur ou d’une session sur ces nombreux services et ordinateurs.

Enfin, le nombre d’utilisateurs dans certaines applications Cloud natives est élevé. Imaginez que chaque utilisateur génère une centaine de messages de journalisation lorsqu’il se connecte à une application. En isolation, cela est gérable, mais multipliez-vous par plus de 100 000 utilisateurs et le volume des journaux devient important.

Heureusement, il existe des alternatives fantastiques à l’utilisation de la journalisation basée sur le système de fichiers. Un serveur de journalisation centralisé dans lequel tous les journaux sont envoyés, résout tous ces problèmes. Les journaux sont collectés par les applications et expédiés à une application de journalisation centralisée qui indexe et stocke les journaux. Cette classe de système peut ingérer des dizaines de gigaoctets de journaux tous les jours.

Il est également utile de suivre certaines pratiques standard lors de la création d’une journalisation qui s’étend sur de nombreux services. Par exemple, la génération d’un [ID de corrélation](https://blog.rapid7.com/2016/12/23/the-value-of-correlation-ids/) au début d’une interaction longue, puis son enregistrement dans chaque message associé à cette interaction facilite la recherche de tous les messages associés. Il suffit de rechercher un seul message et d’extraire l’ID de corrélation pour trouver tous les messages associés. Un autre exemple consiste à s’assurer que le format de journal est le même pour tous les services, quel que soit le langage ou la bibliothèque de journalisation qu’il utilise. Cette normalisation facilite grandement la lecture des journaux. La figure 7-1 montre comment une architecture de microservices peut tirer parti de la journalisation centralisée dans le cadre de son flux de travail.

![journaux de différentes sources sont ingérés dans un magasin de journaux centralisé.](./media/centralized-logging.png)
**Figure 7-1**. Les journaux provenant de différentes sources sont ingérés dans un magasin de journaux centralisé.

## <a name="when-to-use-monitoring"></a>Quand utiliser l’analyse

Certaines applications ne sont pas critiques. Ils sont peut-être utilisés en interne uniquement et, lorsqu’un problème survient, l’utilisateur peut contacter l’équipe responsable et l’application peut être redémarrée. Toutefois, les clients ont souvent des attentes plus élevées pour les applications qu’ils consomment. Si vous avez besoin de savoir quand des problèmes se produisent avec votre application *avant que* les utilisateurs ne le fassent, ou avant que les utilisateurs vous informent, vous devez surveiller son état actuel. Correctement implémentés, la surveillance peut vous informer des conditions qui peuvent entraîner des problèmes, vous permettant de répondre aux conditions sous-jacentes avant qu’elles n’aient un impact sur l’utilisateur.

## <a name="monitoring-considerations"></a>Surveillance - Éléments à prendre en compte

Certains systèmes de journalisation centralisée prennent le rôle supplémentaire de collecter les données de télémétrie en dehors des journaux purs. Ils peuvent collecter des mesures, telles que le temps nécessaire à l’exécution d’une requête de base de données, le temps de réponse moyen d’un serveur Web, et même les moyennes de charge du processeur et la sollicitation de la mémoire, comme indiqué par le système d’exploitation. Conjointement avec les journaux, ces systèmes peuvent fournir une vue holistique de l’intégrité des nœuds du système et de l’application dans son ensemble.

Les fonctionnalités de collecte des mesures des outils de surveillance peuvent également être alimentées manuellement à partir de l’application. Les flux d’activités qui présentent un intérêt particulier, tels que les nouveaux utilisateurs qui s’inscrivent ou les commandes en cours de placement, peuvent être instrumentés de telle sorte qu’ils incrémentent un compteur dans le système de surveillance central. Cela déverrouille les outils de surveillance pour non seulement surveiller l’intégrité de l’application, mais aussi l’intégrité de l’entreprise.

Les requêtes peuvent être créées dans les outils d’agrégation de journaux pour rechercher certaines statistiques ou certains modèles, qui peuvent ensuite être affichés sous forme graphique, sur des tableaux de bord personnalisés. Souvent, les équipes investiront dans des affichages de grande taille et montés sur un mur qui font pivoter les statistiques relatives à une application. De cette façon, il est facile de voir les problèmes à mesure qu’ils se produisent.

## <a name="when-to-use-alerts"></a>Quand utiliser des alertes

Si vous devez réagir à des problèmes avec votre application, vous avez besoin d’un moyen d’alerter le personnel approprié. Il s’agit du troisième modèle d’observabilité des applications natives du Cloud, qui dépend de la journalisation et de la surveillance. Votre application doit se connecter pour permettre le diagnostic des problèmes et, dans certains cas, pour alimenter les outils de surveillance. Il a besoin d’une analyse pour agréger les mesures d’application et les données d’intégrité au même endroit. Une fois que cela a été établi, des règles peuvent être créées pour déclencher des alertes lorsque certaines métriques sont situées en dehors des niveaux acceptables.

## <a name="alerts"></a>Alertes

Vous pouvez élaborer des requêtes sur les outils de surveillance pour rechercher des conditions d’échec connues. Par exemple, les requêtes peuvent parcourir les journaux entrants pour rechercher des indications du code d’état HTTP 500, qui indique un problème sur un serveur Web. Dès que l’une d’entre elles est détectée, un message électronique ou un SMS peut être envoyé au propriétaire du service d’origine, qui peut commencer à examiner.

Toutefois, en règle générale, une seule erreur 500 n’est pas suffisante pour déterminer qu’un problème s’est produit. Cela peut signifier qu’un utilisateur a mal tapé son mot de passe ou entré des données incorrectes. Les requêtes d’alerte peuvent être conçues pour se déclencher uniquement quand un nombre supérieur au nombre moyen d’erreurs 500 est détecté.

L’un des modèles les plus dangereux des alertes consiste à déclencher un trop grand nombre d’alertes pour les êtres humains à examiner. Les propriétaires de services seront rapidement désensibilisés des erreurs qu’ils ont déjà examinées et jugées sans gravité. Lorsque des erreurs vraies se produisent, elles sont perdues dans le bruit de centaines de faux positifs. Le parable du [garçon qui effectué Wolf](https://en.wikipedia.org/wiki/The_Boy_Who_Cried_Wolf) est souvent informé des enfants pour les avertir de ce danger. Il est important de s’assurer que les alertes qui se déclenchent indiquent un problème réel.

>[!div class="step-by-step"]
>[Précédent](monitoring-health.md)
>[Suivant](logging-with-elastic-stack.md)
