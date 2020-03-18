---
title: Consommer une bibliothèque .NET Standard dans Visual Studio
description: Construire une application .NET Core qui appelle les membres d’une autre bibliothèque de classe avec Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920457"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>Consommer une bibliothèque .NET Standard dans Visual Studio

Une fois que vous avez créé une bibliothèque de classe .NET Standard, testé et construit une version de sortie de la bibliothèque, l’étape suivante est de la rendre disponible pour les appelants. Il existe deux méthodes pour le faire :

- Si la bibliothèque doit être utilisée par une seule solution (par exemple s’il s’agit d’un composant dans une seule application de grande taille), vous pouvez l’inclure en tant que projet dans votre solution.
- Si la bibliothèque est accessible au public, vous pouvez la distribuer sous forme de forfait NuGet.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Ajoutez une application console à votre solution qui fait référence à un projet de bibliothèque .NET Standard.
> - Créez un forfait NuGet qui contient un projet de bibliothèque .NET Standard.

## <a name="add-a-console-app-to-your-solution"></a>Ajoutez une application console à votre solution

Tout comme vous avez inclus des tests unitaires dans la même solution que votre bibliothèque de classe dans [Test une bibliothèque .NET Standard dans Visual Studio](testing-library-with-visual-studio.md), vous pouvez inclure votre application dans le cadre de cette solution. Par exemple, vous pouvez utiliser votre bibliothèque de classes dans une application console qui invite l’utilisateur à entrer une chaîne et indique si son premier caractère est une majuscule :

1. Ouvrez `ClassLibraryProjects` la solution que vous avez créée dans l’article [Build a .NET Standard dans l’article Visual Studio.](library-with-visual-studio.md)

1. Ajoutez une nouvelle application de console .NET Core nommée "ShowCase" à la solution.

   1. Cliquez à droite sur la solution dans **Solution Explorer** et sélectionnez **Ajouter** > **un nouveau projet**.

   1. Sur la page **Ajouter un nouveau projet,** entrez **la console** dans la boîte de recherche. Choisissez **C ou** Visual **Basic** dans la liste de langue, puis choisissez toutes **les plates-formes** de la liste de la plate-forme. Choisissez le modèle **Console App (.NET Core),** puis choisissez **Next**.

   1. Sur la configuration de votre nouvelle page **de projet,** entrez **ShowCase** dans la boîte de nom du **projet.** Ensuite, choisissez **Créer**.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ShowCase**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.

   ![Menu context du projet Visual Studio pour définir un projet de démarrage](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Initialement, votre projet n’a pas accès à votre bibliothèque de classes. Pour lui permettre d’appeler des méthodes dans votre bibliothèque de classes, vous créez une référence à la bibliothèque de classes. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet `ShowCase` et sélectionnez **Ajouter une référence**.

   ![Ajouter un menu contextuelle de référence dans Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. Dans la boîte de dialogue **Gestionnaire de références**, sélectionnez **StringLibrary**, votre projet de bibliothèque de classe, puis sélectionnez le bouton **OK**.

   ![Dialogue de gestionnaire de référence avec StringLibrary sélectionné](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. Dans la fenêtre de code pour le *fichier Program.cs* ou *Program.vb,* remplacez tout le code par le code suivant :

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console. Chaque fois qu’il est supérieur ou égal à 25, le code efface la fenêtre de la console et affiche un message à l’utilisateur.

   Le programme invite l’utilisateur à entrer une chaîne. Il indique si la chaîne commence par une majuscule. Si l’utilisateur appuie sur la touche Enter sans entrer une chaîne, l’application se termine et la fenêtre de la console se ferme.

1. Si nécessaire, changez la barre d’outils pour compiler la version **Debug** du projet `ShowCase`. Compilez et exécutez le programme en sélectionnant la flèche verte sur le bouton **ShowCase**.

   ![Barre d’outils de projet de studio visuel affichant le bouton Debug](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

Vous pouvez déboiffer et publier l’application qui utilise cette bibliothèque en suivant les étapes de [Debug votre C ou Visual Basic .NET Core Hello World application en utilisant Visual Studio](debugging-with-visual-studio.md) et [Publiez votre application .NET Core Hello World avec Visual Studio](publishing-with-visual-studio.md).

## <a name="create-a-nuget-package"></a>Créer un package NuGet

Vous pouvez rendre votre bibliothèque de classes disponible à grande échelle en la publiant sous forme de package NuGet. Visual Studio ne prend pas en charge la création de forfaits NuGet. Pour en créer un, vous devez utiliser les commandes CLI de base .NET :

1. Ouvrez une fenêtre de console.

   Par exemple, entrez **l’invite de commande** dans la boîte de recherche sur la barre de tâche Windows. Sélectionnez l’application de bureau **Command Prompt** ou appuyez **sur Enter** si elle est déjà sélectionnée dans les résultats de recherche.

1. Accédez au répertoire de votre projet de bibliothèque. L’annuaire contient votre code source et un fichier de projet, *StringLibrary.csproj* ou *StringLibrary.vbproj*.

1. Exécutez la commande [de pack dotnet](../tools/dotnet-pack.md) pour générer un paquet avec une extension *de .nupkg* :

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > Si le répertoire contenant *dotnet.exe* ne se trouve pas dans votre chemin, vous pouvez trouver son emplacement en entrant `where dotnet.exe` dans la fenêtre de console.

Pour plus d’informations sur la création de paquets NuGet, voir [comment créer un package NuGet avec le CLI Core .NET](../deploying/creating-nuget-packages.md).
