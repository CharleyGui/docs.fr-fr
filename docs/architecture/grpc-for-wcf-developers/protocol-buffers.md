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
# <a name="protocol-buffers"></a><span data-ttu-id="e0e6a-103">Tampons de protocole</span><span class="sxs-lookup"><span data-stu-id="e0e6a-103">Protocol buffers</span></span>

<span data-ttu-id="e0e6a-104">les services gRPC envoient et reçoivent des données sous forme *de messages Protocol Buffer (Protobuf),* similaires aux contrats de données de la Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e0e6a-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to data contracts in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e0e6a-105">Protobuf est un moyen efficace de sérialisation des données structurées pour les machines à lire et à écrire, sans les frais généraux que les formats lisibles par l’homme comme XML ou JSON encourent.</span><span class="sxs-lookup"><span data-stu-id="e0e6a-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="e0e6a-106">Ce chapitre couvre le fonctionnement de Protobuf et la façon de définir vos propres messages Protobuf.</span><span class="sxs-lookup"><span data-stu-id="e0e6a-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="e0e6a-107">Fonctionnement de Protobuf</span><span class="sxs-lookup"><span data-stu-id="e0e6a-107">How Protobuf works</span></span>

<span data-ttu-id="e0e6a-108">La plupart des techniques de sérialisation d’objets .NET, y compris les contrats de données de WCF, fonctionnent en utilisant la réflexion pour analyser la structure de l’objet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e0e6a-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at runtime.</span></span> <span data-ttu-id="e0e6a-109">En revanche, la plupart des bibliothèques Protobuf vous obligent à définir la `.proto` structure à l’avance en utilisant une langue dédiée ( Langage tampon de*protocole*) dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="e0e6a-109">By contrast, most Protobuf libraries require you to define the structure up front by using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="e0e6a-110">Un compilateur utilise ensuite ce fichier pour générer du code pour l’une des plates-formes prises en charge.</span><span class="sxs-lookup"><span data-stu-id="e0e6a-110">A compiler then uses this file to generate code for any of the supported platforms.</span></span> <span data-ttu-id="e0e6a-111">Les plates-formes prises en charge comprennent .NET, Java, C/C, JavaScript, et bien d’autres.</span><span class="sxs-lookup"><span data-stu-id="e0e6a-111">Supported platforms include .NET, Java, C/C++, JavaScript, and many more.</span></span>

<span data-ttu-id="e0e6a-112">Le compilateur Protobuf, `protoc`, est maintenu par Google, bien que d’autres implémentations sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="e0e6a-112">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="e0e6a-113">Le code généré est efficace et optimisé pour la sérialisation rapide et la désétérialisation des données.</span><span class="sxs-lookup"><span data-stu-id="e0e6a-113">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="e0e6a-114">Le format de fil Protobuf est un codage binaire.</span><span class="sxs-lookup"><span data-stu-id="e0e6a-114">The Protobuf wire format is a binary encoding.</span></span> <span data-ttu-id="e0e6a-115">Il utilise quelques astuces intelligentes pour minimiser le nombre d’octets utilisés pour représenter les messages.</span><span class="sxs-lookup"><span data-stu-id="e0e6a-115">It uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="e0e6a-116">La connaissance du format d’encodage binaire n’est pas nécessaire pour utiliser Protobuf.</span><span class="sxs-lookup"><span data-stu-id="e0e6a-116">Knowledge of the binary encoding format isn't necessary to use Protobuf.</span></span> <span data-ttu-id="e0e6a-117">Mais si vous êtes intéressé, vous pouvez en apprendre davantage à ce sujet sur [le site Protocol Buffers](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="e0e6a-117">But if you're interested, you can learn more about it on [the Protocol Buffers website](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e0e6a-118">[Suivant précédent](why-grpc.md)
>[Next](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="e0e6a-118">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
