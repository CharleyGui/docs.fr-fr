---
title: Mémoires tampons de protocole-gRPC pour les développeurs WCF
description: Présentation du format de câble des mémoires tampons de protocole utilisé pour la mise en réseau gRPC.
ms.date: 09/09/2019
ms.openlocfilehash: cc4ff272a9912d6f2dd8f8ddb1972c7369f980fe
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503459"
---
# <a name="protocol-buffers"></a>Mémoires tampons de protocole

les services gRPC envoient et reçoivent des données sous forme de *messages de tampon de protocole (Protobuf)* , similaires aux contrats de données dans Windows Communication Foundation (WCF). Protobuf est un moyen efficace de sérialiser des données structurées pour que les ordinateurs puissent les lire et les écrire, sans la surcharge que les formats explicites, tels que XML ou JSON, impliquent.

Ce chapitre explique comment fonctionne Protobuf et comment définir vos propres messages Protobuf.

## <a name="how-protobuf-works"></a>Fonctionnement de Protobuf

La plupart des techniques de sérialisation d’objets .NET, y compris les contrats de données WCF, fonctionnent à l’aide de la réflexion pour analyser la structure d’objets au moment de l’exécution. En revanche, la plupart des bibliothèques Protobuf nécessitent que vous définissiez la structure en amont à l’aide d’un langage dédié (langue de la*mémoire tampon du protocole*) dans un fichier de `.proto`. Un compilateur utilise ensuite ce fichier pour générer le code pour toutes les plateformes prises en charge. Les plateformes prises en charge incluent .NET,C++Java, C/, JavaScript et bien plus encore. 

Le compilateur Protobuf, `protoc`, est géré par Google, bien que d’autres implémentations soient disponibles. Le code généré est efficace et optimisé pour la sérialisation et la désérialisation rapides des données.

Le format de câble Protobuf est un encodage binaire. Il utilise des astuces astucieuses pour réduire le nombre d’octets utilisés pour représenter les messages. La connaissance du format d’encodage binaire n’est pas nécessaire pour utiliser Protobuf. Mais si cela vous intéresse, vous pouvez en savoir plus à ce sujet sur [le site Web de mémoires tampons de protocole](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Précédent](why-grpc.md)
>[Suivant](protobuf-messages.md)
