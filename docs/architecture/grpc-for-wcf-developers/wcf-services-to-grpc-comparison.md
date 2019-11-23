---
title: Comparaison de WCF à gRPC-gRPC pour les développeurs WCF
description: Comparaison des frameworks WCF et gRPC pour la création d’applications distribuées.
ms.date: 09/02/2019
ms.openlocfilehash: 312492dcce4bdef61feff0bf924c6df287b9c676
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966954"
---
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="4d45f-103">Comparaison de WCF et de gRPC</span><span class="sxs-lookup"><span data-stu-id="4d45f-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="4d45f-104">Le chapitre précédent doit vous avoir donné un aperçu de Protobuf et de la façon dont gRPC gère les messages.</span><span class="sxs-lookup"><span data-stu-id="4d45f-104">The previous chapter should have given you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="4d45f-105">Avant de procéder à une conversion détaillée de WCF en gRPC, il est important de savoir comment la gamme de fonctionnalités actuellement disponibles dans WCF est gérée dans gRPC, ainsi que les solutions de contournement que vous pouvez utiliser lorsqu’il n’apparaît pas comme équivalent à gRPC.</span><span class="sxs-lookup"><span data-stu-id="4d45f-105">Before working through a detailed conversion from WCF to gRPC, it's important to look at how the range of features currently available in WCF are handled in gRPC and what workarounds you can use when there doesn't appear to be a gRPC equivalent.</span></span> <span data-ttu-id="4d45f-106">En particulier, ce chapitre aborde les sujets suivants :</span><span class="sxs-lookup"><span data-stu-id="4d45f-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="4d45f-107">Opérations et méthodes</span><span class="sxs-lookup"><span data-stu-id="4d45f-107">Operations and methods</span></span>
- <span data-ttu-id="4d45f-108">Liaisons et transports</span><span class="sxs-lookup"><span data-stu-id="4d45f-108">Bindings and transports</span></span>
- <span data-ttu-id="4d45f-109">Types RPC</span><span class="sxs-lookup"><span data-stu-id="4d45f-109">RPC types</span></span>
- <span data-ttu-id="4d45f-110">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="4d45f-110">Metadata</span></span>
- <span data-ttu-id="4d45f-111">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="4d45f-111">Error handling</span></span>
- <span data-ttu-id="4d45f-112">Protocoles WS-\*</span><span class="sxs-lookup"><span data-stu-id="4d45f-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="4d45f-113">exemple gRPC</span><span class="sxs-lookup"><span data-stu-id="4d45f-113">gRPC example</span></span>

<span data-ttu-id="4d45f-114">Lorsque vous créez un projet ASP.NET Core 3,0 gRPC à partir de Visual Studio 2019 ou de la ligne de commande, l’équivalent gRPC de « Hello World » est généré pour vous.</span><span class="sxs-lookup"><span data-stu-id="4d45f-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="4d45f-115">Il se compose d’un fichier `greeter.proto` qui définit le service et de ses messages, et d’un fichier `GreeterService.cs` avec une implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="4d45f-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings.
message HelloReply {
  string message = 1;
}
```

```csharp
using System.Threading.Tasks;
using Grpc.Core;
using Microsoft.Extensions.Logging;

namespace HelloGrpc
{
    public class GreeterService : Greeter.GreeterBase
    {
        private readonly ILogger<GreeterService> _logger;
        public GreeterService(ILogger<GreeterService> logger)
        {
            _logger = logger;
        }

        public override Task<HelloReply> SayHello(HelloRequest request, ServerCallContext context)
        {
            return Task.FromResult(new HelloReply
            {
                Message = "Hello " + request.Name
            });
        }
    }
}
```

<span data-ttu-id="4d45f-116">Ce chapitre fait référence à cet exemple de code lors de l’explication des différents concepts et fonctionnalités de gRPC.</span><span class="sxs-lookup"><span data-stu-id="4d45f-116">This chapter will refer to this example code when explaining various concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4d45f-117">[Précédent](protobuf-maps.md)
>[Suivant](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="4d45f-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
