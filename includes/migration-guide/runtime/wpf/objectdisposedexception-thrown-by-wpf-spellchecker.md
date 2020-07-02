---
ms.openlocfilehash: b836b26f3f52e9d0cc78feb764629bd2fa306657
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621791"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException levée par le vérificateur orthographique de WPF

#### <a name="details"></a>Détails

Les applications WPF plantent parfois lors de l’arrêt de l’application avec une <xref:System.ObjectDisposedException?displayProperty=fullName> levée par le vérificateur orthographique. Ce problème est résolu dans .NET Framework 4.7 WPF via une gestion différente de l’exception, qui permet aux applications de ne plus en être affectée de cette façon. Notez que des exceptions occasionnelles continuent d’être observées dans les applications s’exécutant sous un débogueur.

#### <a name="suggestion"></a>Suggestion

Mettre à niveau vers .NET Framework 4.7

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6.1|
|Type|Runtime|
