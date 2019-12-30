---
title: Installer des fichiers IntelliSense traduits
description: Découvrez comment configurer votre ordinateur de développement pour utiliser des fichiers IntelliSense traduits pour les projets .NET Core dans Visual Studio.
author: mairaw
ms.author: mairaw
ms.date: 12/18/2019
ms.openlocfilehash: 98d75544ab853e75c175dd2919991b250cfaa3b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443476"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a>Guide pratique pour installer des fichiers IntelliSense traduits pour .NET Core

[IntelliSense](/visualstudio/ide/using-intellisense) est une aide à la complétion de code qui est disponible dans différents environnements de développement intégrés (IDE) comme Visual Studio. Par défaut, lorsque vous développez des projets .NET Core, le kit SDK comprend uniquement la version anglaise des fichiers IntelliSense. Cet article explique :

- Comment installer la version traduite de ces fichiers.
- Comment modifier l’installation de Visual Studio pour utiliser une autre langue.

## <a name="prerequisites"></a>Prérequis

- [Kit SDK .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core) ou une version ultérieure.
- [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou une version ultérieure.

## <a name="download-and-install-the-localized-intellisense-files"></a>Télécharger et installer les fichiers IntelliSense traduits

> [!IMPORTANT]
> Cette procédure vous demande d’avoir l’autorisation Administrateur pour copier les fichiers IntelliSense dans le dossier d’installation de .NET Core.

1. Accédez à la page de [Téléchargement des fichiers IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense).

1. Téléchargez le fichier IntelliSense correspondant à la langue et à la version que vous souhaitez utiliser.

1. Extrayez le contenu du fichier .zip.

1. Accédez au dossier d’installation .NET Core. Par défaut, il se trouve sous *%ProgramFiles%\dotnet\packs*.

   - Choisissez le kit SDK pour lequel vous souhaitez installer IntelliSense et accédez au chemin associé. Les options suivantes sont disponibles :

      | Type de kit de développement logiciel (SDK)        | Chemin d’accès                               |
      | --------------- | ---------------------------------- |
      | .NET Core       | *Microsoft.NETCore.App.Ref*        |
      | Bureau Windows | *Microsoft.WindowsDesktop.App.Ref* |
      | .NET Standard   | *NETStandard.Library.Ref*          |
   
   - Accédez à la version pour laquelle vous souhaitez installer les fichiers IntelliSense traduits. Par exemple, *3.1.0*.
   - Ouvrez le dossier *ref*.
   - Ouvrez le dossier du moniker. Par exemple, *netcoreapp3.1*.

   Donc, le chemin complet auquel vous voulez accéder devrait ressembler à *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.

1. Créez un sous-dossier dans le dossier du moniker que vous venez d’ouvrir. Le nom du dossier indique la langue que vous souhaitez utiliser. Le tableau suivant spécifie les différentes options :

   | Langue              | Nom de dossier |
   | --------------------- | ----------- |
   | Portugais brésilien  | *pt-br*     |
   | Chinois (simplifié)  | *zh-hans*   |
   | Chinois (traditionnel) | *zh-hant*   |
   | Français                | *fr*        |
   | Allemand                | *de*        |
   | Italien               | *it*        |
   | Japonais              | *ja*        |
   | Coréen                | *ko*        |
   | Russe               | *ru*        |
   | Espagnol               | *es*        |

1. Copiez les fichiers *.xml* que vous avez extraits à l’étape 3 dans ce nouveau dossier. Étant donné que les fichiers *.xml* sont répartis dans les dossiers de SDK, copiez-les dans le kit SDK correspondant que vous avez choisi à l’étape 4.

## <a name="modify-visual-studio-language"></a>Modifier la langue de Visual Studio

Pour que Visual Studio utilise une autre langue pour IntelliSense, installez le module linguistique approprié. Vous pouvez effectuer cette opération [pendant l’installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) ou plus tard en modifiant l’installation de Visual Studio. Si vous avez déjà configuré Visual Studio dans la langue de votre choix, votre installation IntelliSense est prête.

### <a name="install-the-language-pack"></a>Installer le module linguistique

Si vous n’avez pas installé le module linguistique souhaité au cours de l’installation, mettez à jour Visual Studio comme suit pour installer le module linguistique :

> [!IMPORTANT]
> Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur. Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

   Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

   ![Ouvrir Visual Studio Installer à partir de Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > Vous trouverez également Visual Studio Installer à l’emplacement suivant :
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans le programme d’installation, recherchez l’édition de Visual Studio dans laquelle vous voulez ajouter le module linguistique, puis choisissez **Modifier**.

   ![Mettre à jour ou modifier Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > Si vous ne voyez pas de bouton **Modifier** mais que vous voyez un bouton **Mettre à jour** à la place, vous devez mettre à jour Visual Studio avant de pouvoir modifier votre installation.
   > Une fois la mise à jour terminée, le bouton **Modifier** doit apparaître.

1. Sous l’onglet **Modules linguistiques**, sélectionnez ou désélectionnez les langues à installer ou désinstaller.

   ![Onglet Modules linguistiques de Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. Choisissez **Modifier**. La mise à jour démarre.

### <a name="modify-language-settings-in-visual-studio"></a>Modifier les paramètres de langue dans Visual Studio

Une fois que vous avez installé les modules linguistiques souhaités, modifiez les paramètres de Visual Studio pour utiliser une autre langue :

1. Ouvrez Visual Studio.

1. Dans la fenêtre de démarrage, choisissez **Continuer sans code**.

1. Dans le menu principal, sélectionnez **Outils** > **Options**. La boîte de dialogue Options s’ouvre.

1. Sous le dossier **Environnement**, choisissez **Paramètres internationaux**.

1. Dans la liste déroulante **Langue**, sélectionnez la langue souhaitée. Cliquez sur **OK**. 

1. Une boîte de dialogue vous informe que vous devez redémarrer Visual Studio pour que les modifications prennent effet. Cliquez sur **OK**.

1. Redémarrez Visual Studio.

Après le redémarrage, IntelliSense doit fonctionner comme prévu quand vous ouvrez un projet .NET Core qui cible la version des fichiers IntelliSense que vous venez d’installer.

## <a name="see-also"></a>Voir aussi

- [IntelliSense dans Visual Studio](/visualstudio/ide/using-intellisense)
