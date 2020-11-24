---
title: Modifications avec rupture réseau
description: Répertorie les dernières modifications apportées à la mise en réseau dans .NET Core 2,0 et 3,0.
ms.date: 05/05/2020
ms.openlocfilehash: 761c6481888bcb8e91f7b4212355aca067632495
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689210"
---
# <a name="networking-breaking-changes-in-net-core-20-and-30"></a><span data-ttu-id="8215b-103">Modifications de la mise en réseau avec rupture dans .NET Core 2,0 et 3,0</span><span class="sxs-lookup"><span data-stu-id="8215b-103">Networking breaking changes in .NET Core 2.0 and 3.0</span></span>

<span data-ttu-id="8215b-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="8215b-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="8215b-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="8215b-105">Breaking change</span></span> | <span data-ttu-id="8215b-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="8215b-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="8215b-107">La valeur par défaut de HttpRequestMessage. version est passée à 1,1</span><span class="sxs-lookup"><span data-stu-id="8215b-107">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="8215b-108">3.0</span><span class="sxs-lookup"><span data-stu-id="8215b-108">3.0</span></span> |
| [<span data-ttu-id="8215b-109">WebClient. CancelAsync n’est pas toujours annulé immédiatement</span><span class="sxs-lookup"><span data-stu-id="8215b-109">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="8215b-110">2.0</span><span class="sxs-lookup"><span data-stu-id="8215b-110">2.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="8215b-111">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8215b-111">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="8215b-112">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8215b-112">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
