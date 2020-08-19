---
title: Modifications avec rupture réseau
description: Répertorie les dernières modifications apportées à la mise en réseau dans .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: 5d27f9663a2c1b79610ab002a03beeafa8b2818e
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557960"
---
# <a name="networking-breaking-changes"></a><span data-ttu-id="e8f43-103">Modifications avec rupture réseau</span><span class="sxs-lookup"><span data-stu-id="e8f43-103">Networking breaking changes</span></span>

<span data-ttu-id="e8f43-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="e8f43-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="e8f43-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="e8f43-105">Breaking change</span></span> | <span data-ttu-id="e8f43-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e8f43-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="e8f43-107">MulticastOption. Group n’accepte pas de valeur null</span><span class="sxs-lookup"><span data-stu-id="e8f43-107">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="e8f43-108">5.0</span><span class="sxs-lookup"><span data-stu-id="e8f43-108">5.0</span></span> |
| [<span data-ttu-id="e8f43-109">La valeur par défaut de HttpRequestMessage. version est passée à 1,1</span><span class="sxs-lookup"><span data-stu-id="e8f43-109">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="e8f43-110">3.0</span><span class="sxs-lookup"><span data-stu-id="e8f43-110">3.0</span></span> |
| [<span data-ttu-id="e8f43-111">WebClient. CancelAsync n’est pas toujours annulé immédiatement</span><span class="sxs-lookup"><span data-stu-id="e8f43-111">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="e8f43-112">2.0</span><span class="sxs-lookup"><span data-stu-id="e8f43-112">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="e8f43-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e8f43-113">.NET 5.0</span></span>

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="e8f43-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e8f43-114">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="e8f43-115">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e8f43-115">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
