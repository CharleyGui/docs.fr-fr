---
ms.openlocfilehash: 346fb6ecd43f7f93529e45f169c79b7acacc9c1f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497360"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Rupture d’adhésion pour rétrograder de la génération 4.5 de SQL à la génération 4.0 de SQL plus simple

#### <a name="details"></a>Détails

Les requêtes, qui produisent des instructions JOIN et contiennent un appel à une opération de limitation sans préalablement utiliser OrderBy, produisent à présent un langage SQL plus simple. Après la mise à niveau vers .NET Framework 4.5, ces requêtes produisaient un langage SQL plus compliqué que les versions antérieures.

#### <a name="suggestion"></a>Suggestion

Cette fonctionnalité est désactivée par défaut. Si Entity Framework génère des instructions JOIN supplémentaires qui entraînent une dégradation des performances, vous pouvez activer cette fonctionnalité en ajoutant l’entrée suivante à la section <code>&lt;appSettings&gt;</code> du fichier de configuration de l’application (app.config) :<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Mode transparent|
|Version|4.5.2|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
