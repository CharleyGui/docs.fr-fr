---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920658"
---

Lors de l’installation du paquet .NET Core, vous pouvez voir une erreur similaire à `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`. D’une manière générale, cette erreur signifie que le flux de paquet pour .NET Core est mis à niveau avec de nouvelles versions de paquet, et que vous devriez essayer à nouveau plus tard. Pendant une mise à niveau, l’alimentation du paquet ne doit pas être indisponible pendant plus de 30 minutes. Si vous recevez continuellement cette erreur pendant plus de 30 minutes, veuillez déposer un problème à <https://github.com/dotnet/core/issues>.
