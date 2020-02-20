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
# <a name="protocol-buffers"></a><span data-ttu-id="00ab9-103">Mémoires tampons de protocole</span><span class="sxs-lookup"><span data-stu-id="00ab9-103">Protocol buffers</span></span>

<span data-ttu-id="00ab9-104">les services gRPC envoient et reçoivent des données sous forme de *messages de tampon de protocole (Protobuf)* , similaires aux contrats de données dans Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="00ab9-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to data contracts in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="00ab9-105">Protobuf est un moyen efficace de sérialiser des données structurées pour que les ordinateurs puissent les lire et les écrire, sans la surcharge que les formats explicites, tels que XML ou JSON, impliquent.</span><span class="sxs-lookup"><span data-stu-id="00ab9-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="00ab9-106">Ce chapitre explique comment fonctionne Protobuf et comment définir vos propres messages Protobuf.</span><span class="sxs-lookup"><span data-stu-id="00ab9-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="00ab9-107">Fonctionnement de Protobuf</span><span class="sxs-lookup"><span data-stu-id="00ab9-107">How Protobuf works</span></span>

<span data-ttu-id="00ab9-108">La plupart des techniques de sérialisation d’objets .NET, y compris les contrats de données WCF, fonctionnent à l’aide de la réflexion pour analyser la structure d’objets au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="00ab9-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at runtime.</span></span> <span data-ttu-id="00ab9-109">En revanche, la plupart des bibliothèques Protobuf nécessitent que vous définissiez la structure en amont à l’aide d’un langage dédié (langue de la*mémoire tampon du protocole*) dans un fichier de `.proto`.</span><span class="sxs-lookup"><span data-stu-id="00ab9-109">By contrast, most Protobuf libraries require you to define the structure up front by using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="00ab9-110">Un compilateur utilise ensuite ce fichier pour générer le code pour toutes les plateformes prises en charge.</span><span class="sxs-lookup"><span data-stu-id="00ab9-110">A compiler then uses this file to generate code for any of the supported platforms.</span></span> <span data-ttu-id="00ab9-111">Les plateformes prises en charge incluent .NET,C++Java, C/, JavaScript et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="00ab9-111">Supported platforms include .NET, Java, C/C++, JavaScript, and many more.</span></span> 

<span data-ttu-id="00ab9-112">Le compilateur Protobuf, `protoc`, est géré par Google, bien que d’autres implémentations soient disponibles.</span><span class="sxs-lookup"><span data-stu-id="00ab9-112">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="00ab9-113">Le code généré est efficace et optimisé pour la sérialisation et la désérialisation rapides des données.</span><span class="sxs-lookup"><span data-stu-id="00ab9-113">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="00ab9-114">Le format de câble Protobuf est un encodage binaire.</span><span class="sxs-lookup"><span data-stu-id="00ab9-114">The Protobuf wire format is a binary encoding.</span></span> <span data-ttu-id="00ab9-115">Il utilise des astuces astucieuses pour réduire le nombre d’octets utilisés pour représenter les messages.</span><span class="sxs-lookup"><span data-stu-id="00ab9-115">It uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="00ab9-116">La connaissance du format d’encodage binaire n’est pas nécessaire pour utiliser Protobuf.</span><span class="sxs-lookup"><span data-stu-id="00ab9-116">Knowledge of the binary encoding format isn't necessary to use Protobuf.</span></span> <span data-ttu-id="00ab9-117">Mais si cela vous intéresse, vous pouvez en savoir plus à ce sujet sur [le site Web de mémoires tampons de protocole](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="00ab9-117">But if you're interested, you can learn more about it on [the Protocol Buffers website](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="00ab9-118">[Précédent](why-grpc.md)
>[Suivant](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="00ab9-118">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
