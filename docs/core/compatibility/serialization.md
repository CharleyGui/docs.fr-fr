---
title: Modifications avec rupture de la sérialisation
description: Répertorie les dernières modifications apportées à la catégorie de sérialisation dans .NET Core et .NET 5,0 et versions ultérieures.
ms.date: 07/30/2020
ms.openlocfilehash: 67608c8e7a9745c060b7eb179fe5a956ede9f80f
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332876"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="47f78-103">Modifications avec rupture de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="47f78-103">Serialization breaking changes</span></span>

<span data-ttu-id="47f78-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="47f78-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="47f78-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="47f78-105">Breaking change</span></span> | <span data-ttu-id="47f78-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="47f78-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="47f78-107">Les applications ASP.NET Core autorisent la désérialisation des nombres entre guillemets</span><span class="sxs-lookup"><span data-stu-id="47f78-107">ASP.NET Core apps allow deserializing quoted numbers</span></span>](#aspnet-core-apps-allow-deserializing-quoted-numbers) | <span data-ttu-id="47f78-108">5.0</span><span class="sxs-lookup"><span data-stu-id="47f78-108">5.0</span></span> |
| [<span data-ttu-id="47f78-109">Les options PropertyNamingPolicy, PropertyNameCaseInsensitive et encoder sont respectées lors de la sérialisation et de la désérialisation des paires clé-valeur</span><span class="sxs-lookup"><span data-stu-id="47f78-109">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | <span data-ttu-id="47f78-110">5.0</span><span class="sxs-lookup"><span data-stu-id="47f78-110">5.0</span></span> |
| [<span data-ttu-id="47f78-111">Constructeurs non publics, sans paramètre, non utilisés pour la désérialisation</span><span class="sxs-lookup"><span data-stu-id="47f78-111">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="47f78-112">5.0</span><span class="sxs-lookup"><span data-stu-id="47f78-112">5.0</span></span> |
| [<span data-ttu-id="47f78-113">JsonSerializer. Serialize lève une exception ArgumentNullException lorsque le paramètre de type est null</span><span class="sxs-lookup"><span data-stu-id="47f78-113">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="47f78-114">5.0</span><span class="sxs-lookup"><span data-stu-id="47f78-114">5.0</span></span> |
| [<span data-ttu-id="47f78-115">JsonSerializer. Deserialize requiert une chaîne à un seul caractère</span><span class="sxs-lookup"><span data-stu-id="47f78-115">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="47f78-116">5.0</span><span class="sxs-lookup"><span data-stu-id="47f78-116">5.0</span></span> |
| [<span data-ttu-id="47f78-117">BinaryFormatter. Deserialize réencapsule certaines exceptions dans SerializationException</span><span class="sxs-lookup"><span data-stu-id="47f78-117">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="47f78-118">5.0</span><span class="sxs-lookup"><span data-stu-id="47f78-118">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="47f78-119">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="47f78-119">.NET 5.0</span></span>

[!INCLUDE [jsonserializer-allows-reading-numbers-as-strings](../../../includes/core-changes/serialization/5.0/jsonserializer-allows-reading-numbers-as-strings.md)]

***

[!INCLUDE [options-honored-when-serializing-key-value-pairs](../../../includes/core-changes/serialization/5.0/options-honored-when-serializing-key-value-pairs.md)]

<span data-ttu-id="47f78-120">\*\*_</span><span class="sxs-lookup"><span data-stu-id="47f78-120">\*\*_</span></span>

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

_*_

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

_*_

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

_*_

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

<span data-ttu-id="47f78-121">_\*\*</span><span class="sxs-lookup"><span data-stu-id="47f78-121">_\*\*</span></span>
