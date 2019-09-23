---
title: Types imbriqués Protobuf-gRPC pour les développeurs WCF
description: Découvrez les types de messages imbriqués dans Protobuf et gRPC, ainsi que la façon C#dont ils sont générés dans.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 39bc52b37cc9e57cfe0ed5a5118c348de5f014d8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184189"
---
# <a name="protobuf-nested-types"></a>Types imbriqués Protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Tout comme C# vous permet de déclarer des classes dans d’autres classes, Protobuf vous permet d’imbriquer des définitions de message dans d’autres messages. L’exemple suivant montre comment créer des types de messages imbriqués :

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

Dans le code C# généré, le `Inner` type sera déclaré dans une classe statique `Types` imbriquée dans la `HelloRequest` classe :

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Précédent](protobuf-data-types.md)
>[Suivant](protobuf-repeated.md)
