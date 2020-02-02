---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920738"
---

Lors de l’installation du package .NET Core, une erreur semblable à `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`peut s’afficher. En règle générale, cette erreur signifie que le flux de package pour .NET Core est mis à niveau avec des versions de package plus récentes, et que vous devez réessayer ultérieurement. Pendant une mise à niveau, le flux de package ne doit pas être disponible pendant plus de 2 heures. Si vous recevez continuellement cette erreur pendant plus de 2 heures, veuillez envoyer un problème à <https://github.com/dotnet/core/issues>.
