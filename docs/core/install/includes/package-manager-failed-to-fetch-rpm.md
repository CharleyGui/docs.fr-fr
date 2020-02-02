---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920738"
---

<span data-ttu-id="f6d95-101">Lors de l’installation du package .NET Core, une erreur semblable à `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`peut s’afficher.</span><span class="sxs-lookup"><span data-stu-id="f6d95-101">While installing the .NET Core package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="f6d95-102">En règle générale, cette erreur signifie que le flux de package pour .NET Core est mis à niveau avec des versions de package plus récentes, et que vous devez réessayer ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="f6d95-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="f6d95-103">Pendant une mise à niveau, le flux de package ne doit pas être disponible pendant plus de 2 heures.</span><span class="sxs-lookup"><span data-stu-id="f6d95-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="f6d95-104">Si vous recevez continuellement cette erreur pendant plus de 2 heures, veuillez envoyer un problème à <https://github.com/dotnet/core/issues>.</span><span class="sxs-lookup"><span data-stu-id="f6d95-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
