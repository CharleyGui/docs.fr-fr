---
ms.openlocfilehash: ed526095459a48aa37b585dfed79cc12b9fb9e56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622042"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>Certaines API .NET provoquent des exceptions EntryPointNotFoundExceptions de première chance (gérées)

#### <a name="details"></a>Détails

Dans .NET Framework 4.5, un petit nombre de méthodes .NET levaient des exceptions <xref:System.EntryPointNotFoundException?displayProperty=fullName> de première chance. Ces exceptions étaient gérées dans le .NET Framework, mais pouvaient arrêter l’automatisation des tests, car celle-ci ne s’attendait pas à des exceptions de première chance. Ces mêmes API provoquent l’arrêt de certaines exécutions ApiVerifier lorsque HighVersionLie est activé.

#### <a name="suggestion"></a>Suggestion

Vous pouvez éviter ce problème en effectuant une mise à niveau vers .NET Framework 4.5.1. Vous pouvez aussi mettre à jour le code d’automatisation des tests pour que son exécution ne soit pas arrêtée en cas d’exceptions <xref:System.EntryPointNotFoundException?displayProperty=fullName> de première chance.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)></li></ul>|
