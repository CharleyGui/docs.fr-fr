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

Dans le code C# généré, le type de`Inner`est déclaré dans une classe statique`Types`imbriquée dans la classe`HelloRequest`:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Précédent](protobuf-data-types.md)
>[Suivant](protobuf-repeated.md)
