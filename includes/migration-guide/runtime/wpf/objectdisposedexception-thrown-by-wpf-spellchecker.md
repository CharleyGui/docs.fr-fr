---
ms.openlocfilehash: 9d09f598538b9d5ee3f995d6281b8eb4b2668050
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802559"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException levée par le vérificateur orthographique de WPF

|   |   |
|---|---|
|Détails|Les applications WPF plantent parfois lors de l’arrêt de l’application avec une <xref:System.ObjectDisposedException?displayProperty=name> levée par le vérificateur orthographique. Ce problème est résolu dans .NET Framework 4.7 WPF via une gestion différente de l’exception, qui permet aux applications de ne plus en être affectée de cette façon. Notez que des exceptions occasionnelles continuent d’être observées dans les applications s’exécutant sous un débogueur.|
|Suggestion|Mettre à niveau vers .NET Framework 4.7|
|Portée|Microsoft Edge|
|Version|4.6.1|
|Type|Runtime|

