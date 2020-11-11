---
ms.openlocfilehash: aba7b473af7685aa45f7e093a2f75311687593df
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506959"
---

<span data-ttu-id="df89f-101">Si vous recevez un message d’erreur semblable à **incapable de localiser le package {dotnet-package}** ou que **certains packages n’ont pas pu être installés** , exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="df89f-101">If you receive an error message similar to **Unable to locate package {dotnet-package}** or **Some packages could not be installed** , run the following commands.</span></span>

<span data-ttu-id="df89f-102">L’ensemble de commandes suivant contient deux espaces réservés.</span><span class="sxs-lookup"><span data-stu-id="df89f-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="df89f-103">Cela représente le package .NET que vous installez, par exemple `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="df89f-103">This represents the .NET package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="df89f-104">Ce code est utilisé dans la `sudo apt-get install` commande suivante.</span><span class="sxs-lookup"><span data-stu-id="df89f-104">This is used in the following `sudo apt-get install` command.</span></span>

- `{os-version}`\
<span data-ttu-id="df89f-105">Cela représente la version Linux sur laquelle vous vous trouvez.</span><span class="sxs-lookup"><span data-stu-id="df89f-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="df89f-106">Cela est utilisé dans la `wget` commande ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="df89f-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="df89f-107">Tout d’abord, essayez de purger la liste des packages :</span><span class="sxs-lookup"><span data-stu-id="df89f-107">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="df89f-108">Essayez ensuite d’installer à nouveau .NET.</span><span class="sxs-lookup"><span data-stu-id="df89f-108">Then, try to install .NET again.</span></span> <span data-ttu-id="df89f-109">Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="df89f-109">If that doesn't work, you can run a manual install with the following commands:</span></span>
