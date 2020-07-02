---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617530"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Les appels à System.Windows.Input.PenContext.Disable sur des systèmes tactiles peuvent lever une exception ArgumentException

#### <a name="details"></a>Détails

Dans certaines circonstances, les appels à la méthode **System.Windows.Intput.PenContext.Disable** interne sur des systèmes tactiles peuvent lever une exception `T:System.ArgumentException` non gérée en raison de la réentrance.

#### <a name="suggestion"></a>Suggestion

Ce problème a été résolu dans le .NET Framework 4.7. Pour éviter cette exception, effectuez une mise à niveau avec une version du .NET Framework supérieure ou égale à 4.7.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6.1       |
| Type    | Reciblage |
