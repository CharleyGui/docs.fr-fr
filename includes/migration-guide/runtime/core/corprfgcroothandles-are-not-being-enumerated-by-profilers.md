---
ms.openlocfilehash: 25437dcc0c814ed2265b2efb34316af48b372ebd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496093"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>Les membres COR_PRF_GC_ROOT_HANDLE ne sont pas énumérés par les profileurs

#### <a name="details"></a>Détails

Dans .NET Framework 4.5.1, l’API de profilage <code>RootReferences2()</code> ne retourne jamais correctement <code>COR_PRF_GC_ROOT_HANDLE</code> (ils sont retournés comme <code>COR_PRF_GC_ROOT_OTHER</code> à la place). Ce problème est résolu depuis .NET Framework 4.6.

#### <a name="suggestion"></a>Suggestion

Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.5.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
