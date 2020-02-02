---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920658"
---

<span data-ttu-id="8ba44-101">Lors de l’installation du package .NET Core, une erreur semblable à `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`peut s’afficher.</span><span class="sxs-lookup"><span data-stu-id="8ba44-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="8ba44-102">En règle générale, cette erreur signifie que le flux de package pour .NET Core est mis à niveau avec des versions de package plus récentes, et que vous devez réessayer ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="8ba44-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="8ba44-103">Pendant une mise à niveau, le flux de package ne doit pas être disponible pendant plus de 30 minutes.</span><span class="sxs-lookup"><span data-stu-id="8ba44-103">During an upgrade, the package feed should not be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="8ba44-104">Si vous recevez continuellement cette erreur pendant plus de 30 minutes, veuillez envoyer un problème à <https://github.com/dotnet/core/issues>.</span><span class="sxs-lookup"><span data-stu-id="8ba44-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
