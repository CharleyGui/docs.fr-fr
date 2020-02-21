---
title: Types imbriqués Protobuf-gRPC pour les développeurs WCF
description: Découvrez les types de messages imbriqués dans Protobuf et gRPC, ainsi que la façon C#dont ils sont générés dans.
ms.date: 09/09/2019
ms.openlocfilehash: 7b9a331336ebe1ca7bc75fdd164b7b88ae4f9db2
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542844"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="4d0e0-103">Types imbriqués Protobuf</span><span class="sxs-lookup"><span data-stu-id="4d0e0-103">Protobuf nested types</span></span>

<span data-ttu-id="4d0e0-104">Tout comme C# vous permet de déclarer des classes dans d’autres classes, le tampon de protocole (Protobuf) vous permet d’imbriquer des définitions de message dans d’autres messages.</span><span class="sxs-lookup"><span data-stu-id="4d0e0-104">Just as C# allows you to declare classes inside other classes, Protocol Buffer (Protobuf) allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="4d0e0-105">L’exemple suivant montre comment créer des types de messages imbriqués :</span><span class="sxs-lookup"><span data-stu-id="4d0e0-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="4d0e0-106">Dans le code C# généré, le type de `Inner` est déclaré dans une classe statique `Types` imbriquée dans la classe `HelloRequest` :</span><span class="sxs-lookup"><span data-stu-id="4d0e0-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="4d0e0-107">[Précédent](protobuf-data-types.md)
>[Suivant](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="4d0e0-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
