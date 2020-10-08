---
title: Modifications avec rupture de la sérialisation
description: Répertorie les dernières modifications apportées à la catégorie de sérialisation dans .NET Core et .NET 5,0 et versions ultérieures.
ms.date: 07/30/2020
ms.openlocfilehash: d68bb95f4ee2b21a5a5bf002a46a3904543cd4a7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844501"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="f3f63-103">Modifications avec rupture de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="f3f63-103">Serialization breaking changes</span></span>

<span data-ttu-id="f3f63-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="f3f63-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="f3f63-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="f3f63-105">Breaking change</span></span> | <span data-ttu-id="f3f63-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f3f63-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="f3f63-107">JsonSerializer. Deserialize requiert une chaîne à un seul caractère</span><span class="sxs-lookup"><span data-stu-id="f3f63-107">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="f3f63-108">5.0</span><span class="sxs-lookup"><span data-stu-id="f3f63-108">5.0</span></span> |
| [<span data-ttu-id="f3f63-109">BinaryFormatter. Deserialize réencapsule certaines exceptions dans SerializationException</span><span class="sxs-lookup"><span data-stu-id="f3f63-109">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="f3f63-110">5.0</span><span class="sxs-lookup"><span data-stu-id="f3f63-110">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="f3f63-111">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f3f63-111">.NET 5.0</span></span>

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
