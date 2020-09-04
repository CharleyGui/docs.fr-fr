---
title: Modifications avec rupture réseau
description: Répertorie les dernières modifications apportées à la mise en réseau dans .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: fa5807c882c3bc6f66e8a27361ccc14254e90b3e
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465510"
---
# <a name="networking-breaking-changes"></a><span data-ttu-id="2ac7f-103">Modifications avec rupture réseau</span><span class="sxs-lookup"><span data-stu-id="2ac7f-103">Networking breaking changes</span></span>

<span data-ttu-id="2ac7f-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="2ac7f-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="2ac7f-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="2ac7f-105">Breaking change</span></span> | <span data-ttu-id="2ac7f-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2ac7f-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="2ac7f-107">WinHttpHandler supprimé du Runtime .NET</span><span class="sxs-lookup"><span data-stu-id="2ac7f-107">WinHttpHandler removed from .NET runtime</span></span>](#winhttphandler-removed-from-net-runtime) | <span data-ttu-id="2ac7f-108">5.0</span><span class="sxs-lookup"><span data-stu-id="2ac7f-108">5.0</span></span> |
| [<span data-ttu-id="2ac7f-109">MulticastOption. Group n’accepte pas de valeur null</span><span class="sxs-lookup"><span data-stu-id="2ac7f-109">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="2ac7f-110">5.0</span><span class="sxs-lookup"><span data-stu-id="2ac7f-110">5.0</span></span> |
| [<span data-ttu-id="2ac7f-111">La gestion des chemins d’accès des cookies est maintenant conforme à la norme RFC 6265</span><span class="sxs-lookup"><span data-stu-id="2ac7f-111">Cookie Path handling now conforms to RFC 6265</span></span>](#cookie-path-handling-now-conforms-to-rfc-6265) | <span data-ttu-id="2ac7f-112">5.0</span><span class="sxs-lookup"><span data-stu-id="2ac7f-112">5.0</span></span> |
| [<span data-ttu-id="2ac7f-113">La valeur par défaut de HttpRequestMessage. version est passée à 1,1</span><span class="sxs-lookup"><span data-stu-id="2ac7f-113">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="2ac7f-114">3.0</span><span class="sxs-lookup"><span data-stu-id="2ac7f-114">3.0</span></span> |
| [<span data-ttu-id="2ac7f-115">WebClient. CancelAsync n’est pas toujours annulé immédiatement</span><span class="sxs-lookup"><span data-stu-id="2ac7f-115">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="2ac7f-116">2,0</span><span class="sxs-lookup"><span data-stu-id="2ac7f-116">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="2ac7f-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="2ac7f-117">.NET 5.0</span></span>

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

[!INCLUDE [cookie-path-conforms-to-rfc6265](../../../includes/core-changes/networking/5.0/cookie-path-conforms-to-rfc6265.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="2ac7f-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ac7f-118">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="2ac7f-119">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="2ac7f-119">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
