---
ms.openlocfilehash: aba7b473af7685aa45f7e093a2f75311687593df
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506959"
---

Si vous recevez un message d’erreur semblable à **incapable de localiser le package {dotnet-package}** ou que **certains packages n’ont pas pu être installés** , exécutez les commandes suivantes.

L’ensemble de commandes suivant contient deux espaces réservés.

- `{dotnet-package}`\
Cela représente le package .NET que vous installez, par exemple `aspnetcore-runtime-3.1` . Ce code est utilisé dans la `sudo apt-get install` commande suivante.

- `{os-version}`\
Cela représente la version Linux sur laquelle vous vous trouvez. Cela est utilisé dans la `wget` commande ci-dessous.

Tout d’abord, essayez de purger la liste des packages :

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

Essayez ensuite d’installer à nouveau .NET. Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes :
