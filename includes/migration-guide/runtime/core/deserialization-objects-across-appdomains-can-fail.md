---
ms.openlocfilehash: 3f82a4daac3b5d8981532f0c82e9a76f13c68b6e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497258"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>La désérialisation d’objets entre les domaines d’application peut échouer

#### <a name="details"></a>Détails

Dans certains cas, quand une application utilise deux domaines d'application ou plus avec des bases d'application différentes, une tentative de désérialisation des objets dans le contexte d'appel logique entre les domaines d'application lève une exception.

#### <a name="suggestion"></a>Suggestion

Consultez [Atténuation : désérialisation des objets entre les domaines d’application](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.5.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
