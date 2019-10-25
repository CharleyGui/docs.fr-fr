---
title: Types imbriqués Protobuf-gRPC pour les développeurs WCF
description: Découvrez les types de messages imbriqués dans Protobuf et gRPC, ainsi que la façon C#dont ils sont générés dans.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ec9fc522619230c1201bfef1e8128f7356936212
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846313"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="87909-103">Types imbriqués Protobuf</span><span class="sxs-lookup"><span data-stu-id="87909-103">Protobuf nested types</span></span>

<span data-ttu-id="87909-104">Tout comme C# vous permet de déclarer des classes dans d’autres classes, Protobuf vous permet d’imbriquer des définitions de message dans d’autres messages.</span><span class="sxs-lookup"><span data-stu-id="87909-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="87909-105">L’exemple suivant montre comment créer des types de messages imbriqués :</span><span class="sxs-lookup"><span data-stu-id="87909-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="87909-106">Dans le code C# généré, le type de`Inner`est déclaré dans une classe statique`Types`imbriquée dans la classe`HelloRequest`:</span><span class="sxs-lookup"><span data-stu-id="87909-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="87909-107">[Précédent](protobuf-data-types.md)
>[Suivant](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="87909-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
