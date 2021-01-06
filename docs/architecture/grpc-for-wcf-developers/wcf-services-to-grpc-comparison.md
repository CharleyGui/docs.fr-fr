---
title: Comparaison de WCF à gRPC-gRPC pour les développeurs WCF
description: Comparaison des frameworks WCF et gRPC pour la création d’applications distribuées.
ms.date: 12/15/2020
ms.openlocfilehash: 7dd41c3d6f248bb1ef5eacb323b1443c7bc575a7
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938492"
---
# <a name="comparing-wcf-to-grpc"></a>Comparaison de WCF et de gRPC

Le chapitre précédent vous a donné un aperçu de Protobuf et explique comment gRPC gère les messages. Avant de travailler dans une conversion détaillée de Windows Communication Foundation (WCF) vers gRPC, il est important de savoir comment les fonctionnalités disponibles dans WCF sont gérées dans gRPC et les solutions de contournement que vous pouvez utiliser lorsqu’il n’existe aucun équivalent gRPC. En particulier, ce chapitre aborde les sujets suivants :

- Opérations et méthodes
- Liaisons et transports
- Types RPC
- Métadonnées
- Gestion des erreurs
- WS- \* protocoles

## <a name="grpc-example"></a>exemple gRPC

Lorsque vous créez un projet ASP.NET Core 5,0 gRPC à partir de Visual Studio 2019 ou de la ligne de commande, l’équivalent gRPC de « Hello World » est généré pour vous. Il se compose d’un `greeter.proto` fichier qui définit le service et de ses messages, et d’un `GreeterService.cs` fichier avec une implémentation du service.

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
> [Suivant](wcf-endpoints-grpc-methods.md)
