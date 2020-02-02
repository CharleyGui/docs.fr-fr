---
title: Consommer une bibliothèque .NET Standard dans Visual Studio
description: Générez une application .NET Core qui appelle les membres d’une autre bibliothèque de classes avec Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920457"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>Consommer une bibliothèque .NET Standard dans Visual Studio

Une fois que vous avez créé une bibliothèque de classes .NET Standard, que vous l’avez testée et créé une version Release de la bibliothèque, l’étape suivante consiste à la rendre accessible aux appelants. Vous pouvez procéder de deux manières :

- Si la bibliothèque doit être utilisée par une seule solution (par exemple s’il s’agit d’un composant dans une seule application de grande taille), vous pouvez l’inclure en tant que projet dans votre solution.
- Si la bibliothèque est publiquement disponible, vous pouvez la distribuer en tant que package NuGet.

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
>
> - Ajoutez une application console à votre solution qui fait référence à un projet de bibliothèque .NET Standard.
> - Créez un package NuGet qui contient un projet de bibliothèque .NET Standard.

## <a name="add-a-console-app-to-your-solution"></a>Ajouter une application console à votre solution

Tout comme vous avez inclus des tests unitaires dans la même solution que votre bibliothèque de classes dans [test d’une bibliothèque de .NET standard dans Visual Studio](testing-library-with-visual-studio.md), vous pouvez inclure votre application dans le cadre de cette solution. Par exemple, vous pouvez utiliser votre bibliothèque de classes dans une application console qui invite l’utilisateur à entrer une chaîne et indique si son premier caractère est une majuscule :

1. Ouvrez la solution `ClassLibraryProjects` que vous avez créée dans l’article [créer une bibliothèque de .NET standard dans Visual Studio](library-with-visual-studio.md) .

1. Ajoutez une nouvelle application console .NET Core nommée « ShowCase » à la solution.

   1. Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter** > **nouveau projet**.

   1. Dans la page **Ajouter un nouveau projet** , dans la zone de recherche, entrez **console** . Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme. Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.

   1. Dans la page **configurer votre nouveau projet** , entrez **Showcase** dans la zone **nom du projet** . Choisissez ensuite **Créer**.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ShowCase**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.

   ![Menu contextuel du projet Visual Studio pour définir le projet de démarrage](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Initialement, votre projet n’a pas accès à votre bibliothèque de classes. Pour lui permettre d’appeler des méthodes dans votre bibliothèque de classes, vous créez une référence à la bibliothèque de classes. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet `ShowCase` et sélectionnez **Ajouter une référence**.

   ![Menu contextuel ajouter une référence dans Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. Dans la boîte de dialogue **Gestionnaire de références**, sélectionnez **StringLibrary**, votre projet de bibliothèque de classe, puis sélectionnez le bouton **OK**.

   ![Boîte de dialogue Gestionnaire de références avec StringLibrary sélectionné](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. Dans la fenêtre de code du fichier *Program.cs* ou *Program. vb* , remplacez tout le code par le code suivant :

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console. Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.

   Le programme invite l’utilisateur à entrer une chaîne. Il indique si la chaîne commence par une majuscule. Si l’utilisateur appuie sur la touche entrée sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.

1. Si nécessaire, changez la barre d’outils pour compiler la version **Debug** du projet `ShowCase`. Compilez et exécutez le programme en sélectionnant la flèche verte sur le bouton **ShowCase**.

   ![Barre d’outils de projet Visual Studio avec le bouton déboguer](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

Vous pouvez déboguer et publier l’application qui utilise cette bibliothèque en suivant les étapes décrites dans [déboguer votre C# ou Visual Basic application Hello World .net core à l’aide de Visual Studio](debugging-with-visual-studio.md) et [publier votre application .net Core Hello World avec Visual Studio](publishing-with-visual-studio.md).

## <a name="create-a-nuget-package"></a>Créer un package NuGet

Vous pouvez rendre votre bibliothèque de classes disponible à grande échelle en la publiant sous forme de package NuGet. Visual Studio ne prend pas en charge la création de packages NuGet. Pour en créer un, vous devez utiliser les commandes CLI .NET Core :

1. Ouvrez une fenêtre de console.

   Par exemple, entrez l' **invite de commandes** dans la zone de recherche de la barre des tâches Windows. Sélectionnez l’application de bureau **invite de commandes** ou appuyez sur **entrée** si elle est déjà sélectionnée dans les résultats de la recherche.

1. Accédez au répertoire de votre projet de bibliothèque. Le répertoire contient votre code source et un fichier projet, *StringLibrary. csproj* ou *StringLibrary. vbproj*.

1. Exécutez la commande [dotnet Pack](../tools/dotnet-pack.md) pour générer un package avec l’extension *. nupkg* :

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > Si le répertoire contenant *dotnet.exe* ne se trouve pas dans votre chemin, vous pouvez trouver son emplacement en entrant `where dotnet.exe` dans la fenêtre de console.

Pour plus d’informations sur la création de packages NuGet, consultez [How to Create a NuGet package with the CLI .net Core](../deploying/creating-nuget-packages.md).
