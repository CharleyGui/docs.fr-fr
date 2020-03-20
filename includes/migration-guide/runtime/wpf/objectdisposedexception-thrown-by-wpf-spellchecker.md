---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802559"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException levée par le vérificateur orthographique de WPF

|   |   |
|---|---|
|Détails|Les applications WPF plantent parfois lors de l’arrêt de l’application avec une <xref:System.ObjectDisposedException?displayProperty=name> levée par le vérificateur orthographique. Ce problème est résolu dans .NET Framework 4.7 WPF via une gestion différente de l’exception, qui permet aux applications de ne plus en être affectée de cette façon. Notez que des exceptions occasionnelles continuent d’être observées dans les applications s’exécutant sous un débogueur.|
|Suggestion|Mettre à niveau vers .NET Framework 4.7|
|Étendue|Edge|
|Version|4.6.1|
|Type|Runtime|
