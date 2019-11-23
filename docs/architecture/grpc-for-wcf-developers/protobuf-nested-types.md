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
# <a name="protobuf-nested-types"></a>Types imbriqués Protobuf

Tout comme C# vous permet de déclarer des classes dans d’autres classes, Protobuf vous permet d’imbriquer des définitions de message dans d’autres messages. L’exemple suivant montre comment créer des types de messages imbriqués :

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

Dans le code C# généré, le type de `Inner` est déclaré dans une classe statique `Types` imbriquée dans la classe `HelloRequest` :

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Précédent](protobuf-data-types.md)
>[Suivant](protobuf-repeated.md)
