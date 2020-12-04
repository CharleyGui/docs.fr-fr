---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "96588575"
---
<span data-ttu-id="75ebb-101">[À l’aide d’un client SFTP](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md), copiez les fichiers de l’emplacement de publication sur l’ordinateur de développement vers un nouveau dossier sur le Raspberry pi.</span><span class="sxs-lookup"><span data-stu-id="75ebb-101">[Using an SFTP client](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md), copy the files from the publish location on the development computer to a new folder on the Raspberry Pi.</span></span>

<span data-ttu-id="75ebb-102">Par exemple, pour utiliser la `scp` commande pour copier des fichiers de l’ordinateur de développement vers votre Raspberry pi, ouvrez une invite de commandes et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="75ebb-102">For example, to use the `scp` command to copy files from the development computer to your Raspberry Pi, open a command prompt and execute the following:</span></span>

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

<span data-ttu-id="75ebb-103">Où :</span><span class="sxs-lookup"><span data-stu-id="75ebb-103">Where:</span></span>

- <span data-ttu-id="75ebb-104">L' `-r` option indique `scp` de copier les fichiers de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="75ebb-104">The `-r` option instructs `scp` to copy files recursively.</span></span>
- <span data-ttu-id="75ebb-105">*/Publish-location/* est le dossier que vous avez publié à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="75ebb-105">*/publish-location/* is the folder you published to in the previous step.</span></span>
- <span data-ttu-id="75ebb-106">`pi@raspberypi` est l’utilisateur et les noms d’hôte au format `<username>@<hostname>` .</span><span class="sxs-lookup"><span data-stu-id="75ebb-106">`pi@raspberypi` is the user and host names in the format `<username>@<hostname>`.</span></span>
- <span data-ttu-id="75ebb-107">*/Home/pi/Deployment-location/* est le nouveau dossier sur le Raspberry pi.</span><span class="sxs-lookup"><span data-stu-id="75ebb-107">*/home/pi/deployment-location/* is the new folder on the Raspberry Pi.</span></span>

> [!TIP]
> <span data-ttu-id="75ebb-108">Les versions récentes de Windows possèdent OpenSSH, qui comprend `scp` , préinstallé.</span><span class="sxs-lookup"><span data-stu-id="75ebb-108">Recent versions of Windows have OpenSSH, which includes `scp`, pre-installed.</span></span>
