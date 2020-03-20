---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887766"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Les appels à System.Windows.Input.PenContext.Disable sur des systèmes tactiles peuvent lever une exception ArgumentException

|   |   |
|---|---|
|Détails|Dans certaines circonstances, les appels à la méthode **System.Windows.Intput.PenContext.Disable** interne sur des systèmes tactiles peuvent lever une exception <code>T:System.ArgumentException</code> non gérée en raison de la réentrance.|
|Suggestion|Ce problème a été résolu dans le .NET Framework 4.7. Pour éviter cette exception, effectuez une mise à niveau avec une version du .NET Framework supérieure ou égale à 4.7.|
|Étendue|Edge|
|Version|4.6.1|
|Type|Reciblage|
