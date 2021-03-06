---
title: Installer des fichiers IntelliSense localisés
description: Découvrez comment configurer votre ordinateur de développement pour utiliser des fichiers IntelliSense localisés pour des projets .NET 5 + (y compris .NET Core) dans Visual Studio.
ms.date: 11/06/2020
ms.openlocfilehash: 45eeae12ca79179cacb3d48fca28118de70e0a4f
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506764"
---
# <a name="how-to-install-localized-intellisense-files-for-net"></a>Comment installer des fichiers IntelliSense localisés pour .NET

[IntelliSense](/visualstudio/ide/using-intellisense) est une aide à la saisie semi-automatique de code qui est disponible dans différents environnements de développement intégré (IDE), tels que Visual Studio. Par défaut, lorsque vous développez des projets .NET, le kit de développement logiciel (SDK) comprend uniquement la version anglaise des fichiers IntelliSense. Cet article explique les éléments suivants :

- Comment installer la version localisée de ces fichiers.
- Comment modifier l’installation de Visual Studio pour utiliser une autre langue.

## <a name="prerequisites"></a>Prérequis

- [.Net Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) ou une version ultérieure, comme le [Kit de développement logiciel (SDK) .net 5](https://dotnet.microsoft.com/download/dotnet/5.0).
- [Visual Studio 2019 version 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou une version ultérieure.

## <a name="download-and-install-the-localized-intellisense-files"></a>Télécharger et installer les fichiers IntelliSense localisés

> [!IMPORTANT]
> Cette procédure nécessite que vous disposiez de l’autorisation d’administrateur pour copier les fichiers IntelliSense dans le dossier d’installation de .NET.

1. Accédez à la page [Télécharger les fichiers IntelliSense](https://dotnet.microsoft.com/download/intellisense) .

1. Téléchargez le fichier IntelliSense correspondant à la langue et à la version que vous souhaitez utiliser.

1. Extrayez le contenu du fichier zip.

1. Accédez au dossier .NET IntelliSense.

   1. Accédez au dossier d’installation de .NET. Par défaut, il se trouve sous *%ProgramFiles%\dotnet\packs*.
   1. Choisissez le kit de développement logiciel (SDK) pour lequel vous souhaitez installer IntelliSense et accédez au chemin d’accès associé. Les options suivantes s’offrent à vous :

      | Type de kit de développement logiciel (SDK)              | Path                               |
      |-----------------------|------------------------------------|
      | .NET 5 + et .NET Core | *Microsoft. Netcore. app. Ref*        |
      | Bureau Windows       | *Microsoft. WindowsDesktop. app. Ref* |
      | .NET Standard         | *Netstandard. Library. Ref*          |

   1. Accédez à la version pour laquelle vous souhaitez installer la fonctionnalité IntelliSense localisée. Par exemple, *5.0.0*.
   1. Ouvrez le dossier *ref* .
   1. Ouvrez le dossier moniker. Par exemple, *net 5.0*.

   Par conséquent, le chemin d’accès complet que vous recherchez devrait ressembler à *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\5.0.0\ref\net5.0*.

1. Créez un sous-dossier à l’intérieur du dossier moniker que vous venez d’ouvrir. Le nom du dossier indique la langue que vous souhaitez utiliser. Le tableau suivant spécifie les différentes options :

   | Langage              | Nom de dossier |
   | --------------------- | ----------- |
   | Portugais brésilien  | *PT-BR*     |
   | Chinois (simplifié)  | *zh-Hans*   |
   | Chinois (traditionnel) | *zh-Hant*   |
   | Français                | *fr*        |
   | Allemand                | *de*        |
   | Italien               | *it*        |
   | Japonais              | *ja*        |
   | Coréen                | *ko*        |
   | Russe               | *ru*        |
   | Espagnol               | *es*        |

1. Copiez les fichiers *. xml* que vous avez extraits à l’étape 3 dans ce nouveau dossier. Les fichiers *. xml* sont décomposés par dossiers SDK. par conséquent, copiez-les dans le kit de développement logiciel (SDK) correspondant que vous avez choisi à l’étape 4.

## <a name="modify-visual-studio-language"></a>Modifier le langage de Visual Studio

Pour que Visual Studio utilise une langue différente pour IntelliSense, installez le module linguistique approprié. Vous pouvez effectuer cette opération [pendant l’installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) ou ultérieurement en modifiant l’installation de Visual Studio. Si vous avez déjà configuré Visual Studio dans le langage de votre choix, votre installation IntelliSense est prête.

### <a name="install-the-language-pack"></a>Installer le module linguistique

Si vous n’avez pas installé le module linguistique souhaité au cours de l’installation, mettez à jour Visual Studio comme suit pour installer le module linguistique :

> [!IMPORTANT]
> Pour installer, mettre à jour ou modifier Visual Studio, vous devez ouvrir une session avec un compte disposant de l’autorisation administrateur. Pour plus d’informations, consultez [autorisations utilisateur et Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

   Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer** , puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

   ![Ouvrir le Visual Studio Installer à partir de Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > Vous trouverez également Visual Studio Installer à l’emplacement suivant :
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans le programme d’installation, recherchez l’édition de Visual Studio à laquelle vous souhaitez ajouter le module linguistique, puis choisissez **modifier**.

   ![Mettre à jour ou modifier Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > Si vous ne voyez pas de bouton **modifier** mais que vous voyez une **mise à jour** , vous devez mettre à jour votre Visual Studio avant de pouvoir modifier votre installation.
   > Une fois la mise à jour terminée, le bouton **modifier** doit s’afficher.

1. Sous l’onglet **modules linguistiques** , sélectionnez ou désélectionnez les langues que vous voulez installer ou désinstaller.

   ![Onglet modules linguistiques de Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. Choisissez **Modifier**. La mise à jour démarre.

### <a name="modify-language-settings-in-visual-studio"></a>Modifier les paramètres de langue dans Visual Studio

Une fois que vous avez installé les modules linguistiques souhaités, modifiez les paramètres de Visual Studio pour utiliser une autre langue :

1. Ouvrez Visual Studio.

1. Dans la fenêtre de démarrage, choisissez **Continuer sans code**.

1. Dans la barre de menus, sélectionnez **Outils** > **Options**. La boîte de dialogue Options s’ouvre.

1. Sous le nœud **environnement** , choisissez **paramètres internationaux**.

1. Dans la liste déroulante **langue** , sélectionnez la langue de votre choix. Choisissez **OK**.

1. Une boîte de dialogue vous informe que vous devez redémarrer Visual Studio pour que les modifications prennent effet. Choisissez **OK**.

1. Démarrez Visual Studio.

Après cela, votre IntelliSense doit fonctionner comme prévu lorsque vous ouvrez un projet .NET qui cible la version des fichiers IntelliSense que vous venez d’installer.

## <a name="see-also"></a>Voir aussi

- [IntelliSense dans Visual Studio](/visualstudio/ide/using-intellisense)
