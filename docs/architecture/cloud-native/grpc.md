---
title: gRPC (en)
description: Renseignez-vous sur le gRPC, son rôle dans les applications cloud-natives, et comment il diffère de la communication RESTful HTTP.
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 28a07ad5ec105d3fc5b65e4cf0ac0cd85eb16627
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80524172"
---
# <a name="grpc"></a>gRPC (en)

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jusqu’à présent, dans ce livre, nous nous sommes concentrés sur la communication basée sur [REST.](https://docs.microsoft.com/azure/architecture/best-practices/api-design) Nous avons vu que REST est un style architectural flexible qui définit les opérations basées sur CRUD par rapport aux ressources de l’entité. Les clients interagissent avec les ressources de HTTP avec un modèle de communication de demande/réponse. Bien que REST soit largement mise en œuvre, une nouvelle technologie de communication, gRPC, a pris un élan énorme dans la communauté des personnes du cloud.

## <a name="what-is-grpc"></a>Qu’est-ce que le gRPC?

gRPC est un cadre moderne et performant qui évolue le protocole [d’appel d’intervention à distance (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) séculaire. Au niveau de l’application, gRPC rationalise la messagerie entre les clients et les services back-end. Originaire de Google, gRPC est open source et fait partie de l’écosystème Cloud [Native Computing Foundation (CNCF)](https://www.cncf.io/) d’offres cloud-native. La CNCF considère gRPC comme un [projet d’incubation.](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc) Incubation signifie que les utilisateurs finaux utilisent la technologie dans les applications de production, et le projet a un nombre sain de contributeurs.

Une application client GRPC typique exposera une fonction locale en cours de traitement qui met en œuvre une entreprise. Sous les couvertures, cette fonction locale invoque une autre fonction sur une machine à distance. Ce qui semble être un appel local devient essentiellement un appel transparent hors-processus à un service distant. La plomberie RPC résume la communication de réseautage point-à-point, la sérialisation et l’exécution entre les ordinateurs.

Dans les applications cloud-natives, les développeurs travaillent souvent à travers les langages de programmation, les cadres et les technologies. Cette *interopérabilité* complique les contrats de messages et la plomberie requise pour la communication interplateforme.  gRPC fournit une « couche horizontale uniforme » qui résume ces préoccupations. Les développeurs codent dans leur plate-forme native axée sur la fonctionnalité d’entreprise, tandis que gRPC gère la plomberie de communication.

gRPC offre un soutien complet sur la plupart des piles de développement populaires, y compris Java, JavaScript, C, Go, Swift et NodeJS.

## <a name="grpc-benefits"></a>avantages gRPC

gRPC utilise HTTP/2 pour son protocole de transport. Bien que compatible avec HTTP 1.1, HTTP/2 dispose de nombreuses fonctionnalités avancées :

- Un protocole binaire pour le transport de données - contrairement à HTTP 1.1, qui envoie des données sous forme de texte clair.
- Soutien multiplexant pour l’envoi de plusieurs demandes parallèles sur la même connexion - HTTP 1.1 limite le traitement à un message de demande/réponse à la fois.
- Communication bidirectionnelle en duplex pour l’envoi simultané de demandes de clients et de réponses au serveur.
- Streaming intégré permettant des demandes et des réponses à diffuser asynchronement de grands ensembles de données.

gRPC est léger et très performant. Il peut être jusqu’à 8x plus rapide que la sérialisation JSON avec des messages 60-80% plus petit. Dans le langage de [microsoft Windows Communication Foundation (WCF),](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) les performances de gRPC dépassent la vitesse et l’efficacité des [liaisons NetTCP](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8)hautement optimisées. Contrairement à NetTCP, qui favorise la pile Microsoft, gRPC est multiplateforme.

## <a name="protocol-buffers"></a>Mémoires tampon de protocole

gRPC adopte une technologie open-source appelée [Protocol Buffers](https://developers.google.com/protocol-buffers/docs/overview). Ils fournissent un format de sérialisation très efficace et neutre sur la plate-forme pour la sérialisation des messages structurés que les services s’envoient les uns aux autres. À l’aide d’un langage de définition d’interface interplateforme (IDL), les développeurs définissent un contrat de service pour chaque microservice. Le contrat, mis en `.proto` œuvre sous forme de fichier textuel, décrit les méthodes, les entrées et les sorties de chaque service. Le même fichier de contrat peut être utilisé pour les clients et services gRPC construits sur différentes plates-formes de développement.

À l’aide du fichier proto, `protoc`le compilateur Protobuf, génère à la fois le client et le code de service pour votre plate-forme cible. Le code comprend les composants suivants :

- Objets fortement typés, partagés par le client et le service, qui représentent les opérations de service et les éléments de données pour un message.
- Une classe de base fortement typée avec la plomberie réseau requise que le service à distance gRPC peut hériter et étendre.
- Un talon client qui contient la plomberie requise pour invoquer le service à distance gRPC.

Au moment de l’exécution, chaque message est sérialisé en tant que représentation Protobuf standard et échangé entre le client et le service à distance. Contrairement à JSON ou XML, les messages Protobuf sont sérialisés sous forme d’octets binaires compilés.

Le livre, [gRPC pour WCF Developers](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/), disponible sur le site Microsoft Architecture, offre une couverture approfondie de gRPC et Protocol Buffers.

## <a name="grpc-support-in-net"></a>support gRPC en .NET

gRPC est intégré dans .NET Core 3.0 SDK ou plus tard. Les outils suivants le soutiennent :

- Visual Studio 2019, version 16.3 ou plus tard, avec la charge de travail de développement web installée.
- Visual Studio Code
- l’ICIC dotnet

Le SDK comprend l’outillage pour le routage des points de terminaison, l’IoC intégré et l’enregistrement. Le serveur web open-source Kestrel prend en charge les connexions HTTP/2. La figure 4-20 montre un modèle Visual Studio 2019 qui échafaude un projet de squelette pour un service gRPC. Notez comment .NET Core prend pleinement en charge Windows, Linux et macOS.

![support gRPC en Studio Visuel 2019](./media/visual-studio-2019-grpc-template.png)

**Figure 4-20**. gRPC support dans Visual Studio 2019
  
La figure 4-21 montre le service squelette gRPC généré par l’échafaudage intégré inclus dans Visual Studio 2019.  

![gRPC projet dans Visual Studio 2019](./media/grpc-project.png  )

**Figure 4-21**. gRPC projet dans Visual Studio 2019

Dans le chiffre précédent, notez le fichier de description proto et le code de service. Comme vous le verrez bientôt, Visual Studio génère une configuration supplémentaire dans la classe Startup et dans le fichier de projet sous-jacent.

## <a name="grpc-usage"></a>utilisation de gRPC

Favoriser gRPC pour les scénarios suivants:

- Communication synchrone de microservice de backend-à-microservice où une réponse immédiate est nécessaire pour continuer le traitement.
- Environnements polyglottes qui ont besoin de prendre en charge les plates-formes de programmation mixtes.
- Faible latence et communication à haut débit où la performance est critique.
- Communication en temps réel point à point - gRPC peut pousser des messages en temps réel sans sondage et a un excellent soutien pour le streaming bidirectionnel.
- Environnements de réseau restreints - les messages de gRPC binaires sont toujours plus petits qu’un message JSON basé sur le texte équivalent.

À l’époque, de cette écriture, gRPC est principalement utilisé avec les services backend. La plupart des navigateurs modernes ne peuvent pas fournir le niveau de contrôle HTTP/2 requis pour prendre en charge un client gRPC frontale. Cela dit, il ya une [initiative précoce](https://devblogs.microsoft.com/aspnet/grpc-web-experiment/) qui permet la communication gRPC à partir d’applications basées sur le navigateur construit avec JavaScript ou Blazor WebAssembly technologies. Le [gRPC-Web pour .NET](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md) permet à une application ASP.NET Core gRPC de prendre en charge les fonctionnalités gRPC dans les applications de navigateur:

- Clients fortement typés générés par le code
- Messages Protobuf compacts
- Streaming serveur

## <a name="grpc-implementation"></a>mise en œuvre gRPC

L’architecture de référence de microservice, [eShop sur Les conteneurs](https://github.com/dotnet-architecture/eShopOnContainers), de Microsoft, montre comment implémenter les services gRPC dans les applications .NET Core. La figure 4-22 présente l’architecture back-end.

![Architecture backend pour eShop sur Conteneurs](./media/eshop-with-aggregators.png)

**Figure 4-22**. Architecture backend pour eShop sur Conteneurs

Dans le chiffre précédent, notez comment eShop embrasse le [modèle Backend for Frontends](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) (BFF) en exposant plusieurs passerelles API. Nous avons discuté du modèle BFF plus tôt dans ce chapitre. Portez une attention particulière au microservice Aggregator (en gris) qui se trouve entre la passerelle de l’API Web-Shopping et les microservices d’achats backend. L’agrégateur reçoit une seule demande d’un client, l’envoie à divers microservices, agrége les résultats et les renvoie au client demandeur. Ces opérations nécessitent généralement une communication synchrone pour produire une réponse immédiate. Dans eShop, les appels backend de l’agrégateur sont effectués à l’aide de gRPC comme indiqué dans la figure 4-23.

![gRPC dans eShop sur conteneurs](./media/grpc-implementation.png)

**Figure 4-23**. gRPC dans eShop sur conteneurs

la communication gRPC nécessite à la fois des composants clients et serveur. Dans le chiffre précédent, notez comment l’agrégateur de shopping implémente un client gRPC. Le client fait des appels synchrones gRPC (en rouge) pour backend microservices, dont chacun implémente un serveur gRPC. Le client et le serveur profitent de la plomberie gRPC intégrée de la .NET Core 3.0 SDK. Les *talons* côté client fournissent la plomberie pour invoquer les appels à distance de gRPC. Les composants côté serveur fournissent la plomberie gRPC que les classes de service personnalisé peuvent hériter et consommer.

Les microservices qui exposent à la fois une communication RESTful API et gRPC nécessitent plusieurs paramètres de gestion du trafic. Vous ouvririez un point de terminaison qui écoute le trafic HTTP pour les appels RESTful et un autre pour les appels gRPC. Le critère d’évaluation gRPC doit être configuré pour le protocole HTTP/2 requis pour la communication gRPC.

Bien que nous nous effervions à découpler les microservices avec des modèles de communication asynchrones, certaines opérations nécessitent des appels directs. gRPC devrait être le choix principal pour la communication synchrone directe entre les microservices. Son protocole de communication haute performance, basé sur HTTP/2 et les tampons de protocole, en font un choix parfait.

## <a name="looking-ahead"></a>Vers l’avenir

Pour l’avenir, gRPC continuera de gagner en traction pour les systèmes cloud-autochtones. Les avantages de la performance et la facilité de développement sont convaincants. Cependant, REST sera probablement là pendant une longue période. Il excelle pour les API publiquement exposées et pour des raisons de compatibilité rétrograde.

>[!div class="step-by-step"]
>[Suivant précédent](service-to-service-communication.md)
>[Next](service-mesh-communication-infrastructure.md)
