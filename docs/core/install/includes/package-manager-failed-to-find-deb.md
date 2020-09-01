---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132940"
---

Si vous recevez un message d’erreur semblable à **incapable de localiser le package {Netcore-package}** ou que **certains packages n’ont pas pu être installés**, exécutez les commandes suivantes.

L’ensemble de commandes suivant contient deux espaces réservés.

- `{dotnet-package}`\
Cela représente le package .NET Core que vous installez, par exemple `aspnetcore-runtime-3.1` . Cela est utilisé dans la `sudo apt-get install` commande ci-dessous.

- `{os-version}`\
Cela représente la version Linux sur laquelle vous vous trouvez. Cela est utilisé dans la `wget` commande ci-dessous.

Tout d’abord, essayez de purger la liste des packages :

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

Essayez ensuite d’installer à nouveau .NET Core. Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes :
