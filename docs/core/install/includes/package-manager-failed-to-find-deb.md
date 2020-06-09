---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602984"
---

Si vous recevez un message d’erreur semblable à **incapable de localiser le package {Netcore-package}**, exécutez les commandes suivantes.

L’ensemble de commandes suivant contient deux espaces réservés.

- `{dotnet-package}`\
Cela représente le package .NET Core que vous installez, par exemple `aspnetcore-runtime-3.1` . Cela est utilisé dans la `sudo apt-get install` commande ci-dessous.

- `{os-version}`\
Cela représente la version Linux sur laquelle vous vous trouvez. Cela est utilisé dans la `wget` commande ci-dessous.

Essayez de purger la liste des packages :

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes :
