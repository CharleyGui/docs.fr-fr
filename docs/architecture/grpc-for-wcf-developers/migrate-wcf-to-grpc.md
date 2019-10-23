---
title: Migrer une solution WCF vers gRPC-gRPC pour les développeurs WCF
description: Comment migrer différents types de service WCF vers l’équivalent dans gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 77bcb1412803b371778943763308c3010ed35aac
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770113"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="7756a-103">Migrer une solution WCF vers gRPC</span><span class="sxs-lookup"><span data-stu-id="7756a-103">Migrate a WCF solution to gRPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="7756a-104">Ce chapitre aborde l’utilisation des projets ASP.NET Core 3,0 gRPC et montre comment migrer différents types de service WCF vers l’équivalent gRPC :</span><span class="sxs-lookup"><span data-stu-id="7756a-104">This chapter will look at how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of WCF service to the gRPC equivalent:</span></span>

- <span data-ttu-id="7756a-105">Créez un projet ASP.NET Core 3,0 gRPC.</span><span class="sxs-lookup"><span data-stu-id="7756a-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="7756a-106">Opérations de requête-réponse simples pour gRPC RPC unaire.</span><span class="sxs-lookup"><span data-stu-id="7756a-106">Simple Request-Reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="7756a-107">Opérations unidirectionnelles vers gRPC client streaming RPC.</span><span class="sxs-lookup"><span data-stu-id="7756a-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="7756a-108">Services duplex intégral vers gRPC de diffusion en continu bidirectionnelle RPC.</span><span class="sxs-lookup"><span data-stu-id="7756a-108">Full Duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="7756a-109">Il y a également une comparaison entre l’utilisation de services de streaming et les champs répétés pour le renvoi de jeux de données, ainsi que l’utilisation des bibliothèques clientes à la fin du chapitre.</span><span class="sxs-lookup"><span data-stu-id="7756a-109">There's also a comparison of using streaming services versus repeated fields for returning data sets, and the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="7756a-110">L’exemple d’application WCF est un stub minimal d’un ensemble de services commerciaux boursiers, à l’aide de la bibliothèque de conteneurs IoC (inversion Open source of Control) appelée *Autofac* pour l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="7756a-110">The sample WCF application is a minimal stub of a set of stock trading services, using the open-source Inversion of Control (IoC) container library called *Autofac* for dependency injection.</span></span> <span data-ttu-id="7756a-111">Il comprend trois services, un pour chaque type de service WCF.</span><span class="sxs-lookup"><span data-stu-id="7756a-111">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="7756a-112">Les services seront abordés plus en détail dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="7756a-112">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="7756a-113">Les solutions peuvent être téléchargées à partir de [dotnet-architecture/GRPC-pour-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="7756a-113">The solutions can be downloaded from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="7756a-114">Les services utilisent des données factices pour réduire les dépendances externes.</span><span class="sxs-lookup"><span data-stu-id="7756a-114">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="7756a-115">Les exemples incluent les implémentations WCF et gRPC de chaque service.</span><span class="sxs-lookup"><span data-stu-id="7756a-115">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7756a-116">[Précédent](ws-protocols.md)
>[Suivant](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="7756a-116">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
