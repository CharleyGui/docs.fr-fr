---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132940"
---

<span data-ttu-id="e71d8-101">Si vous recevez un message d’erreur semblable à **incapable de localiser le package {Netcore-package}** ou que **certains packages n’ont pas pu être installés**, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="e71d8-101">If you receive an error message similar to **Unable to locate package {netcore-package}** or **Some packages could not be installed**, run the following commands.</span></span>

<span data-ttu-id="e71d8-102">L’ensemble de commandes suivant contient deux espaces réservés.</span><span class="sxs-lookup"><span data-stu-id="e71d8-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="e71d8-103">Cela représente le package .NET Core que vous installez, par exemple `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="e71d8-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="e71d8-104">Cela est utilisé dans la `sudo apt-get install` commande ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e71d8-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="e71d8-105">Cela représente la version Linux sur laquelle vous vous trouvez.</span><span class="sxs-lookup"><span data-stu-id="e71d8-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="e71d8-106">Cela est utilisé dans la `wget` commande ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e71d8-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="e71d8-107">Tout d’abord, essayez de purger la liste des packages :</span><span class="sxs-lookup"><span data-stu-id="e71d8-107">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="e71d8-108">Essayez ensuite d’installer à nouveau .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e71d8-108">Then, try to install .NET Core again.</span></span> <span data-ttu-id="e71d8-109">Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e71d8-109">If that doesn't work, you can run a manual install with the following commands:</span></span>
