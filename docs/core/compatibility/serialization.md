---
title: Modifications avec rupture de la sérialisation
description: Répertorie les dernières modifications apportées à la catégorie de sérialisation dans .NET Core et .NET 5,0 et versions ultérieures.
ms.date: 07/30/2020
ms.openlocfilehash: 65006e6fb45ed2d54699c9972e0489e3ac5ac8bc
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955332"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="fc451-103">Modifications avec rupture de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="fc451-103">Serialization breaking changes</span></span>

<span data-ttu-id="fc451-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="fc451-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="fc451-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="fc451-105">Breaking change</span></span> | <span data-ttu-id="fc451-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fc451-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="fc451-107">JsonSerializer. Serialize lève une exception ArgumentNullException lorsque le paramètre de type est null</span><span class="sxs-lookup"><span data-stu-id="fc451-107">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="fc451-108">5.0</span><span class="sxs-lookup"><span data-stu-id="fc451-108">5.0</span></span> |
| [<span data-ttu-id="fc451-109">JsonSerializer. Deserialize requiert une chaîne à un seul caractère</span><span class="sxs-lookup"><span data-stu-id="fc451-109">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="fc451-110">5.0</span><span class="sxs-lookup"><span data-stu-id="fc451-110">5.0</span></span> |
| [<span data-ttu-id="fc451-111">BinaryFormatter. Deserialize réencapsule certaines exceptions dans SerializationException</span><span class="sxs-lookup"><span data-stu-id="fc451-111">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="fc451-112">5.0</span><span class="sxs-lookup"><span data-stu-id="fc451-112">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="fc451-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="fc451-113">.NET 5.0</span></span>

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
