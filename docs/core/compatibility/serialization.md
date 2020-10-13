---
title: Modifications avec rupture de la sérialisation
description: Répertorie les dernières modifications apportées à la catégorie de sérialisation dans .NET Core et .NET 5,0 et versions ultérieures.
ms.date: 07/30/2020
ms.openlocfilehash: 6902ef8eb2dc23610ef532ff57b755456648ffb0
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997714"
---
# <a name="serialization-breaking-changes"></a>Modifications avec rupture de la sérialisation

Les modifications avec rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | - |
| [Constructeurs non publics, sans paramètre, non utilisés pour la désérialisation](#non-public-parameterless-constructors-not-used-for-deserialization) | 5.0 |
| [JsonSerializer. Serialize lève une exception ArgumentNullException lorsque le paramètre de type est null](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | 5.0 |
| [JsonSerializer. Deserialize requiert une chaîne à un seul caractère](#jsonserializerdeserialize-requires-single-character-string) | 5.0 |
| [BinaryFormatter. Deserialize réencapsule certaines exceptions dans SerializationException](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | 5.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

***

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
