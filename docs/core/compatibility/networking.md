---
title: Modifications avec rupture réseau
description: Répertorie les dernières modifications apportées à la mise en réseau dans .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: fdbd3f3bdcae5048b4f01e4d827f8a0e876c5c15
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050513"
---
# <a name="networking-breaking-changes"></a>Modifications avec rupture réseau

Les modifications avec rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | - |
| [NegotiateStream et SslStream autorisent les opérations Begin successives](#negotiatestream-and-sslstream-allow-successive-begin-operations) | 5.0 |
| [Socket. LocalEndPoint est mis à jour après l’appel de SendToAsync](#socketlocalendpoint-is-updated-after-calling-sendtoasync) | 5.0 |
| [WinHttpHandler supprimé du Runtime .NET](#winhttphandler-removed-from-net-runtime) | 5.0 |
| [MulticastOption. Group n’accepte pas de valeur null](#multicastoptiongroup-doesnt-accept-a-null-value) | 5.0 |
| [La gestion des chemins d’accès des cookies est maintenant conforme à la norme RFC 6265](#cookie-path-handling-now-conforms-to-rfc-6265) | 5.0 |
| [La valeur par défaut de HttpRequestMessage. version est passée à 1,1](#default-value-of-httprequestmessageversion-changed-to-11) | 3.0 |
| [WebClient. CancelAsync n’est pas toujours annulé immédiatement](#webclientcancelasync-doesnt-always-cancel-immediately) | 2.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [negotiatestream-sslstream-dont-fail-on-successive-begin-calls](../../../includes/core-changes/networking/5.0/negotiatestream-sslstream-dont-fail-on-successive-begin-calls.md)]

***

[!INCLUDE [localendpoint-updated-on-sendtoasync](../../../includes/core-changes/networking/5.0/localendpoint-updated-on-sendtoasync.md)]

***

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

[!INCLUDE [cookie-path-conforms-to-rfc6265](../../../includes/core-changes/networking/5.0/cookie-path-conforms-to-rfc6265.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
