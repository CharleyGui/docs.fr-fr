---
ms.openlocfilehash: fccf349517133245ec85ae3c25cedbfb27a7dd8b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496448"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>La méthode Replace est désactivée par défaut dans les URL OData

#### <a name="details"></a>Détails

À compter de la version 4.5 du .NET Framework, la méthode Replace des URL OData est désactivée par défaut. Quand la méthode Replace OData est désactivée (ce qui est désormais le cas par défaut), toutes les demandes utilisateur, y compris les fonctions de remplacement (qui sont rares) échouent.

#### <a name="suggestion"></a>Suggestion

Si la méthode Replace est nécessaire (ce qui est rare), elle peut être réactivée via les paramètres de configuration (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>). Toutefois, l’activation d’une méthode Replace peut créer des failles de sécurité et ne doit donc être utilisée qu’après un examen minutieux.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Data.Services.DataService%601?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``T:System.Data.Services.DataService`1``

-->
