---
title: Installer des fichiers IntelliSense localisés
description: Découvrez comment configurer votre machine de développement pour utiliser des fichiers IntelliSense localisés pour des projets .NET Core dans Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157711"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a>Comment installer des fichiers IntelliSense localisés pour .NET Core

[IntelliSense](/visualstudio/ide/using-intellisense) est une aide à l’achèvement du code qui est disponible dans différents environnements de développement intégrés (IDE), tels que Visual Studio. Par défaut, lorsque vous développez des projets .NET Core, le SDK ne comprend que la version anglaise des fichiers IntelliSense. Cet article explique :

- Comment installer la version localisée de ces fichiers.
- Comment modifier l’installation Visual Studio pour utiliser une langue différente.

## <a name="prerequisites"></a>Conditions préalables requises

- [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) ou une version ultérieure.
- [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou une version ultérieure.

## <a name="download-and-install-the-localized-intellisense-files"></a>Télécharger et installer les fichiers IntelliSense localisés

> [!IMPORTANT]
> Cette procédure exige que vous ayez la permission de l’administrateur de copier les fichiers IntelliSense au dossier d’installation .NET Core.

1. Rendez-vous sur la page [télécharger les fichiers IntelliSense.](https://dotnet.microsoft.com/download/dotnet-core/intellisense)

1. Téléchargez le fichier IntelliSense pour la langue et la version que vous souhaitez utiliser.

1. Extraire le contenu du fichier zip.

1. Naviguez vers le dossier Intellisense .NET Core.

   1. Naviguez vers le dossier d’installation .NET Core. Par défaut, il est inférieur *à %ProgramFiles%-dotnet packs*.
   1. Choisissez le SDK pour lequel vous souhaitez installer l’IntelliSense et naviguez vers le chemin associé. Vous disposez des options suivantes :

      | Type de kit de développement logiciel (SDK)        | Path                               |
      | --------------- | ---------------------------------- |
      | .NET Core       | *Microsoft.NETCore.App.Ref (en anglais seulement)*        |
      | Windows Desktop | *Microsoft.WindowsDesktop.App.Ref (en)* |
      | .NET Standard   | *NETStandard.Library.Ref NETStandard.Library.Ref NETStandard.Library.Ref NETStand*          |

   1. Naviguez vers la version pour laquelle vous souhaitez installer l’IntelliSense localisé. Par exemple, *3.1.0*.
   1. Ouvrez le dossier *d’arbitre.*
   1. Ouvrez le dossier de surnom. Par exemple, *netcoreapp3.1*.

   Ainsi, le chemin complet que vous navigueriez à ressembler à *C: 'Program Files’dotnet’packs-Microsoft.NETCore.App.Ref'3.1.0'ref’netcoreapp3.1*.

1. Créez un sous-pliage à l’intérieur du dossier de surnom que vous venez d’ouvrir. Le nom du dossier indique la langue que vous souhaitez utiliser. Le tableau suivant précise les différentes options :

   | Langage              | Nom du dossier |
   | --------------------- | ----------- |
   | Portugais brésilien  | *pt-br*     |
   | Chinois (simplifié)  | *zh-hans*   |
   | Chinois (traditionnel) | *zh-hant*   |
   | Français                | *Fr*        |
   | Allemand                | *de*        |
   | Italien               | *Il*        |
   | Japonais              | *ja*        |
   | Coréen                | *ko (en)*        |
   | Russe               | *Ru*        |
   | Espagnol               | *es es*        |

1. Copiez les fichiers *.xml* que vous avez extraits sur l’étape 3 à ce nouveau dossier. Les fichiers *.xml* sont décomposés par les dossiers SDK, alors copiez-les sur le SDK correspondant que vous avez choisi sur l’étape 4.

## <a name="modify-visual-studio-language"></a>Modifier le langage Visual Studio

Pour Visual Studio d’utiliser une langue différente pour IntelliSense, installez le pack de langue approprié. Cela peut être fait lors de [l’installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) ou à une date ultérieure en modifiant l’installation Visual Studio. Si vous avez déjà Visual Studio configuré dans la langue de votre choix, votre installation IntelliSense est prête.

### <a name="install-the-language-pack"></a>Installer le pack de langue

Si vous n’avez pas installé le pack de langue désiré pendant la configuration, mettez à jour Visual Studio comme suit pour installer le pack de langue :

> [!IMPORTANT]
> Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui a la permission de l’administrateur. Pour plus d’informations, voir [les autorisations des utilisateurs et Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).

1. Recherchez le programme d’installation de Visual Studio sur votre ordinateur.

   Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.

   ![Ouvrez l’installateur visual studio à partir de Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > Vous trouverez également Visual Studio Installer à l’emplacement suivant :
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   Vous devrez peut-être mettre à jour le programme d’installation avant de continuer. Dans ce cas, suivez les invites.

1. Dans l’installateur, recherchez l’édition de Visual Studio à laquelle vous souhaitez ajouter le pack de langue, puis choisissez **Modifier**.

   ![Mettre à jour ou modifier Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > Si vous ne voyez pas de bouton **Modifier** mais que vous en voyez une **mise à jour** à la place, vous devez mettre à jour votre studio visuel avant de pouvoir modifier votre installation.
   > Une fois la mise à jour terminée, le bouton **Modifier** doit s’apparaître.

1. Dans **l’onglet Packs langue,** sélectionnez ou désélectionner les langues que vous souhaitez installer ou désinstaller.

   ![Visuel Studio langue packs onglet](./media/localized-intellisense/vs-modify-language-packs.png)

1. Choisissez **Modifier**. La mise à jour démarre.

### <a name="modify-language-settings-in-visual-studio"></a>Modifier les paramètres linguistiques dans Visual Studio

Une fois que vous avez installé les packs de langage souhaités, modifiez vos paramètres Visual Studio pour utiliser une langue différente :

1. Ouvrez Visual Studio.

1. Dans la fenêtre de démarrage, choisissez **Continuer sans code**.

1. Sur la barre de menu, sélectionnez **Options Outils** > **.** Le dialogue Options s’ouvre.

1. Sous le nœud **Environnement,** choisissez **paramètres internationaux**.

1. Sur le **décrochage linguistique,** sélectionnez la langue désirée. Choisissez **OK**.

1. Un dialogue vous informe que vous devez redémarrer Visual Studio pour que les modifications prennent effet. Choisissez **OK**.

1. Redémarrez Visual Studio.

Après cela, votre IntelliSense devrait fonctionner comme prévu lorsque vous ouvrez un projet .NET Core qui cible la version des fichiers IntelliSense que vous venez d’installer.

## <a name="see-also"></a>Voir aussi

- [IntelliSense dans Visual Studio](/visualstudio/ide/using-intellisense)
