---
title: Modifications avec rupture de la sérialisation
description: Répertorie les dernières modifications apportées à la catégorie de sérialisation dans .NET Core et .NET 5,0 et versions ultérieures.
ms.date: 07/30/2020
ms.openlocfilehash: bb6bd650afeba426edc6e102076f05f97f8e0598
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050462"
---
# <a name="serialization-breaking-changes"></a>Modifications avec rupture de la sérialisation

Les modifications avec rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | - |
| [Les options PropertyNamingPolicy, PropertyNameCaseInsensitive et encoder sont respectées lors de la sérialisation et de la désérialisation des paires clé-valeur](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | 5.0 |
| [Constructeurs non publics, sans paramètre, non utilisés pour la désérialisation](#non-public-parameterless-constructors-not-used-for-deserialization) | 5.0 |
| [JsonSerializer. Serialize lève une exception ArgumentNullException lorsque le paramètre de type est null](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | 5.0 |
| [JsonSerializer. Deserialize requiert une chaîne à un seul caractère](#jsonserializerdeserialize-requires-single-character-string) | 5.0 |
| [BinaryFormatter. Deserialize réencapsule certaines exceptions dans SerializationException](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | 5.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [options-honored-when-serializing-key-value-pairs](../../../includes/core-changes/serialization/5.0/options-honored-when-serializing-key-value-pairs.md)]

***

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

***

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
