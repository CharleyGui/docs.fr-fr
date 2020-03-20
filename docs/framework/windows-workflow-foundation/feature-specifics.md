---
title: Fonctionnalités spécifiques à Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 11bde5edea44f09ef1a5658cdf0e20ec1349c84b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182921"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Fonctionnalités spécifiques à Windows Workflow Foundation

.NET Framework 4 ajoute un certain nombre de fonctionnalités à Windows Workflow Foundation. Ce document décrit quelques-unes de ces nouvelles fonctionnalités et donne des détails relatifs à certains scénarios dans lesquels elles peuvent être utiles.

## <a name="messaging-activities"></a>Activités de messagerie

Les activités<xref:System.ServiceModel.Activities.Receive>de <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Send>messagerie <xref:System.ServiceModel.Activities.ReceiveReply>( , , , ) sont utilisées pour envoyer et recevoir des messages WCF de votre flux de travail. <xref:System.ServiceModel.Activities.Receive>et <xref:System.ServiceModel.Activities.SendReply> les activités sont utilisées pour former une opération de service de la Windows Communication Foundation (WCF) qui est exposée via WSDL tout comme les services Web WCF standard. <xref:System.ServiceModel.Activities.Send>et <xref:System.ServiceModel.Activities.ReceiveReply> sont utilisés pour consommer un service <xref:System.ServiceModel.ChannelFactory>web similaire à un WCF; une expérience **de référence de service Add** existe également pour Workflow Foundation qui génère des activités préconfigurées.

### <a name="getting-started-with-messaging-activities"></a>Activités de messagerie - Mise en route

- Dans Visual Studio 2012, créez un projet WCF Workflow Service Application. Une combinaison <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> sera placée sur votre zone de dessin.

- Cliquez à droite sur le projet et sélectionnez **Ajouter la référence de service**. Pointez vers un service web existant WSDL et cliquez **sur OK**. Construisez votre projet pour afficher <xref:System.ServiceModel.Activities.Send> les <xref:System.ServiceModel.Activities.ReceiveReply>activités générées (implémentées à l’aide et) dans votre boîte à outils.

- [Documentation sur les services de flux de travail](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>Exemple de scénario d'activités de messagerie

Un `BestPriceFinder` service appelle plusieurs services aériens pour trouver le meilleur prix de billet pour un itinéraire particulier. La mise en œuvre de ce scénario vous obligerait à utiliser les activités de message pour recevoir la demande de prix, récupérer les prix des services back-end, et répondre à la demande de prix avec le meilleur prix. Il vous obligerait également à utiliser d’autres activités hors boîte pour créer la logique d’affaires pour calculer le meilleur prix.

## <a name="workflowservicehost"></a>WorkflowServiceHost

Il <xref:System.ServiceModel.WorkflowServiceHost> s’agit de l’hôte de flux de travail hors boîte qui prend en charge plusieurs instances, configuration, et la messagerie WCF (bien que les flux de travail ne sont pas tenus d’utiliser la messagerie afin d’être hébergé). Il permet également la persistance, le suivi et le contrôle de l'instance par un ensemble de comportements de service. Tout comme <xref:System.ServiceModel.ServiceHost>WCF, <xref:System.ServiceModel.WorkflowServiceHost> le peut être auto-hébergé dans une console / WinForms / WPF application ou service Windows, ou hébergé sur le Web (comme un fichier .xamlx) dans IIS ou WAS.

### <a name="getting-started-with-workflow-service-host"></a>Mise en route avec l'hôte du service de workflow

- Dans Visual Studio 2010, créez un projet WCF Workflow Service <xref:System.ServiceModel.WorkflowServiceHost> Application : ce projet sera mis en place dans un environnement hébergeur.

- Pour héberger un flux de travail sans rapport avec la messagerie, ajoutez un <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> personnalisé qui créera l'instance en fonction d'un message.

- Il est possible de contrôler des instances de flux de travail (de les suspendre ou de les arrêter, par exemple) en ajoutant un <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> au <xref:System.ServiceModel.WorkflowServiceHost>, puis en utilisant un <xref:System.ServiceModel.Activities.WorkflowControlClient>.

- Vous trouverez des exemples de <xref:System.ServiceModel.WorkflowServiceHost> dans les sections suivantes :

  - [Exécution](./samples/execution.md)

  - Demande : [Gestion des instances suspendues](./samples/suspended-instance-management.md)

- [Aperçu des services workflow d’hébergement](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>Scénario WorkflowServiceHost

Un service BestPriceFinder fait appel à plusieurs services aériens pour trouver le meilleur prix de billet pour un itinéraire particulier. La mise en œuvre de ce <xref:System.ServiceModel.WorkflowServiceHost>scénario vous obligerait à accueillir le flux de travail en . Il utiliserait également les activités de message pour recevoir la demande de prix, récupérer les prix des services back-end, et répondre à la demande de prix avec le meilleur prix.

## <a name="correlation"></a>Correlation

Une corrélation correspond à l'un des deux concepts suivants :

- manière de regrouper des messages ; autrement dit, la relation entre un message de demande et sa réponse ;

- manière de mapper des données à une instance de service.

### <a name="getting-started"></a>Mise en route

- Pour démarrer une corrélation, créez un projet dans Visual Studio. Créez une variable de type <xref:System.ServiceModel.Activities.CorrelationHandle>.

- À titre d'exemple de corrélation utilisé pour regrouper des messages, citons une corrélation demande-réponse.

  - Sur <xref:System.ServiceModel.Activities.Receive> une activité, <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> cliquez sur <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> la propriété et ajoutez un en utilisant le CorrelationHandle créé dans la première étape ci-dessus.

  - Créez <xref:System.ServiceModel.Activities.SendReply> une activité en cliquant <xref:System.ServiceModel.Activities.Receive> à droite sur le site et en cliquant sur «Créer SendReply». Collez-la dans votre flux de travail à la suite de l'activité <xref:System.ServiceModel.Activities.Receive>.

- Une corrélation basée sur le contenu qui mappe des données (un numéro de commande, par exemple) à une instance de flux de travail particulière constitue un exemple de mappage de données à une instance de service.

  - Dans une activité de messagerie, cliquez sur la propriété `CorrelationInitializers` et ajoutez un <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> à l'aide de la variable <xref:System.ServiceModel.Activities.CorrelationHandle> créée ci-dessus. Double-cliquez sur la propriété de votre choix dans le message (par exemple, OrderID) du menu déroulant. Définissez la propriété `CorrelatesWith` avec la variable <xref:System.ServiceModel.Activities.CorrelationHandle> utilisée précédemment.

- [Documentation conceptuelle relative à la corrélation](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>Scénario de corrélation

Un flux de travail de traitement des commandes est utilisé pour gérer la création de nouveaux ordres et la mise à jour des commandes existantes qui sont en cours. La mise en œuvre de ce <xref:System.ServiceModel.WorkflowServiceHost> scénario vous obligerait à héberger le flux de travail et à utiliser les activités de messagerie. Il faudrait également une `orderId` corrélation basée sur le pour s’assurer que les mises à jour sont faites au flux de travail correct.

## <a name="simplified-configuration"></a>Configuration simplifiée

Le schéma de configuration WCF est complexe et fournit aux utilisateurs de nombreuses fonctionnalités difficiles à trouver. En [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], nous nous sommes concentrés sur l’aide aux utilisateurs de WCF configurer leurs services avec les fonctionnalités suivantes:

- Plus besoin de configuration explicite par service. Si vous ne \<configurez aucun service> éléments pour votre service, et que votre service ne définit aucun critère d’évaluation programmatique, un ensemble de paramètres sera automatiquement ajouté à votre service, une adresse de base de service et par contrat implémenté par votre service.

- Permet à l’utilisateur de définir pour les comportements et les liaisons WCF des valeurs par défaut qui seront appliquées aux services sans configuration explicite.

- Les points de terminaison standard définissent les points de terminaison préconfigurés réutilisables qui ont des valeurs fixes pour une ou plusieurs propriétés de point de terminaison (adresse, liaison ou contrat) et permettent la définition de propriétés personnalisées.

- Enfin, <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> le vous permet de faire la gestion centrale de la configuration du client WCF, utile dans les scénarios dans lesquels la configuration est sélectionnée ou modifiée après le temps de chargement de domaine d’application.

### <a name="getting-started"></a>Mise en route

- [Guide du développeur pour WCF 4.0](https://docs.microsoft.com/previous-versions/dotnet/articles/ee354381(v=msdn.10))

- [Fabrique de canaux de configuration](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [Élément de point de terminaison standard](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [Améliorations de configuration de service dans .NET Framework 4](https://docs.microsoft.com/archive/blogs/endpoint/service-configuration-improvements-in-net-4)

- [Erreur souvent commise par les utilisateurs dans .NET 4 : entrée incorrecte du nom de configuration du service WF/WCF](https://docs.microsoft.com/archive/blogs/endpoint/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name)

### <a name="simplified-configuration-scenarios"></a>Scénarios de configuration simplifiée

- Un développeur ASMX expérimenté veut commencer à utiliser WCF. Cependant, WCF semble beaucoup trop compliqué! Quelles sont les informations dont j'ai besoin pour écrire dans un fichier de configuration ? Dans .NET 4, vous pouvez même décider de ne pas avoir de fichier de configuration du tout.

- Il est très difficile de configurer et de gérer un ensemble existant de services WCF. Le fichier de configuration contient des milliers de lignes de code XML qui doivent être manipulées avec la plus grande prudence. De l'aide est nécessaire pour réduire la quantité de code afin que ce dernier soit plus facile à gérer.

## <a name="data-contract-resolver"></a>Programme de résolution de contrat de données

Dans .NET 3.5, il existait quelques limitations à la conception de types connus :

- L’ajout de types connus de manière dynamique pendant la sérialisation ou la désérialisation était impossible.

- Les sérialiseurs n'étaient pas en mesure de gérer des informations xsi:type inconnues.

- Il n'était pas possible pour les utilisateurs de spécifier le xsi:type qu'ils souhaitaient voir apparaître sur le câble pour, par exemple, réduire la taille d'une instance de sérialisation sur ce dernier.

Le [DataContractResolver](../wcf/samples/datacontractresolver.md) résout ces problèmes en .NET 4.5.

### <a name="getting-started"></a>Mise en route

- [Documentation relative à l'API d'un programme de résolution de contrat de données](xref:System.Runtime.Serialization.DataContractResolver)

- [Présentation du programme de résolution de contrat de données](https://docs.microsoft.com/archive/blogs/youssefm/configuring-known-types-dynamically-introducing-the-datacontractresolver)

- Exemples :

  - [DataContractResolver](../wcf/samples/datacontractresolver.md)

  - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>Scénarios d'un programme de résolution de contrat de données

- Éviter d'avoir à déclarer des dizaines d'objets <xref:System.Runtime.Serialization.KnownTypeAttribute> dans un service.

- Réduire la taille d'un objet BLOB XML.

## <a name="flowchart"></a>Organigramme

Un organigramme est un paradigme connu permettant la représentation visuelle de problèmes liés à un domaine. Il s’agit d’un nouveau style de flux de contrôle que nous introduisons dans .NET 4. La principale caractéristique d'un organigramme tient dans le fait qu'une seule activité est exécutée à un moment donné. Les organigrammes peuvent représenter des boucles et des alternatives possibles, mais ne peuvent pas, de manière native, représenter l'exécution simultanée de plusieurs nœuds.

### <a name="getting-started"></a>Mise en route

- Dans Visual Studio 2012, créez une application de console de flux de travail. Ajoutez un organigramme dans le concepteur de workflow.

- La fonctionnalité d’organigramme utilise les classes suivantes :

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- Exemples :

  - [Gestion des erreurs dans une activité Flowchart à l’aide de TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [Processus d’embauche](./samples/hiring-process.md)

- Documentation relative au concepteur :

  - [Concepteurs d’activités Flowchart](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>Scénarios d'organigramme

Une activité d'organigramme peut permettre d'implémenter un jeu de devinette. Le jeu de devinette est très simple : l'ordinateur sélectionne un nombre aléatoire et le joueur doit deviner ce nombre. Lorsque le joueur soumet chaque supposition, l’ordinateur leur montre un indice (c’est-à-dire «essayer un nombre inférieur»). Si le joueur trouve le nombre en moins de 7 tentatives, il reçoit une félicitations spéciale de l’ordinateur. Ce jeu peut être implémenté avec une combinaison des activités procédurales suivantes :

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Activités procédurales (Sequence, If, ForEach, Switch, Assign, DoWhile, While)

Les activités procédurales fournissent un mécanisme de modélisation d'un flux de contrôle séquentiel en faisant appel à des concepts que connaissent bien les programmeurs. Ces activités permettent des constructions linguistiques de programmation traditionnellement structurées et, le cas échéant, offrent une parité linguistique avec des langages procéduraux communs tels que le C et Visual Basic.

### <a name="getting-started"></a>Mise en route

- Dans Visual Studio 2012, créez une application de console de flux de travail. Ajoutez des activités procédurales dans le concepteur de workfow.

- Exemples :

  - [Processus d’embauche](./samples/hiring-process.md)

  - [Processus d’achat d’entreprise](./samples/corporate-purchase-process.md)

- Documentation relative au concepteur :

  - [Concepteur d'activités Parallel](/visualstudio/workflow-designer/parallel-activity-designer)

  - [ParallelForEach\<T> Concepteur d’activités](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>Scénarios d'activités procédurales

- <xref:System.Activities.Statements.Parallel>: Un système de gestion de documents intranet dispose d’un flux de travail d’approbation de documents. Les documents doivent être approuvés par du personnel travaillant dans plusieurs services différents avant d'être publiés sur le réseau intranet. Il n’y a pas d’ordre établi pour les approbations; ils peuvent se produire à tout moment pendant que le document est en phase d’approbation en attente. Lorsqu’un utilisateur soumet un document pour examen, il doit être approuvé par son gestionnaire direct, l’administrateur intranet et le responsable des communications internes.

- <xref:System.Activities.Statements.ParallelForEach%601> : une application WF gère les achats au sein d'une grande entreprise. Les règles d'entreprise imposent une évaluation de trois fournisseurs différents avant toute planification d'une opération d'achat. Un employé du service d’achat sélectionne trois fournisseurs de la liste des fournisseurs de l’entreprise. Une fois que ces fournisseurs ont été sélectionnés et informés, la société attend de recevoir leur offre. L'ordre de réception des offres n'a pas d'importance. Pour implémenter ce scénario dans WF, nous utilisons un <xref:System.Activities.Statements.ParallelForEach%601> qui permettra une recherche au sein de la liste de fournisseurs et demandera une offre de leur part. Une fois que toutes les offres ont été recueillies, la meilleure est sélectionnée et affichée.

## <a name="invokemethod"></a>InvokeMethod

L'activité <xref:System.Activities.Statements.InvokeMethod> permet l'appel de méthodes publiques dans des objets ou des types de l'étendue. Elle prend en charge l'appel de méthodes statiques et d'instances avec ou sans paramètres (y compris les tableaux de paramètres), ainsi que les méthodes génériques. Elle permet également l’exécution de la méthode de façon synchrone et de façon asynchrone.

### <a name="getting-started"></a>Mise en route

- Dans Visual Studio 2012, créez une application de console de flux de travail. Ajoutez une activité <xref:System.Activities.Statements.InvokeMethod> dans le concepteur de workflow et configurez-y des méthodes d'instances et statiques.

- Documentation de concepteur : [InvokeMethod Activity Designer](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>Scénarios InvokeMethod

- Une méthode doit être appelée dans un objet de l'étendue. Par exemple, une valeur doit être ajoutée à un dictionnaire. La méthode d'ajout de l'instance du dictionnaire est appelée, puis la clé et la valeur sont fournies.

- Une méthode doit être appelée sur un objet CLR hérité. Au lieu de créer une activité personnalisée pour encapsuler l'appel dans cette classe héritée, s'il se trouve dans l'étendue pendant l'exécution du flux de travail, il est possible d'utiliser <xref:System.Activities.Statements.InvokeMethod>.

## <a name="error-handling-activities"></a>Activités de gestion des erreurs

L’activité <xref:System.Activities.Statements.TryCatch> fournit un mécanisme pour attraper les exceptions qui se produisent lors de l’exécution d’un ensemble d’activités contenues (semblable à la construction Try/Catch dans C et Visual Basic). <xref:System.Activities.Statements.TryCatch> permet la gestion des exceptions au niveau du flux de travail. Lorsqu’une exception non manipulée est lancée, le flux de travail est avorté et le bloc Enfin ne sera pas exécuté. Ce comportement est cohérent avec le langage C#.

### <a name="getting-started"></a>Mise en route

- Dans Visual Studio 2012, créez une application de console de flux de travail. Ajoutez une activité <xref:System.Activities.Statements.TryCatch> dans le concepteur de workflow.

- Exemple : [Manipulation de défaut dans une activité Flowchart utilisant TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- Documentation de concepteur : [Concepteurs d’activités de traitement des erreurs](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>Scénarios de gestion des erreurs

Un ensemble d'activités doit être exécuté et une logique spécifique être exécutée en cas d'erreur. Si, au cours de la logique de gestion des erreurs, il apparaît qu'il n'est pas possible de remédier à l'erreur, l'exception est à nouveau levée et l'activité parente (ou l'hôte) se charge du problème.

## <a name="pick-activity"></a>Activité Pick

L'activité <xref:System.Activities.Statements.Pick> fournit une modélisation de flux de contrôle basée sur les événements dans WF. <xref:System.Activities.Statements.Pick> contient de nombreuses branches, où chacune d'entre elles attend qu'un événement particulier se produise avant de s'exécuter. Dans cette configuration, un <xref:System.Activities.Statements.Pick> se comporte de manière similaire à un <xref:System.Activities.Statements.Switch%601> dans lequel l'activité exécutera un seul des jeux d'événements qu'elle écoute. Chaque branche est pilotée par l’événement et celui qui se produit exécute la branche correspondante. Toutes les autres branches annulent et arrêtent l'écoute des événements.

### <a name="getting-started"></a>Mise en route

- Dans Visual Studio 2012, créez une application de console de flux de travail. Ajoutez une activité <xref:System.Activities.Statements.Pick> dans le concepteur de workflow.

- Exemple : [Utilisation de l’activité Pick](./samples/using-the-pick-activity.md)

- Documentation de concepteur : [Concepteur d’activités pick](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Scénario de l'activité Pick

Un utilisateur doit être invité à entrer des informations. Dans des circonstances normales, le <xref:System.Console.ReadLine%2A> développeur utiliserait un appel de méthode comme pour inciter à l’entrée d’un utilisateur. Le problème avec cette configuration est que le programme attend que l'utilisateur entre des données. Dans ce scénario, un délai d'attente est nécessaire pour débloquer une activité bloquante. Dans la plupart des scénarios, une tâche doit être effectuée pendant une durée déterminée. La définition d'un délai d'attente pour une activité bloquante fait partie des cas où Pick apporte une grande valeur ajoutée.

## <a name="wcf-routing-service"></a>Service de routage WCF

Le service de routage est conçu pour être un logiciel générique Router qui vous permet de contrôler la façon dont les messages WCF circulent entre vos clients et services. Le service de routage vous permet de découpler vos clients de vos services, ce qui vous donne beaucoup plus de liberté en termes de configurations que vous pouvez prendre en charge et de la flexibilité que vous avez lorsque vous envisagez comment héberger vos services. En .NET 3.5, les clients et les services ont été étroitement couplés; un client devait connaître tous les services qu’il devait parler et où il se trouvait. De plus, WCF dans le cadre .NET 3.5 avait les limites suivantes :

- La gestion des erreurs était complexe car cette logique devait être codée en dur côté client.

- Les clients et les services devaient toujours utiliser les mêmes liaisons.

- Les services étaient rarement conçus de manière appropriée : il est plus facile de faire communiquer le client avec un service qui implémente tout un ensemble, plutôt que de choisir entre plusieurs services.

Le service de routage en .NET 4 est conçu pour rendre ces problèmes plus faciles à résoudre. Le nouveau service de routage présente les fonctionnalités suivantes :

1. Routage basé sur le contenu (les objets <xref:System.ServiceModel.Dispatcher.MessageFilter> examinent un message afin de déterminer sa destination.)

2. Protocole de transition (transport & message)

3. Gestion des erreurs (le routeur intercepte les exceptions de communication et bascule sur les points de terminaison de sauvegarde)

4. Mise à jour dynamique (en mémoire) de <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> et configuration du routage.

### <a name="getting-started"></a>Mise en route

1. Documentation: [Routage](../wcf/feature-details/routing.md)

2. Échantillons : [Les services de routage &#91;les échantillons de WCF&#93;](../wcf/samples/routing-services.md)

3. Blog: [Règles de routage!](https://docs.microsoft.com/archive/blogs/RoutingRules/)

### <a name="routing-scenarios"></a>Scénarios de routage

Le service de routage s'avère utile dans les scénarios suivants :

- Les clients peuvent communiquer avec plusieurs services sans avoir à s'adresser à l'ensemble d'entre eux directement.

- Les clients peuvent apporter une logique supplémentaire à une demande du client afin de déterminer la destination du routage

- Décomposez les opérations effectuées par un client en plusieurs implémentations du service sans refactoriser le client.

- Les clients et les services peuvent présenter différentes liaisons avec différents paramètres de sécurité.

- Les clients peuvent être configurés de manière à être plus fiables en cas de défaillance ou d'indisponibilité des services.

## <a name="wcf-discovery"></a>Discovery WCF

WCF Discovery est une technologie-cadre qui vous permet d’intégrer un mécanisme de découverte à votre infrastructure d’application. Vous pouvez vous en servir pour rendre votre service détectable et configurer vos clients pour qu'ils recherchent des services. Les clients n'ont plus besoin d'être codés en dur avec un point de terminaison, ce qui rend votre application plus fiable et plus tolérante aux pannes. Discovery est la plateforme parfaite pour intégrer des fonctionnalités d'auto-configuration à votre application.

Le produit repose sur la norme WS-Discovery. Il est conçu pour être interopérable, extensible et générique. Le produit prend en charge deux modes d'opération :

1. Managed : lorsqu'une entité sur le réseau est informée des services existants, les clients l'interrogent directement. Ce comportement est similaire à Active Directory.

2. Ad-hoc : lorsque les clients utilisent des messages de multidiffusion pour localiser des services.

Par ailleurs, les messages de découverte ne dépendent pas du protocole réseau ; vous pouvez les utiliser avec tout protocole qui prend en charge les besoins de chaque mode. Par exemple, les messages multicasts de découverte peuvent être envoyés sur la chaîne UDP ou tout autre réseau qui prend en charge la messagerie multicast. Ces points de conception, combinés à la flexibilité des fonctionnalités, vous permettent d’adapter la découverte spécifiquement à votre solution.

### <a name="getting-started"></a>Mise en route

- Documentation: [WCF Discovery](../wcf/feature-details/wcf-discovery.md)

- Échantillons: [Découverte (Échantillons)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>Scénarios Discovery

Un développeur ne souhaite pas coder en dur les points de terminaison car la date de disponibilité de mon service n'est pas encore connue. Il souhaite plutôt choisir un service au moment du runtime. Un plus grand degré de découplage, de fiabilité et de configuration automatique est requis entre les composants de l'application.

## <a name="tracking"></a>Suivi

Le suivi des flux de travail donne un aperçu de l’exécution d’une instance de flux de travail. Les événements de suivi sont émis à partir d’un flux de travail au niveau de l’instance de flux de travail et lorsque les activités au sein du flux de travail s’exécutent. Un participant au suivi du flux de travail doit être ajouté à l'hôte du flux de travail pour s'abonner aux enregistrements de suivi. Les enregistrements de suivi sont filtrés à l'aide d'un profil de suivi. Le cadre .NET fournit un participant de suivi ETW (Event Tracing for Windows), et un profil de base est installé dans le fichier machine.config.

### <a name="getting-started"></a>Mise en route

1. Dans Visual Studio 2010, créez un projet d'application de service de flux de travail WCF. Une paire <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> sera placée dans votre zone de dessin pour le démarrage.

2. Ouvrez le fichier web.config et ajoutez un comportement de suivi ETW sans profil.

    1. Le profil par défaut est utilisé.

    2. Ouvrez le visualiseur d’événements et activez le canal analytique dans le nœud suivant : **Event Viewer**, Applications and **Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**. Cliquez à droite **Analytic** et **sélectionnez Active Log**.

    3. Exécutez le service de flux de travail.

    4. Observez les événements de suivi du flux de travail dans l'observateur d'événements.

3. Échantillons: [Suivi](./samples/tracking.md)

4. Documentation conceptuelle : [Suivi et traçage des flux de travail](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>Magasin d'instances de workflow SQL

Le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> est une implémentation basée sur SQL d'un magasin d'instances. Un magasin d'instances stocke l'état d'une instance en cours d'exécution avec l'ensemble des données nécessaires au chargement et à la reprise de cette instance. L'hôte du service demande au magasin d'instances d'enregistrer l'état de l'instance si le flux de travail persiste et de charger l'état de l'instance quand un message arrive pour cette instance ou qu'une activité de report arrive à expiration.

### <a name="getting-started"></a>Mise en route

1. Dans Visual Studio 2012, créez un workflow <xref:System.Activities.Statements.Persist> qui contient une activité implicite ou explicite. Ajoutez le comportement <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> à votre hôte de service de workflow. Cela peut se faire dans le code ou dans le fichier de configuration de l'application.

2. Échantillons: [Persistance](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))

3. Documentation conceptuelle: [SQL Workflow Instance Store](sql-workflow-instance-store.md).
