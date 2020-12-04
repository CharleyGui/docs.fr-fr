---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "96588575"
---
[À l’aide d’un client SFTP](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md), copiez les fichiers de l’emplacement de publication sur l’ordinateur de développement vers un nouveau dossier sur le Raspberry pi.

Par exemple, pour utiliser la `scp` commande pour copier des fichiers de l’ordinateur de développement vers votre Raspberry pi, ouvrez une invite de commandes et exécutez la commande suivante :

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

Où :

- L' `-r` option indique `scp` de copier les fichiers de manière récursive.
- */Publish-location/* est le dossier que vous avez publié à l’étape précédente.
- `pi@raspberypi` est l’utilisateur et les noms d’hôte au format `<username>@<hostname>` .
- */Home/pi/Deployment-location/* est le nouveau dossier sur le Raspberry pi.

> [!TIP]
> Les versions récentes de Windows possèdent OpenSSH, qui comprend `scp` , préinstallé.
