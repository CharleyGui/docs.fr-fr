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
# <a name="serialization-breaking-changes"></a><span data-ttu-id="b9f6b-103">Modifications avec rupture de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="b9f6b-103">Serialization breaking changes</span></span>

<span data-ttu-id="b9f6b-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="b9f6b-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="b9f6b-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="b9f6b-105">Breaking change</span></span> | <span data-ttu-id="b9f6b-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b9f6b-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="b9f6b-107">Constructeurs non publics, sans paramètre, non utilisés pour la désérialisation</span><span class="sxs-lookup"><span data-stu-id="b9f6b-107">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="b9f6b-108">5.0</span><span class="sxs-lookup"><span data-stu-id="b9f6b-108">5.0</span></span> |
| [<span data-ttu-id="b9f6b-109">JsonSerializer. Serialize lève une exception ArgumentNullException lorsque le paramètre de type est null</span><span class="sxs-lookup"><span data-stu-id="b9f6b-109">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="b9f6b-110">5.0</span><span class="sxs-lookup"><span data-stu-id="b9f6b-110">5.0</span></span> |
| [<span data-ttu-id="b9f6b-111">JsonSerializer. Deserialize requiert une chaîne à un seul caractère</span><span class="sxs-lookup"><span data-stu-id="b9f6b-111">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="b9f6b-112">5.0</span><span class="sxs-lookup"><span data-stu-id="b9f6b-112">5.0</span></span> |
| [<span data-ttu-id="b9f6b-113">BinaryFormatter. Deserialize réencapsule certaines exceptions dans SerializationException</span><span class="sxs-lookup"><span data-stu-id="b9f6b-113">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="b9f6b-114">5.0</span><span class="sxs-lookup"><span data-stu-id="b9f6b-114">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="b9f6b-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="b9f6b-115">.NET 5.0</span></span>

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

***

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
