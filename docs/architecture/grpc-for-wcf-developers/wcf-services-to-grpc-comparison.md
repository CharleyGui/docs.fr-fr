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
# <a name="comparing-wcf-to-grpc"></a>Comparaison de WCF et de gRPC

Le chapitre précédent vous a donné un aperçu de Protobuf et explique comment gRPC gère les messages. Avant de travailler dans une conversion détaillée de Windows Communication Foundation (WCF) vers gRPC, il est important de savoir comment les fonctionnalités disponibles dans WCF sont gérées dans gRPC et les solutions de contournement que vous pouvez utiliser lorsqu’il n’existe aucun équivalent gRPC. En particulier, ce chapitre aborde les sujets suivants :

- Opérations et méthodes
- Liaisons et transports
- Types RPC
- Métadonnées
- Gestion des erreurs
- Protocoles WS-\*

## <a name="grpc-example"></a>exemple gRPC

Lorsque vous créez un projet ASP.NET Core 3,0 gRPC à partir de Visual Studio 2019 ou de la ligne de commande, l’équivalent gRPC de « Hello World » est généré pour vous. Il se compose d’un fichier `greeter.proto` qui définit le service et de ses messages, et d’un fichier `GreeterService.cs` avec une implémentation du service.

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

Ce chapitre fait référence à cet exemple de code lors de l’explication des différents concepts et fonctionnalités de gRPC.

>[!div class="step-by-step"]
>[Précédent](protobuf-maps.md)
>[Suivant](wcf-endpoints-grpc-methods.md)
