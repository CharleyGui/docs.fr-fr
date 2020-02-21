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
# <a name="protobuf-nested-types"></a>Types imbriqués Protobuf

Tout comme C# vous permet de déclarer des classes dans d’autres classes, le tampon de protocole (Protobuf) vous permet d’imbriquer des définitions de message dans d’autres messages. L’exemple suivant montre comment créer des types de messages imbriqués :

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
