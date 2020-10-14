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
# <a name="serialization-breaking-changes"></a><span data-ttu-id="24d37-103">Modifications avec rupture de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="24d37-103">Serialization breaking changes</span></span>

<span data-ttu-id="24d37-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="24d37-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="24d37-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="24d37-105">Breaking change</span></span> | <span data-ttu-id="24d37-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="24d37-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="24d37-107">Les options PropertyNamingPolicy, PropertyNameCaseInsensitive et encoder sont respectées lors de la sérialisation et de la désérialisation des paires clé-valeur</span><span class="sxs-lookup"><span data-stu-id="24d37-107">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | <span data-ttu-id="24d37-108">5.0</span><span class="sxs-lookup"><span data-stu-id="24d37-108">5.0</span></span> |
| [<span data-ttu-id="24d37-109">Constructeurs non publics, sans paramètre, non utilisés pour la désérialisation</span><span class="sxs-lookup"><span data-stu-id="24d37-109">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="24d37-110">5.0</span><span class="sxs-lookup"><span data-stu-id="24d37-110">5.0</span></span> |
| [<span data-ttu-id="24d37-111">JsonSerializer. Serialize lève une exception ArgumentNullException lorsque le paramètre de type est null</span><span class="sxs-lookup"><span data-stu-id="24d37-111">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="24d37-112">5.0</span><span class="sxs-lookup"><span data-stu-id="24d37-112">5.0</span></span> |
| [<span data-ttu-id="24d37-113">JsonSerializer. Deserialize requiert une chaîne à un seul caractère</span><span class="sxs-lookup"><span data-stu-id="24d37-113">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="24d37-114">5.0</span><span class="sxs-lookup"><span data-stu-id="24d37-114">5.0</span></span> |
| [<span data-ttu-id="24d37-115">BinaryFormatter. Deserialize réencapsule certaines exceptions dans SerializationException</span><span class="sxs-lookup"><span data-stu-id="24d37-115">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="24d37-116">5.0</span><span class="sxs-lookup"><span data-stu-id="24d37-116">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="24d37-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="24d37-117">.NET 5.0</span></span>

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
