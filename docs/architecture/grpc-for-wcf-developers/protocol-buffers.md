---
title: Protocole Buffers - gRPC pour les développeurs WCF
description: Introduction au format de fil Protocol Buffers utilisé pour le réseautage gRPC.
ms.date: 09/09/2019
ms.openlocfilehash: 35319d299a8bc2866a87954b3e54bfda9314ffe8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147930"
---
# <a name="protocol-buffers"></a>Tampons de protocole

les services gRPC envoient et reçoivent des données sous forme *de messages Protocol Buffer (Protobuf),* similaires aux contrats de données de la Windows Communication Foundation (WCF). Protobuf est un moyen efficace de sérialisation des données structurées pour les machines à lire et à écrire, sans les frais généraux que les formats lisibles par l’homme comme XML ou JSON encourent.

Ce chapitre couvre le fonctionnement de Protobuf et la façon de définir vos propres messages Protobuf.

## <a name="how-protobuf-works"></a>Fonctionnement de Protobuf

La plupart des techniques de sérialisation d’objets .NET, y compris les contrats de données de WCF, fonctionnent en utilisant la réflexion pour analyser la structure de l’objet au moment de l’exécution. En revanche, la plupart des bibliothèques Protobuf vous obligent à définir la `.proto` structure à l’avance en utilisant une langue dédiée ( Langage tampon de*protocole*) dans un fichier. Un compilateur utilise ensuite ce fichier pour générer du code pour l’une des plates-formes prises en charge. Les plates-formes prises en charge comprennent .NET, Java, C/C, JavaScript, et bien d’autres.

Le compilateur Protobuf, `protoc`, est maintenu par Google, bien que d’autres implémentations sont disponibles. Le code généré est efficace et optimisé pour la sérialisation rapide et la désétérialisation des données.

Le format de fil Protobuf est un codage binaire. Il utilise quelques astuces intelligentes pour minimiser le nombre d’octets utilisés pour représenter les messages. La connaissance du format d’encodage binaire n’est pas nécessaire pour utiliser Protobuf. Mais si vous êtes intéressé, vous pouvez en apprendre davantage à ce sujet sur [le site Protocol Buffers](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Suivant précédent](why-grpc.md)
>[Next](protobuf-messages.md)
