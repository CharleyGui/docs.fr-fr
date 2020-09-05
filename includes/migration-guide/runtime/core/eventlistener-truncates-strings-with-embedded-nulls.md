---
ms.openlocfilehash: e47a24239872e3fe86ff6902f66b38daaa106598
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497391"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>EventListener tronque les chaînes comportant des valeurs Null incorporées

#### <a name="details"></a>Détails

<xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> tronque les chaînes comportant des valeurs null incorporées. Les caractères Null ne sont pas pris en charge par la classe <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>. La modification affecte uniquement les applications qui utilisent <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> pour lire des données <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> dans le processus et qui utilisent des caractères Null comme délimiteurs.

#### <a name="suggestion"></a>Suggestion

Les données <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> doivent être, si possible, mises à jour pour ne pas utiliser les caractères Null incorporés.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.5.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.Tracing.EventListener.%23ctor>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Tracing.EventListener.#ctor`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})`

-->
