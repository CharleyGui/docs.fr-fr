---
title: gRPC
description: En savoir plus sur gRPC, son rôle dans les applications natives du Cloud et sa différence par rapport à la communication HTTP RESTful.
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: f34b267d7f5c6b4e593841c80df44d1ccbde95ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614043"
---
# <a name="grpc"></a>gRPC

Jusqu’ici, dans cet ouvrage, nous nous sommes concentrés sur la communication [basée sur REST](https://docs.microsoft.com/azure/architecture/best-practices/api-design) . Nous avons vu que REST est un style architectural flexible qui définit les opérations CRUD sur les ressources d’entité. Les clients interagissent avec les ressources sur HTTP avec un modèle de communication de demande/réponse. Bien que REST soit largement implémenté, une technologie de communication plus récente, gRPC, a gagné un énorme dynamisme au sein de la communauté Cloud-native.

## <a name="what-is-grpc"></a>Qu’est-ce que gRPC ?

gRPC est une infrastructure moderne et hautement performante qui fait évoluer le protocole d' [appel de procédure distante (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) Age Old. Au niveau de l’application, gRPC simplifie la messagerie entre les clients et les services principaux. En provenance de Google, gRPC est open source et fait partie de l’écosystème [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) des offres Cloud natives. CNCF considère gRPC un [projet en incubation](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc). L’incubation signifie que les utilisateurs finaux utilisent la technologie dans les applications de production et que le projet a un nombre sain de contributeurs.

Une application cliente gRPC standard expose une fonction in-process locale qui implémente une opération commerciale. En coulisses, cette fonction locale appelle une autre fonction sur un ordinateur distant. Ce qui semble être un appel local devient essentiellement un appel out-of-process transparent à un service distant. L’infrastructure RPC fait abstraction de la communication réseau point à point, de la sérialisation et de l’exécution entre les ordinateurs.

Dans les applications Cloud natives, les développeurs travaillent souvent dans des langages de programmation, des infrastructures et des technologies. Cette *interopérabilité* complique les contrats de message et les mécanismes requis pour la communication multiplateforme.  gRPC fournit une « couche horizontale uniforme » qui résume ces préoccupations. Les développeurs codent dans leur plate-forme native axée sur les fonctionnalités métier, tandis que gRPC gère la gestion des communications.

gRPC offre une prise en charge complète des piles de développement les plus populaires, notamment Java, JavaScript, C#, Go, Swift et NodeJS.

## <a name="grpc-benefits"></a>Avantages gRPC

gRPC utilise HTTP/2 pour son protocole de transport. Bien qu’compatible avec HTTP 1,1, HTTP/2 offre de nombreuses fonctionnalités avancées :

- Protocole binaire pour le transport de données, contrairement à HTTP 1,1, qui envoie des données en texte clair.
- Prise en charge du multiplexage pour l’envoi de plusieurs requêtes parallèles sur la même connexion-HTTP 1,1 limite le traitement à un message de demande/réponse à la fois.
- Communication bidirectionnelle en duplex intégral pour l’envoi simultané des demandes du client et des réponses du serveur.
- Streaming intégré permettant des demandes et des réponses pour diffuser de manière asynchrone des jeux de données volumineux.

gRPC est léger et très performant. Elle peut être jusqu’à 8 fois plus rapide que la sérialisation JSON avec des messages de 60-80% de plus. Dans le jargon de Microsoft [Windows Communication Foundation (WCF)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) , les performances de gRPC dépassent la vitesse et l’efficacité des [liaisons NetTcp](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8)hautement optimisées. Contrairement à NetTCP, qui privilégie la pile Microsoft, gRPC est multiplateforme.

## <a name="protocol-buffers"></a>Mémoires tampon de protocole

gRPC adopte une technologie open source appelée [mémoires tampons de protocole](https://developers.google.com/protocol-buffers/docs/overview). Ils fournissent un format de sérialisation très efficace et indépendant de la plateforme pour la sérialisation des messages structurés que les services envoient entre eux. À l’aide d’un langage IDL (Interface Definition Language) multiplateforme, les développeurs définissent un contrat de service pour chaque microservice. Le contrat, implémenté sous forme de fichier texte `.proto` , décrit les méthodes, les entrées et les sorties pour chaque service. Le même fichier de contrat peut être utilisé pour les clients et services gRPC basés sur différentes plateformes de développement.

À l’aide du fichier proto, le compilateur Protobuf, `protoc` , génère le code du client et du service pour votre plateforme cible. Le code comprend les composants suivants :

- Objets fortement typés, partagés par le client et le service, qui représentent les opérations de service et les éléments de données d’un message.
- Classe de base fortement typée avec l’infrastructure réseau requise que le service gRPC distant peut hériter et étendre.
- Stub client qui contient les plombages requis pour appeler le service gRPC distant.

Lors de l’exécution, chaque message est sérialisé en tant que représentation Protobuf standard et échangé entre le client et le service distant. Contrairement à JSON ou XML, les messages Protobuf sont sérialisés en tant qu’octets binaires compilés.

Le livre, [gRPC pour les développeurs WCF](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/), disponible sur le site de l’architecture Microsoft, fournit une couverture approfondie des gRPC et des mémoires tampons de protocole.

## <a name="grpc-support-in-net"></a>prise en charge de gRPC dans .NET

gRPC est intégré au kit de développement logiciel (SDK) .NET Core 3,0 et versions ultérieures. Les outils suivants le prennent en charge :

- Visual Studio 2019, version 16,3 ou ultérieure, avec la charge de travail développement Web installée.
- Visual Studio Code
- interface CLI dotnet

Le kit de développement logiciel (SDK) comprend des outils pour le routage des points de terminaison, l’IoC intégré et la journalisation. Le serveur Web Kestrel Open Source prend en charge les connexions HTTP/2. La figure 4-20 illustre un modèle de Visual Studio 2019 qui génère une structure de projet squelette pour un service gRPC. Notez comment .NET Core prend entièrement en charge Windows, Linux et macOS.

![Prise en charge de gRPC dans Visual Studio 2019](./media/visual-studio-2019-grpc-template.png)

**Figure 4-20**. prise en charge de gRPC dans Visual Studio 2019
  
La figure 4-21 montre le squelette du service gRPC généré à partir de la génération de modèles automatique intégrée incluse dans Visual Studio 2019.  

![projet gRPC dans Visual Studio 2019](./media/grpc-project.png  )

**Figure 4-21**. projet gRPC dans Visual Studio 2019

Dans l’illustration précédente, notez le fichier de description proto et le code de service. Comme vous le verrez bientôt, Visual Studio génère une configuration supplémentaire à la fois dans la classe Startup et dans le fichier projet sous-jacent.

## <a name="grpc-usage"></a>utilisation de gRPC

Privilégiez gRPC pour les scénarios suivants :

- Communication du microservice vers le serveur principal synchrone, où une réponse immédiate est nécessaire pour poursuivre le traitement.
- Environnements polyglotte qui doivent prendre en charge des plateformes de programmation mixte.
- Communication à faible latence et débit élevé, où les performances sont critiques.
- Communication en temps réel point à point : gRPC peut envoyer des messages en temps réel sans interrogation et offre une excellente prise en charge de la diffusion bidirectionnelle.
- Environnements réseau restreints : les messages gRPC binaires sont toujours plus petits qu’un message JSON équivalent basé sur le texte.

Au moment de la rédaction de cet article, gRPC est principalement utilisé avec les services principaux. La plupart des navigateurs modernes ne peuvent pas fournir le niveau de contrôle HTTP/2 requis pour prendre en charge un client gRPC frontal. Cela dit, il existe une [initiative précoce](https://devblogs.microsoft.com/aspnet/grpc-web-experiment/) qui permet la communication gRPC à partir d’applications basées sur le navigateur créées avec des technologies de webassembly avec JavaScript ou éblouissant. [GRPC-Web pour .net](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md) permet à une application ASP.net Core gRPC de prendre en charge des fonctionnalités gRPC dans les applications de navigateur :

- Clients générés par du code fortement typés
- Compacter les messages Protobuf
- Streaming de serveur

## <a name="grpc-implementation"></a>implémentation de gRPC

L’architecture de référence des microservices, [eShop on containers](https://github.com/dotnet-architecture/eShopOnContainers), de Microsoft, montre comment implémenter des services gRPC dans des applications .net core. La figure 4-22 présente l’architecture back-end.

![Architecture backend pour eShop sur les conteneurs](./media/eshop-with-aggregators.png)

**Figure 4-22**. Architecture backend pour eShop sur les conteneurs

Dans l’illustration précédente, vous remarquerez comment eShop adopte le [modèle backend pour les serveurs frontaux](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) (BFF) en exposant plusieurs passerelles d’API. Nous avons abordé le modèle BFF plus haut dans ce chapitre. Portez une attention particulière au microservice de l’agrégateur (en gris) qui se situe entre la passerelle d’API d’achat Web et les microservices d’achat principaux. L’agrégation reçoit une requête unique d’un client, la distribue à différents microservices, agrège les résultats et les renvoie au client demandeur. Ces opérations nécessitent généralement une communication synchrone en ce qui concerne la génération d’une réponse immédiate. Dans eShop, les appels backend de l’agrégateur sont effectués à l’aide de gRPC, comme le montre la figure 4-23.

![gRPC dans eShop sur les conteneurs](./media/grpc-implementation.png)

**Figure 4-23**. gRPC dans eShop sur les conteneurs

la communication gRPC nécessite à la fois les composants client et serveur. Dans la figure précédente, Notez comment l’agrégateur d’achat implémente un client gRPC. Le client effectue des appels gRPC synchrones (en rouge) aux microservices backend, chacun d’entre eux implémentant un serveur gRPC. Le client et le serveur tirent parti des fonctionnalités gRPC intégrées du kit SDK .NET Core. Les *stubs* côté client permettent d’appeler les appels gRPC distants. Les composants côté serveur fournissent des éléments gRPC qui peuvent être hérités et consommés par les classes de service personnalisées.

Les microservices qui exposent une API RESTful et une communication gRPC requièrent plusieurs points de terminaison pour gérer le trafic. Vous ouvrez un point de terminaison qui écoute le trafic HTTP pour les appels RESTful et un autre pour les appels gRPC. Le point de terminaison gRPC doit être configuré pour le protocole HTTP/2 requis pour la communication gRPC.

Bien que nous cherchions à découpler les microservices avec des modèles de communication asynchrones, certaines opérations nécessitent des appels directs. gRPC doit être le principal choix pour la communication synchrone directe entre les microservices. Son protocole de communication hautes performances, basé sur les mémoires tampons HTTP/2 et de protocole, en fait un choix parfait.

## <a name="looking-ahead"></a>Avant

Avant, gRPC continuera à gagner en traction pour les systèmes Cloud natifs. Les avantages en matière de performances et de facilité de développement sont intéressants. Toutefois, REST sera probablement inactif pendant une longue période. Il expose les API exposées publiquement et pour des raisons de compatibilité descendante.

>[!div class="step-by-step"]
>[Précédent](service-to-service-communication.md) 
> [Suivant](service-mesh-communication-infrastructure.md)
