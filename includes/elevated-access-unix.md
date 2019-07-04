---
ms.openlocfilehash: dece035f443ff827a250ca1c1233b7651df7d108
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424710"
---
### <a name="install-the-global-tool"></a>Installer l’outil global

Les ressources de package doivent être installées dans un emplacement protégé à l’aide de l’option `--tool-path`. Cette séparation évite le partage d’un environnement d’utilisateur restreint avec un environnement à privilèges élevés.

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

`/usr/local/share/dotnet-tools` sera créé avec l’autorisation `drwxr-xr-x`. Si le répertoire existe déjà, utilisez la commande `ls -l` pour vérifier si l’utilisateur restreint est autorisé à modifier le répertoire. Dans ce cas, utilisez la commande `sudo chmod o-w -R /usr/share/dotnet-tools` pour retirer l’accès.

### <a name="run-the-global-tool"></a>Exécuter l’outil global

**Option 1** Utilisez le chemin complet avec sudo :

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

**Option 2** Ajoutez le lien de symbole de l’outil (une fois pour chaque outil) :

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

Puis exécutez avec :

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Désinstaller l’outil global

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

Si vous avez créé un lien de symbole, vous devez également le supprimer :

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```