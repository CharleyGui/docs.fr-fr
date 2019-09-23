---
title: Langage de définition d’interface-gRPC pour les développeurs WCF
description: Présentation de l’IDL des tampons de protocole.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 71bdf8bf488e0a5bed177817343051bcd7847d25
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184427"
---
# <a name="interface-definition-language"></a>Langage de définition d’interface

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Avec WCF, les services peuvent exposer des métadonnées de description à l’aide du langage WSDL (Web Service Definition Language), qui est généré dynamiquement à l’aide de la réflexion .NET au moment de l’exécution. Les développeurs peuvent utiliser ces métadonnées pour générer des clients pour ces services, éventuellement dans d’autres langues si une liaison indépendante de la plateforme, telle que SOAP sur HTTP, est utilisée.

gRPC utilise le langage IDL (Interface Definition Language) à partir des mémoires tampons de protocole. L’IDL de mémoires tampons de protocole est un langage personnalisé, indépendant de la plateforme, avec une spécification ouverte. Les développeurs codent `.proto` manuellement les fichiers pour décrire les services, ainsi que leurs entrées et sorties. Ces `.proto` fichiers peuvent ensuite être utilisés pour générer des stubs spécifiques à une langue ou à une plateforme pour les clients et les serveurs, ce qui permet à plusieurs plateformes de communiquer. En partageant `.proto` des fichiers, les équipes peuvent générer du code pour utiliser les services de chacun d’eux sans avoir à prendre de dépendance de code.

L’un des avantages de l’IDL Protobuf est qu’en tant que langage personnalisé, il permet à gRPC d’être totalement indépendant du langage et de la plateforme, et non de privilégier toute technologie sur une autre.

L’IDL Protobuf est également conçu pour la lecture et l’écriture par les êtres humains, tandis que le langage WSDL est conçu comme un format lisible par machine. La modification du WSDL d’un service WCF requiert généralement d’apporter des modifications au code de service lui-même, d’exécuter le service et de régénérer le fichier WSDL à partir du serveur. En revanche, avec un `.proto` fichier, les modifications sont simples à appliquer à un éditeur de texte et passent automatiquement par le code généré. Visual Studio 2019 génère `.proto` des fichiers en arrière-plan lorsqu’ils sont enregistrés ; quand vous utilisez d’autres éditeurs, tels que vs code, les modifications sont appliquées lors de la génération du projet.

En comparaison avec XML, et en particulier SOAP, les messages encodés à l’aide de Protobuf présentent de nombreux avantages. Les messages Protobuf ont tendance à être plus petits que les mêmes données sérialisées en XML SOAP, et l’encodage, le décodage et la transmission sur un réseau peuvent être plus rapides.

Le désavantage potentiel de Protobuf par rapport à SOAP est que, étant donné que les messages ne sont pas lisibles par l’homme, des outils supplémentaires sont requis pour déboguer le contenu des messages.

> [!TIP]
> gRPC *prend* en charge la réflexion de serveur pour l’accès dynamique aux services sans stubs précompilés, bien qu’il soit destiné davantage aux outils à usage général que les clients spécifiques à l’application. Pour plus d’informations sur la réflexion de serveur gRPC, consultez dépôt [gRPC/gRPC](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) sur GitHub.

> [!NOTE]
> Le format binaire de WCF, utilisé avec la liaison NetTCP, est bien plus proche de Protobuf en termes de compactage et de performances, mais NetTCP est utilisable uniquement entre les clients et les serveurs .NET, alors que Protobuf est une solution multiplateforme.

>[!div class="step-by-step"]
>[Précédent](approach.md)
>[Suivant](network-protocols.md)
