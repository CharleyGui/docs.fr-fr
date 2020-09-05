---
ms.openlocfilehash: 76425ca03c98cd6a23b8366257f9e0d53b486edb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497708"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>Le partage de l’état de session avec Asp.Net StateServer nécessite que tous les serveurs de la batterie de serveurs web utilisent la même version du .NET Framework

#### <a name="details"></a>Détails

Lors de l’activation de l’état de session <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>, tous les serveurs dans la batterie de serveurs web donnée doivent utiliser la même version du .NET Framework pour que l’état soit correctement partagé.

#### <a name="suggestion"></a>Suggestion

Veillez à mettre à niveau les versions du .NET Framework sur les serveurs web qui partagent l’état en même temps.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->
