---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920738"
---

<span data-ttu-id="d9b2e-101">Lors de l’installation du paquet .NET Core, vous pouvez voir une erreur similaire à `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span><span class="sxs-lookup"><span data-stu-id="d9b2e-101">While installing the .NET Core package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="d9b2e-102">D’une manière générale, cette erreur signifie que le flux de paquet pour .NET Core est mis à niveau avec de nouvelles versions de paquet, et que vous devriez essayer à nouveau plus tard.</span><span class="sxs-lookup"><span data-stu-id="d9b2e-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="d9b2e-103">Pendant une mise à niveau, l’alimentation du paquet ne doit pas être indisponible pendant plus de 2 heures.</span><span class="sxs-lookup"><span data-stu-id="d9b2e-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="d9b2e-104">Si vous recevez continuellement cette erreur pendant plus de <https://github.com/dotnet/core/issues>2 heures, veuillez déposer un problème à .</span><span class="sxs-lookup"><span data-stu-id="d9b2e-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
