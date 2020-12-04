---
title: Publier une application console .NET à l’aide de Visual Studio pour Mac
description: Découvrez comment utiliser Visual Studio pour Mac pour créer l’ensemble des fichiers nécessaires à l’exécution d’une application .NET.
ms.date: 11/30/2020
ms.openlocfilehash: 88f143011b19ca8eda6610803c894e619d06a635
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599182"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio-for-mac"></a>Didacticiel : publier une application console .NET à l’aide de Visual Studio pour Mac

Ce didacticiel montre comment publier une application console afin que d’autres utilisateurs puissent l’exécuter. La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application. Pour déployer les fichiers, copiez-les sur l’ordinateur cible.

## <a name="prerequisites"></a>Prérequis

- Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net à l’aide de Visual Studio pour Mac](with-visual-studio-mac.md).

## <a name="publish-the-app"></a>Publier l’application

1. Démarrez Visual Studio pour Mac.

1. Ouvrez le projet HelloWorld que vous avez créé dans [créer une application console .net à l’aide de Visual Studio pour Mac](with-visual-studio-mac.md).

1. Vérifiez que Visual Studio génère la version release de votre application. Si nécessaire, modifiez le paramètre de configuration de la génération dans la barre d’outils de **Debug** en **Release**.

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="Barre d’outils Visual Studio avec version Release sélectionnée":::

1. Dans le menu principal, choisissez **générer**  >  **publier dans un dossier...**.

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Menu contextuel Publier de Visual Studio":::

1. Dans la boîte de dialogue **publier dans un dossier** , sélectionnez **publier**.

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Boîte de dialogue publier dans un dossier de Visual Studio":::

   Le dossier publier s’ouvre et affiche les fichiers qui ont été créés.

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="dossier de publication":::

1. Sélectionnez l’icône d’engrenage, puis sélectionnez **copier « publier » comme chemin d’accès** dans le menu contextuel.

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="Copier le chemin vers le dossier de publication":::

## <a name="inspect-the-files"></a>Inspecter les fichiers

Le processus de publication crée un déploiement dépendant du Framework, qui est un type de déploiement dans lequel l’application publiée s’exécute sur un ordinateur sur lequel le Runtime .NET est installé. Les utilisateurs peuvent exécuter l’application publiée en exécutant la `dotnet HelloWorld.dll` commande à partir d’une invite de commandes.

Comme l’indique l’image précédente, la sortie publiée comprend les fichiers suivants :

* *HelloWorld.deps.json*

  Il s’agit du fichier de dépendances d’exécution de l’application. Il définit les composants .NET et les bibliothèques (y compris la bibliothèque de liens dynamiques qui contient votre application) nécessaires pour exécuter l’application. Pour plus d’informations, consultez [fichiers de configuration](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)de l’exécution.

* *HelloWorld.dll*

   Il s’agit de la version de [déploiement dépendante du Framework](../deploying/deploy-with-cli.md#framework-dependent-deployment) de l’application. Pour exécuter cette bibliothèque de liens dynamiques, entrez `dotnet HelloWorld.dll` à l’invite de commandes. Cette méthode d’exécution de l’application fonctionne sur toutes les plateformes sur lesquelles le Runtime .NET est installé.

* *HelloWorld.pdb* (facultatif pour le déploiement)

   Il s’agit du fichier de symboles de débogage. Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.

* *HelloWorld.runtimeconfig.json*

   Il s’agit du fichier de configuration au moment de l’exécution de l’application. Il identifie la version de .NET sur laquelle votre application a été conçue pour s’exécuter. Vous pouvez également y ajouter des options de configuration. Pour plus d’informations, consultez [paramètres de configuration du Runtime .net](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Exécuter l’application publiée

1. Ouvrez un terminal et accédez au dossier *Publish* . Pour ce faire, entrez, `cd` puis collez le chemin d’accès que vous avez copié précédemment. Par exemple :

   ```console
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/net5.0/publish/
   ```

1. Exécutez l’application à l’aide de la `dotnet` commande :

   1. Entrez `dotnet HelloWorld.dll` et appuyez sur <kbd>entrée</kbd>.

   1. Entrez un nom en réponse à l’invite, puis appuyez sur n’importe quelle touche pour quitter.

## <a name="additional-resources"></a>Ressources supplémentaires

- [déploiement d'applications .NET](../deploying/index.md)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez publié une application console. Dans le didacticiel suivant, vous allez créer une bibliothèque de classes.

> [!div class="nextstepaction"]
> [Créer une bibliothèque .NET à l’aide de Visual Studio pour Mac](library-with-visual-studio-mac.md)
