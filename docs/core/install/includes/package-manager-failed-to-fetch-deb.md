---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920658"
---

Lors de l’installation du package .NET Core, une erreur semblable à `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`peut s’afficher. En règle générale, cette erreur signifie que le flux de package pour .NET Core est mis à niveau avec des versions de package plus récentes, et que vous devez réessayer ultérieurement. Pendant une mise à niveau, le flux de package ne doit pas être disponible pendant plus de 30 minutes. Si vous recevez continuellement cette erreur pendant plus de 30 minutes, veuillez envoyer un problème à <https://github.com/dotnet/core/issues>.
