---
ms.openlocfilehash: e450c53008e7562e37518fdfd6872ff9b63b6ac3
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609130"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>L’état de session de partage avec ASP.NET StateServer nécessite que tous les serveurs de la batterie de serveurs Web utilisent la même version de .NET Framework

#### <a name="details"></a>Détails

Lors de l’activation de l’état de session <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>, tous les serveurs dans la batterie de serveurs web donnée doivent utiliser la même version du .NET Framework pour que l’état soit correctement partagé.

#### <a name="suggestion"></a>Suggestion

Veillez à mettre à niveau les versions du .NET Framework sur les serveurs web qui partagent l’état en même temps.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->
