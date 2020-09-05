---
ms.openlocfilehash: 6431f3b4d0983c44629e4fe760c75adcc277ddd4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496656"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>Certaines API .NET provoquent des exceptions EntryPointNotFoundExceptions de première chance (gérées)

#### <a name="details"></a>Détails

Dans .NET Framework 4.5, un petit nombre de méthodes .NET levaient des exceptions <xref:System.EntryPointNotFoundException?displayProperty=fullName> de première chance. Ces exceptions étaient gérées dans le .NET Framework, mais pouvaient arrêter l’automatisation des tests, car celle-ci ne s’attendait pas à des exceptions de première chance. Ces mêmes API provoquent l’arrêt de certaines exécutions ApiVerifier lorsque HighVersionLie est activé.

#### <a name="suggestion"></a>Suggestion

Vous pouvez éviter ce problème en effectuant une mise à niveau vers .NET Framework 4.5.1. Vous pouvez aussi mettre à jour le code d’automatisation des tests pour que son exécution ne soit pas arrêtée en cas d’exceptions <xref:System.EntryPointNotFoundException?displayProperty=fullName> de première chance.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)>

<!--

#### Affected APIs

- `M:System.Diagnostics.Debug.Assert(System.Boolean)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])`
- `M:System.Xml.Serialization.XmlSerializer.#ctor(System.Type)`

-->
