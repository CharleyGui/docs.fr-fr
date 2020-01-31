---
title: REST et gRPC
description: En savoir plus sur gRPC, son rôle dans les applications natives du Cloud et sa différence par rapport à HTTP REST
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: f5725106b251a7e62ef74ea36a63c663e5db36de
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781065"
---
# <a name="rest-and-grpc"></a>REST et gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jusqu’ici, dans cet ouvrage, nous nous sommes concentrés sur la communication [basée sur REST](https://docs.microsoft.com/azure/architecture/best-practices/api-design) . REST est un style architectural qui favorise l’interopérabilité entre les systèmes informatiques distribués. Elle utilise un modèle de demande/réponse où chaque réponse du serveur est une demande du client. Bien que très populaires, REST n’est pas parfait pour chaque problème. Une technologie de communication plus récente, intitulée gRPC, est en pleine popularité et s’adapte à l’univers Cloud natif.

## <a name="grpc"></a>gRPC

gRPC est une communication Open source qui provient de Google. Il repose sur le modèle d' [appel de procédure distante (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) , populaire dans l’informatique distribuée. À la suite de ce modèle, un programme client local expose une méthode in-process pour exécuter une opération. En arrière-plan, cet appel est appelé sur un microservice hors processus sur un réseau distribué. Le développeur code l’opération en tant qu’appel de procédure locale. La plateforme sous-jacente extrait la communication réseau point à point, la sérialisation et l’exécution.

gRPC est une infrastructure RPC moderne, légère et très performante. Il utilise HTTP/2 pour son protocole de transport. Bien qu’compatible avec HTTP 1,1, HTTP/2 offre de nombreuses fonctionnalités avancées :

- Alors que HTTP 1,1 envoie des données en texte clair, HTTP/2 est un protocole binaire. Il analyse les données plus rapidement en utilisant moins de mémoire, réduit la latence du réseau avec les améliorations associées à la vitesse et gère plus efficacement les ressources réseau.
- Alors que HTTP 1,1 est limité au traitement d’une requête/réponse aller-retour à la fois, HTTP/2 prend en charge le multiplexage ou plusieurs demandes parallèles sur la même connexion.
- HTTP/2 prend en charge la communication en duplex intégral ou bidirectionnel, où le client et le serveur peuvent communiquer en même temps. Le client peut télécharger les données de demande en même temps que le serveur qui envoie les données de réponse.
- La diffusion en continu est intégrée à HTTP/2, ce qui signifie que les demandes et les réponses peuvent diffuser de manière asynchrone des jeux de données volumineux.
- En combinant gRPC et HTTP/2, les performances augmentent considérablement. En langage [Windows Communication Foundation (WCF)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) , les performances de gRPC sont conformes et dépassent la vitesse et l’efficacité des [liaisons NetTcp](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8). Toutefois, contrairement à NetTCP, gRPC n’est pas restreinte aux langages C# Microsoft tels que ou Visual Basic.

gRPC est pris en charge sur les plateformes les plus C#populaires, y compris Java,, Golang et NodeJS.

## <a name="protocol-buffers"></a>Mémoires tampon de protocole

gRPC adopte une autre technologie open source appelée [mémoires tampons de protocole](https://developers.google.com/protocol-buffers/docs/overview) ou messages Protobuf pour envoyer et recevoir des données. À l’instar d’un [contrat de données WCF](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-data-contracts), Protobuf sérialise les données structurées pour que les systèmes lisent et écrivent. Cela réduit la surcharge que les formats explicites, tels que XML ou JSON, impliquent.

De nombreuses techniques de sérialisation d’objets reflètent l’ensemble de la structure des objets de données au moment de l’exécution. Protobuf vous oblige à définir la structure en amont avec un langage de langue dépendante de la plateforme. Chaque définition est stockée dans un fichier « . proto ». Ensuite, à l’aide du compilateur Protobuf, « protonique », vous générez le code du client et du serveur pour toutes les plateformes prises en charge. Le code généré est optimisé pour la sérialisation/désérialisation rapide des données. Lors de l’exécution, chaque message est encapsulé dans le contrat de service fortement typé et sérialisé dans une représentation Protobuf standard.

## <a name="grpc-support-in-net"></a>prise en charge de gRPC dans .NET

Le Microsoft .NET Core Framework 3,0 comprend des outils et une prise en charge native pour gRPC. La figure 4-20 illustre le modèle de Visual Studio 2019 qui génère le modèle de structure d’un projet squelette gRPC pour un service gRPC. Notez comment .NET Core prend en charge les plateformes Windows, Linux et macOS.

![Prise en charge de gRPC dans Visual Studio 2019](./media/visual-studio-2019-grpc-template.png)

**Figure 4-20**. prise en charge de gRPC dans Visual Studio 2019

.NET Core 3,0 intègre en toute transparence gRPC dans son infrastructure, y compris le routage de point de terminaison, la prise en charge IoC intégrée et la journalisation. Le serveur Web Kestrel Open Source prend entièrement en charge les connexions HTTP/2.

La figure 4-21 illustre la structure d’un service gRPC dans Visual Studio 2019. Notez comment la structure de dossiers comprend des dossiers pour les fichiers proto et le code de service.

![projet gRPC dans Visual Studio 2019](./media/grpc-project.png  )

**Figure 4-21**. projet gRPC dans Visual Studio 2019

## <a name="grpc-usage"></a>Utilisation de gRPC

gRPC est bien adapté aux scénarios suivants :

- Communication à faible latence et débit élevé. gRPC est parfait pour les microservices légers où l’efficacité est essentielle.
- Communication en temps réel point à point. gRPC offre une excellente prise en charge de la diffusion bidirectionnelle. les services gRPC peuvent envoyer des messages en temps réel sans interrogation.
- Environnements polyglotte : les outils gRPC prennent en charge les langages de développement les plus populaires, ce qui en fait un bon choix pour les environnements multilingues.
- Environnements réseau restreints : les messages gRPC sont sérialisés avec Protobuf, un format de message léger. Un message gRPC est toujours plus petit qu’un message JSON équivalent.

Au moment de la rédaction de ce livre, la plupart des navigateurs ont une prise en charge limitée de gRPC. gRPC utilise fortement les fonctionnalités HTTP/2 et aucun navigateur ne fournit le niveau de contrôle requis sur les requêtes Web pour prendre en charge un client gRPC. gRPC est généralement utilisé pour la communication entre les microservices internes et les microservices. La figure 4-22 illustre un modèle d’utilisation simple, mais courant.

![Modèles d’utilisation de gRPC](./media/grpc-usage.png)

**Figure 4-22**. modèles d’utilisation de gRPC

Notez dans la figure précédente Comment le trafic frontal est appelé avec HTTP tandis que le microservice principal vers le microservice utilise gRPC.

Avant, gRPC peut jouer un rôle majeur dans la dethroning de la domination des REST pour les systèmes natifs du Cloud. Les avantages en matière de performances et de facilité de développement sont trop bons pour être transmis. Toutefois, ne vous contentez pas de continuer à utiliser le reste pendant une longue période. Il est toujours plus rapide pour les API exposées publiquement et pour des raisons de compatibilité descendante.

>[!div class="step-by-step"]
>[Précédent](service-to-service-communication.md)
>[Suivant](service-mesh-communication-infrastructure.md)
