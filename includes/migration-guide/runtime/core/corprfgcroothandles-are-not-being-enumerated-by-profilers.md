---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858574"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>Les membres COR_PRF_GC_ROOT_HANDLE ne sont pas énumérés par les profileurs

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.5.1, l’API de profilage <code>RootReferences2()</code> ne retourne jamais correctement <code>COR_PRF_GC_ROOT_HANDLE</code> (ils sont retournés comme <code>COR_PRF_GC_ROOT_OTHER</code> à la place). Ce problème est résolu depuis .NET Framework 4.6.|
|Suggestion|Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.|
|Étendue|Secondaire|
|Version|4.5.1|
|Type|Runtime|
