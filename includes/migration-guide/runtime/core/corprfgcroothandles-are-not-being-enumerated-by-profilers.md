---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619956"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>Les membres COR_PRF_GC_ROOT_HANDLE ne sont pas énumérés par les profileurs

#### <a name="details"></a>Détails

Dans .NET Framework 4.5.1, l’API de profilage <code>RootReferences2()</code> ne retourne jamais correctement <code>COR_PRF_GC_ROOT_HANDLE</code> (ils sont retournés comme <code>COR_PRF_GC_ROOT_OTHER</code> à la place). Ce problème est résolu depuis .NET Framework 4.6.

#### <a name="suggestion"></a>Suggestion

Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.5.1|
|Type|Runtime|
