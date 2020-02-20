---
title: Comparaison de WCF à gRPC-gRPC pour les développeurs WCF
description: Comparaison des frameworks WCF et gRPC pour la création d’applications distribuées.
ms.date: 09/02/2019
ms.openlocfilehash: 4f54db76c9512b770b4dd993496d95437dd89753
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503338"
---
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="ba6ce-103">Comparaison de WCF et de gRPC</span><span class="sxs-lookup"><span data-stu-id="ba6ce-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="ba6ce-104">Le chapitre précédent vous a donné un aperçu de Protobuf et explique comment gRPC gère les messages.</span><span class="sxs-lookup"><span data-stu-id="ba6ce-104">The previous chapter gave you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="ba6ce-105">Avant de travailler dans une conversion détaillée de Windows Communication Foundation (WCF) vers gRPC, il est important de savoir comment les fonctionnalités disponibles dans WCF sont gérées dans gRPC et les solutions de contournement que vous pouvez utiliser lorsqu’il n’existe aucun équivalent gRPC.</span><span class="sxs-lookup"><span data-stu-id="ba6ce-105">Before you work through a detailed conversion from Windows Communication Foundation (WCF) to gRPC, it's important know how the features available in WCF are handled in gRPC and what workarounds you can use when there's no gRPC equivalent.</span></span> <span data-ttu-id="ba6ce-106">En particulier, ce chapitre aborde les sujets suivants :</span><span class="sxs-lookup"><span data-stu-id="ba6ce-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="ba6ce-107">Opérations et méthodes</span><span class="sxs-lookup"><span data-stu-id="ba6ce-107">Operations and methods</span></span>
- <span data-ttu-id="ba6ce-108">Liaisons et transports</span><span class="sxs-lookup"><span data-stu-id="ba6ce-108">Bindings and transports</span></span>
- <span data-ttu-id="ba6ce-109">Types RPC</span><span class="sxs-lookup"><span data-stu-id="ba6ce-109">RPC types</span></span>
- <span data-ttu-id="ba6ce-110">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="ba6ce-110">Metadata</span></span>
- <span data-ttu-id="ba6ce-111">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="ba6ce-111">Error handling</span></span>
- <span data-ttu-id="ba6ce-112">Protocoles WS-\*</span><span class="sxs-lookup"><span data-stu-id="ba6ce-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="ba6ce-113">exemple gRPC</span><span class="sxs-lookup"><span data-stu-id="ba6ce-113">gRPC example</span></span>

<span data-ttu-id="ba6ce-114">Lorsque vous créez un projet ASP.NET Core 3,0 gRPC à partir de Visual Studio 2019 ou de la ligne de commande, l’équivalent gRPC de « Hello World » est généré pour vous.</span><span class="sxs-lookup"><span data-stu-id="ba6ce-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="ba6ce-115">Il se compose d’un fichier `greeter.proto` qui définit le service et de ses messages, et d’un fichier `GreeterService.cs` avec une implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="ba6ce-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message that contains the user's name.
message HelloRequest {
  string name = 1;
}

// The response message that contains the greetings.
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

<span data-ttu-id="ba6ce-116">Ce chapitre fait référence à cet exemple de code lors de l’explication des différents concepts et fonctionnalités de gRPC.</span><span class="sxs-lookup"><span data-stu-id="ba6ce-116">This chapter will refer to this example code when explaining different concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ba6ce-117">[Précédent](protobuf-maps.md)
>[Suivant](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="ba6ce-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
