---
title: Types imbriqués Protobuf-gRPC pour les développeurs WCF
description: Découvrez les types de messages imbriqués dans Protobuf et gRPC, ainsi que la façon C#dont ils sont générés dans.
ms.date: 09/09/2019
ms.openlocfilehash: bbc7ed41516d29f867bbc9da5b258f6a3c9ff261
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967394"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="21049-103">Types imbriqués Protobuf</span><span class="sxs-lookup"><span data-stu-id="21049-103">Protobuf nested types</span></span>

<span data-ttu-id="21049-104">Tout comme C# vous permet de déclarer des classes dans d’autres classes, Protobuf vous permet d’imbriquer des définitions de message dans d’autres messages.</span><span class="sxs-lookup"><span data-stu-id="21049-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="21049-105">L’exemple suivant montre comment créer des types de messages imbriqués :</span><span class="sxs-lookup"><span data-stu-id="21049-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="21049-106">Dans le code C# généré, le type de `Inner` est déclaré dans une classe statique `Types` imbriquée dans la classe `HelloRequest` :</span><span class="sxs-lookup"><span data-stu-id="21049-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="21049-107">[Précédent](protobuf-data-types.md)
>[Suivant](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="21049-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
