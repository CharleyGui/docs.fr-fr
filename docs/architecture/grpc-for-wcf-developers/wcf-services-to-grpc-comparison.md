---
title: Comparaison de WCF à gRPC-gRPC pour les développeurs WCF
description: Comparaison des frameworks WCF et gRPC pour la création d’applications distribuées.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: c763048d09e7ed5ca0a3d5240f6b3cf5262f897c
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184042"
---
# <a name="comparing-wcf-to-grpc"></a>Comparaison de WCF et de gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Le chapitre précédent doit vous avoir donné un aperçu de Protobuf et de la façon dont gRPC gère les messages. Avant de procéder à une conversion détaillée de WCF en gRPC, il est important de savoir comment la gamme de fonctionnalités actuellement disponibles dans WCF est gérée dans gRPC, ainsi que les solutions de contournement que vous pouvez utiliser lorsqu’il n’apparaît pas comme équivalent à gRPC. En particulier, ce chapitre aborde les sujets suivants :

- Opérations et méthodes
- Liaisons et transports
- Types RPC
- Métadonnées
- Gestion des erreurs
- WS-\* protocoles

## <a name="grpc-example"></a>exemple gRPC

Lorsque vous créez un projet ASP.NET Core 3,0 gRPC à partir de Visual Studio 2019 ou de la ligne de commande, l’équivalent gRPC de « Hello World » est généré pour vous. Il se compose d' `greeter.proto` un fichier qui définit le service et de ses messages, `GreeterService.cs` et d’un fichier avec une implémentation du service.

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

Ce chapitre fait référence à cet exemple de code lors de l’explication des différents concepts et fonctionnalités de gRPC.

>[!div class="step-by-step"]
>[Précédent](protobuf-maps.md)
>[Suivant](wcf-endpoints-grpc-methods.md)
