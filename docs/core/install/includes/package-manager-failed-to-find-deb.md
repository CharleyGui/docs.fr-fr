---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602984"
---

<span data-ttu-id="804d1-101">Si vous recevez un message d’erreur semblable à **incapable de localiser le package {Netcore-package}**, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="804d1-101">If you receive an error message similar to **Unable to locate package {netcore-package}**, run the following commands.</span></span>

<span data-ttu-id="804d1-102">L’ensemble de commandes suivant contient deux espaces réservés.</span><span class="sxs-lookup"><span data-stu-id="804d1-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="804d1-103">Cela représente le package .NET Core que vous installez, par exemple `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="804d1-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="804d1-104">Cela est utilisé dans la `sudo apt-get install` commande ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="804d1-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="804d1-105">Cela représente la version Linux sur laquelle vous vous trouvez.</span><span class="sxs-lookup"><span data-stu-id="804d1-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="804d1-106">Cela est utilisé dans la `wget` commande ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="804d1-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="804d1-107">Essayez de purger la liste des packages :</span><span class="sxs-lookup"><span data-stu-id="804d1-107">Try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

<span data-ttu-id="804d1-108">Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="804d1-108">If that doesn't work, you can run a manual install with the following commands:</span></span>
