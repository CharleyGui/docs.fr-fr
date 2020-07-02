---
ms.openlocfilehash: 0fe07ac21effacffc56d37ccb46a121f443acd20
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619938"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>Le partage de l’état de session avec Asp.Net StateServer nécessite que tous les serveurs de la batterie de serveurs web utilisent la même version du .NET Framework

#### <a name="details"></a>Détails

Lors de l’activation de l’état de session <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>, tous les serveurs dans la batterie de serveurs web donnée doivent utiliser la même version du .NET Framework pour que l’état soit correctement partagé.

#### <a name="suggestion"></a>Suggestion

Veillez à mettre à niveau les versions du .NET Framework sur les serveurs web qui partagent l’état en même temps.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
