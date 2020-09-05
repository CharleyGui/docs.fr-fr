---
ms.openlocfilehash: 3244913e06a744dafc4440f824ebe6bed25b8dd1
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496485"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException levée par le vérificateur orthographique de WPF

#### <a name="details"></a>Détails

Les applications WPF plantent parfois lors de l’arrêt de l’application avec une <xref:System.ObjectDisposedException?displayProperty=fullName> levée par le vérificateur orthographique. Ce problème est résolu dans .NET Framework 4.7 WPF via une gestion différente de l’exception, qui permet aux applications de ne plus en être affectée de cette façon. Notez que des exceptions occasionnelles continuent d’être observées dans les applications s’exécutant sous un débogueur.

#### <a name="suggestion"></a>Suggestion

Mettre à niveau vers .NET Framework 4.7

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
