---
title: Migrer une solution WCF vers gRPC-gRPC pour les développeurs WCF
description: Migration de différents types de services WCF vers l’équivalent dans gRPC.
ms.date: 12/15/2020
ms.openlocfilehash: 3bd35cb6119368ff3db3be9ab5fabf89f2652b29
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97937959"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="2b838-103">Migrer une solution WCF vers gRPC</span><span class="sxs-lookup"><span data-stu-id="2b838-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="2b838-104">Ce chapitre décrit comment utiliser des projets ASP.NET Core 5,0 gRPC et illustre la migration de différents types de services Windows Communication Foundation (WCF) vers l’équivalent gRPC :</span><span class="sxs-lookup"><span data-stu-id="2b838-104">This chapter will describe how to work with ASP.NET Core 5.0 gRPC projects and demonstrate migrating different types of Windows Communication Foundation (WCF) services to the gRPC equivalent:</span></span>

- <span data-ttu-id="2b838-105">Créez un projet ASP.NET Core 5,0 gRPC.</span><span class="sxs-lookup"><span data-stu-id="2b838-105">Create an ASP.NET Core 5.0 gRPC project.</span></span>
- <span data-ttu-id="2b838-106">Opérations de requête-réponse simples pour gRPC RPC unaire.</span><span class="sxs-lookup"><span data-stu-id="2b838-106">Simple request-reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="2b838-107">Opérations unidirectionnelles vers gRPC client streaming RPC.</span><span class="sxs-lookup"><span data-stu-id="2b838-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="2b838-108">Services duplex intégral vers gRPC de diffusion en continu bidirectionnelle RPC.</span><span class="sxs-lookup"><span data-stu-id="2b838-108">Full-duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="2b838-109">Il y a également une comparaison entre l’utilisation de services de streaming et les champs répétés pour le retour de jeux de données, et il existe une discussion sur l’utilisation des bibliothèques clientes à la fin du chapitre.</span><span class="sxs-lookup"><span data-stu-id="2b838-109">There's also a comparison of using streaming services versus repeated fields for returning datasets, and there's a discussion of the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="2b838-110">L’exemple d’application WCF est un stub minimal d’un ensemble de services commerciaux boursiers.</span><span class="sxs-lookup"><span data-stu-id="2b838-110">The sample WCF application is a minimal stub of a set of stock trading services.</span></span> <span data-ttu-id="2b838-111">Il utilise la bibliothèque de conteneurs inversion Open source de Control (IoC) appelée Autofac pour l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="2b838-111">It uses the open-source Inversion of Control (IoC) container library called Autofac for dependency injection.</span></span> <span data-ttu-id="2b838-112">Il comprend trois services, un pour chaque type de service WCF.</span><span class="sxs-lookup"><span data-stu-id="2b838-112">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="2b838-113">Les services seront abordés plus en détail dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="2b838-113">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="2b838-114">Vous pouvez télécharger les solutions à partir de [dotnet-architecture/GRPC-pour-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="2b838-114">You can download the solutions from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="2b838-115">Les services utilisent des données factices pour réduire les dépendances externes.</span><span class="sxs-lookup"><span data-stu-id="2b838-115">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="2b838-116">Les exemples incluent les implémentations WCF et gRPC de chaque service.</span><span class="sxs-lookup"><span data-stu-id="2b838-116">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2b838-117">[Précédent](ws-protocols.md) 
> [Suivant](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="2b838-117">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
