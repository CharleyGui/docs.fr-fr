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
# <a name="protobuf-nested-types"></a><span data-ttu-id="3eb4b-103">Types imbriqués Protobuf</span><span class="sxs-lookup"><span data-stu-id="3eb4b-103">Protobuf nested types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="3eb4b-104">Tout comme C# vous permet de déclarer des classes dans d’autres classes, Protobuf vous permet d’imbriquer des définitions de message dans d’autres messages.</span><span class="sxs-lookup"><span data-stu-id="3eb4b-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="3eb4b-105">L’exemple suivant montre comment créer des types de messages imbriqués :</span><span class="sxs-lookup"><span data-stu-id="3eb4b-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="3eb4b-106">Dans le code C# généré, le `Inner` type sera déclaré dans une classe statique `Types` imbriquée dans la `HelloRequest` classe :</span><span class="sxs-lookup"><span data-stu-id="3eb4b-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="3eb4b-107">[Précédent](protobuf-data-types.md)
>[Suivant](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="3eb4b-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
