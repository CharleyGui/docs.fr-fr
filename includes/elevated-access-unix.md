---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67540101"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="a7d99-101">Installer l’outil global</span><span class="sxs-lookup"><span data-stu-id="a7d99-101">Install the global tool</span></span>

<span data-ttu-id="a7d99-102">Les ressources de package doivent être installées dans un emplacement protégé à l’aide de l’option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="a7d99-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="a7d99-103">Cette séparation évite le partage d’un environnement d’utilisateur restreint avec un environnement à privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="a7d99-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="a7d99-104">`/usr/local/share/dotnet-tools` sera créé avec l’autorisation `drwxr-xr-x`.</span><span class="sxs-lookup"><span data-stu-id="a7d99-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="a7d99-105">Si le répertoire existe déjà, utilisez la commande `ls -l` pour vérifier si l’utilisateur restreint est autorisé à modifier le répertoire.</span><span class="sxs-lookup"><span data-stu-id="a7d99-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="a7d99-106">Dans ce cas, utilisez la commande `sudo chmod o-w -R /usr/share/dotnet-tools` pour retirer l’accès.</span><span class="sxs-lookup"><span data-stu-id="a7d99-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="a7d99-107">Exécuter l’outil global</span><span class="sxs-lookup"><span data-stu-id="a7d99-107">Run the global tool</span></span>

<span data-ttu-id="a7d99-108">**Option 1** Utilisez le chemin complet avec sudo :</span><span class="sxs-lookup"><span data-stu-id="a7d99-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="a7d99-109">**Option 2** Ajoutez le lien de symbole de l’outil (une fois pour chaque outil) :</span><span class="sxs-lookup"><span data-stu-id="a7d99-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="a7d99-110">Puis exécutez avec :</span><span class="sxs-lookup"><span data-stu-id="a7d99-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="a7d99-111">Désinstaller l’outil global</span><span class="sxs-lookup"><span data-stu-id="a7d99-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="a7d99-112">Si vous avez créé un lien de symbole, vous devez également le supprimer :</span><span class="sxs-lookup"><span data-stu-id="a7d99-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
