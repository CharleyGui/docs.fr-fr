---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859613"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a>WebClient. CancelAsync n’est pas toujours annulé immédiatement

À compter de .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> l’appel de n’annule pas immédiatement la requête si la réponse a commencé à extraire.

#### <a name="change-description"></a>Description de la modification

Précédemment, l' <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> appel de a annulé la demande immédiatement. À compter de .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> l’appel de annule la demande immédiatement uniquement si la réponse n’a pas commencé la récupération. Si la réponse a commencé l’extraction, la demande est annulée uniquement après la lecture d’une réponse complète.

Cette modification a été implémentée <xref:System.Net.WebClient> , car l’API est déconseillée en faveur de <xref:System.Net.Http.HttpClient>.

#### <a name="version-introduced"></a>Version introduite

2.0

#### <a name="recommended-action"></a>Action recommandée

Utilisez la <xref:System.Net.Http.HttpClient?displayProperty=fullName> classe au lieu <xref:System.Net.WebClient?displayProperty=fullName>de, qui est déconseillé.

#### <a name="category"></a>Catégorie

Mise en réseau

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->
