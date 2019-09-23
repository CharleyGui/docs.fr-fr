---
title: Mémoires tampons de protocole-gRPC pour les développeurs WCF
description: Présentation du format de câble des mémoires tampons de protocole utilisé pour la mise en réseau gRPC.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 4f9031c86731ea7ded4a812be9967237e52c4b39
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184168"
---
# <a name="protocol-buffers"></a><span data-ttu-id="ad726-103">Mémoires tampons de protocole</span><span class="sxs-lookup"><span data-stu-id="ad726-103">Protocol buffers</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ad726-104">les services gRPC envoient et reçoivent des données sous forme de *messages de tampon de protocole (Protobuf)* , similaires aux contrats de données de WCF.</span><span class="sxs-lookup"><span data-stu-id="ad726-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to WCF's data contracts.</span></span> <span data-ttu-id="ad726-105">Protobuf est un moyen efficace de sérialiser des données structurées pour que les ordinateurs puissent les lire et les écrire, sans la surcharge que les formats explicites, tels que XML ou JSON, impliquent.</span><span class="sxs-lookup"><span data-stu-id="ad726-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="ad726-106">Ce chapitre explique comment fonctionne Protobuf et comment définir vos propres messages Protobuf.</span><span class="sxs-lookup"><span data-stu-id="ad726-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="ad726-107">Fonctionnement de Protobuf</span><span class="sxs-lookup"><span data-stu-id="ad726-107">How Protobuf works</span></span>

<span data-ttu-id="ad726-108">La plupart des techniques de sérialisation d’objets .NET, y compris les contrats de données WCF, fonctionnent à l’aide de la réflexion pour analyser la structure d’objets au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ad726-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at run time.</span></span> <span data-ttu-id="ad726-109">En revanche, la plupart des bibliothèques Protobuf nécessitent que vous définissiez la structure en amont à l’aide d’un langage dédié ( `.proto` langue de la*mémoire tampon du protocole*) dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="ad726-109">By contrast, most Protobuf libraries require you to define the structure up front using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="ad726-110">Ce fichier est ensuite utilisé par un compilateur pour générer du code pour l’une des plateformes prises en charge, y compris .NETC++, Java, C/, JavaScript et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="ad726-110">This file is then used by a compiler to generate code for any of the supported platforms, including .NET, Java, C/C++, JavaScript, and many more.</span></span> <span data-ttu-id="ad726-111">Le compilateur Protobuf, `protoc`, est géré par Google, bien que d’autres implémentations soient disponibles.</span><span class="sxs-lookup"><span data-stu-id="ad726-111">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="ad726-112">Le code généré est efficace et optimisé pour la sérialisation et la désérialisation rapides des données.</span><span class="sxs-lookup"><span data-stu-id="ad726-112">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="ad726-113">Le format de câble Protobuf lui-même est un encodage binaire, qui utilise des astuces astucieuses pour réduire le nombre d’octets utilisés pour représenter les messages.</span><span class="sxs-lookup"><span data-stu-id="ad726-113">The Protobuf wire format itself is a binary encoding, which uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="ad726-114">La connaissance du format d’encodage binaire n’est pas nécessaire pour utiliser Protobuf, mais si vous êtes intéressé, vous pouvez en savoir plus à ce sujet sur [le site Web de mémoires tampons de protocole](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="ad726-114">Knowledge of the binary encoding format isn't necessary to use Protobuf, but if you're interested you can learn more about it on [the Protocol Buffers web site](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ad726-115">[Précédent](why-grpc.md)
>[Suivant](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="ad726-115">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
