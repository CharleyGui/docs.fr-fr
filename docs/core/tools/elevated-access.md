---
title: Accès de niveau élevé pour les commandes dotnet
description: Découvrez les bonnes pratiques concernant les commandes dotnet qui nécessitent un accès de niveau élevé.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 4aff9badfa8ad9b83adc4496d4ebd6df29252e36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156762"
---
# <a name="elevated-access-for-dotnet-commands"></a>Accès de niveau élevé pour les commandes dotnet

Les bonnes pratiques guident les développeurs dans l’écriture de logiciels qui nécessitent des privilèges peu élevés. Toutefois, certains logiciels, comme les outils de supervision des performances, nécessitent des autorisations d’administrateur en raison de règles liées au système d’exploitation. Le guide qui suit décrit les scénarios pris en charge pour l’écriture de tels logiciels avec .NET Core.

Les commandes suivantes peuvent être exécutées avec des privilèges élevés :

- Commandes `dotnet tool`, comme [dotnet tool install](dotnet-tool-install.md).
- `dotnet run --no-build`

Il est déconseillé d’exécuter les autres commandes avec des privilèges élevés. Plus précisément, il est déconseillé d’utiliser des privilèges élevés avec les commandes qui utilisent MSBuild, telles que [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md) et [dotnet run](dotnet-run.md). Le problème le plus courant est celui qui est lié à la gestion des autorisations, lorsqu’un utilisateur passe régulièrement d’un compte racine à un compte restreint, après l’émission de commandes dotnet. Vous pouvez vous rendre compte, qu’en tant qu’utilisateur restreint, que vous ne pouvez pas accéder au fichier créé par un utilisateur racine. Il existe des moyens de résoudre ce problème, mais nous n’avons pas besoin de nous y intéresser tout de suite.

Vous pouvez exécuter des commandes avec un compte racine, du moment que vous ne passez constamment d’un compte racine à un compte restreint. Par exemple, les conteneurs Docker sont exécutés par défaut avec un compte racine. Ils ont donc cette caractéristique.

## <a name="global-tool-installation"></a>Installation de l’outil global

Les instructions suivantes montrent la méthode recommandée pour installer, exécuter et désinstaller les outils .NET Core dont l’exécution nécessite des autorisations élevées.

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

### <a name="install-the-tool"></a>Installer l’outil

Si le dossier `%ProgramFiles%\dotnet-tools` existe déjà, effectuez les étapes suivantes pour vérifier si le groupe « Utilisateurs » est autorisé à écrire ou à modifier ce répertoire :

- Cliquez à `%ProgramFiles%\dotnet-tools` droite sur le dossier et sélectionnez **les propriétés**. La boîte de dialogue **Propriétés communes** s’ouvre.
- Sélectionnez l’onglet **Sécurité.** Sous **nom de groupe ou d’utilisateur,** vérifiez si le groupe "Utilisateurs" a la permission d’écrire ou de modifier l’annuaire.
- Si le groupe « Utilisateurs » peut modifier le répertoire ou y écrire des données, utilisez un nom de répertoire autre que *dotnet-tools* lorsque vous installez les outils.

Pour installer les outils, exécutez la commande suivante dans l’invite de commandes avec élévation de privilèges. Cela va créer le dossier *dotnet-tools* pendant l’installation.

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Exécuter l’outil global

**Option 1** Utilisez le chemin complet dans l’invite de commandes avec élévation de privilèges :

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Option 2** Ajoutez le dossier que vous venez de créer dans `%Path%`. Cette opération n’est à exécuter qu’une seule fois.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

Puis exécutez avec :

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Désinstaller l’outil global

À l’invite de commandes avec privilèges élevés, tapez la commande suivante :

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[macOS](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Outils locaux

L’étendue des outils locaux se limite à l’arborescence des sous-répertoires et à l’utilisateur. Lorsqu’ils sont exécutés avec des privilèges élevés, les outils locaux partagent un environnement d’utilisateur restreint avec l’environnement à privilèges élevés. Sur Linux et macOS, seuls les utilisateurs racines peuvent accéder aux fichiers. Si l’utilisateur bascule vers un compte restreint, il ne peut plus accéder aux fichiers ni y écrire des données. Il n’est donc pas recommandé d’installer des outils qui nécessitent des privilèges élevés, comme les outils locaux. Utilisez plutôt l’option `--tool-path` et les instructions précédentes concernant les outils globaux.

## <a name="elevation-during-development"></a>Élévation des privilèges pendant le développement

Pendant le développement, vous aurez peut-être besoin de privilèges élevés pour tester votre application. Ce scénario est courant pour les applications IoT, par exemple. Nous recommandons de générer l’application sans privilèges élevés, puis de l’exécuter avec des privilèges élevés. Il existe quelques modèles, par exemple :

- Utilisation d’un fichier exécutable généré (fournit les meilleures performances de démarrage) :

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- Utilisation de la commande [dotnet run](dotnet-run.md) avec l’indicateur `—no-build` pour éviter de générer de nouveaux fichiers binaires :

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des outils globaux .NET Core](global-tools.md)
