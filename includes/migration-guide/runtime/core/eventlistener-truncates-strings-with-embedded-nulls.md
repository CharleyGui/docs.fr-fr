---
ms.openlocfilehash: 6f5c1ecead4e2f74e621354058aab70bfa1cccb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619967"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>EventListener tronque les chaînes comportant des valeurs Null incorporées

#### <a name="details"></a>Détails

<xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> tronque les chaînes comportant des valeurs null incorporées. Les caractères Null ne sont pas pris en charge par la classe <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>. La modification affecte uniquement les applications qui utilisent <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> pour lire des données <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> dans le processus et qui utilisent des caractères Null comme délimiteurs.

#### <a name="suggestion"></a>Suggestion

Les données <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> doivent être, si possible, mises à jour pour ne pas utiliser les caractères Null incorporés.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.5.1|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Diagnostics.Tracing.EventListener.%23ctor></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|
