---
title: Consommer une bibliothèque .NET Standard dans Visual Studio 2017
description: Créez une application .NET Core qui appelle des membres d’une autre bibliothèque de classes avec Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: cfceb7ba384a28a09f172032f6edb6f5e495e9c0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420898"
---
# <a name="consume-a-net-standard-library-in-visual-studio-2017"></a>Consommer une bibliothèque .NET Standard dans Visual Studio 2017

Une fois que vous avez créé une bibliothèque de classes .NET Standard en suivant les étapes de [Création d’une bibliothèque de classes C# avec .NET Core dans Visual Studio 2017](./library-with-visual-studio.md) ou [Création d’une bibliothèque de classes Visual Basic avec .NET Core dans Visual Studio 2017](vb-library-with-visual-studio.md), que vous l’avez testée en suivant les instructions dans [Test d’une bibliothèque de classes avec .NET Core dans Visual Studio 2017](testing-library-with-visual-studio.md) et que vous avez créé une version Release de la bibliothèque, l’étape suivante consiste à la rendre accessible aux appelants. Pour cela, deux solutions s'offrent à vous :

* Si la bibliothèque doit être utilisée par une seule solution (par exemple s’il s’agit d’un composant dans une seule application de grande taille), vous pouvez l’inclure en tant que projet dans votre solution.

* Si la bibliothèque est généralement accessible, vous pouvez la distribuer comme package NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Inclusion d’une bibliothèque en tant que projet dans une solution

Tout comme vous avez inclus des tests unitaires dans la même solution que votre bibliothèque de classes, vous pouvez inclure votre application dans le cadre de cette solution. Par exemple, vous pouvez utiliser votre bibliothèque de classes dans une application console qui invite l’utilisateur à entrer une chaîne et indique si son premier caractère est une majuscule :

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Ouvrez la `ClassLibraryProjects` solution que vous avez créée dans la rubrique [Création d’une bibliothèque de classes C# avec .NET Core dans Visual Studio 2017](./library-with-visual-studio.md). Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur la solution **ClassLibraryProjects** et, dans le menu contextuel, sélectionnez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, développez le nœud **Visual C#** et sélectionnez le nœud **.NET Core**, puis choisissez le modèle de projet **Application console (.NET Core)** . Dans la zone de texte **Nom**, tapez « ShowCase », puis sélectionnez le bouton **OK**.

   ![Boîte de dialogue Ajouter un nouveau projet Visual Studio - C#](./media/consuming-library-with-visual-studio/add-new-project-dialog.png)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ShowCase**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.

   ![Menu contextuel de projet Visual Studio pour définir le projet de démarrage - C#](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Initialement, votre projet n’a pas accès à votre bibliothèque de classes. Pour lui permettre d’appeler des méthodes dans votre bibliothèque de classes, vous créez une référence à la bibliothèque de classes. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet `ShowCase` et sélectionnez **Ajouter une référence**.

   ![Menu contextuel Ajouter une référence dans un projet Visual Studio - C#](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. Dans la boîte de dialogue **Gestionnaire de références**, sélectionnez **StringLibrary**, votre projet de bibliothèque de classe, puis sélectionnez le bouton **OK**.

   ![Boîte de dialogue Gérer les références dans Visual Studio - C#](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. Dans la fenêtre de code pour le fichier *Program.cs*, remplacez tout le code par le code suivant :

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console. Chaque fois que ce nombre est supérieur ou égal à 25, le code efface la fenêtre de console et envoie un message à l’utilisateur.

   Le programme invite l’utilisateur à entrer une chaîne. Il indique si la chaîne commence par une majuscule. Si l’utilisateur appuie sur la touche Entrée sans entrer une chaîne, l’application se termine et la fenêtre de console se ferme.

1. Si nécessaire, changez la barre d’outils pour compiler la version **Debug** du projet `ShowCase`. Compilez et exécutez le programme en sélectionnant la flèche verte sur le bouton **ShowCase**.

   ![Barre d’outils d’un projet Visual Studio montrant le bouton Déboguer - C#](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Ouvrez la solution `ClassLibraryProjects` que vous avez créée dans la rubrique [Création d’une bibliothèque de classes avec Visual Basic et .NET Core dans Visual Studio 2017](vb-library-with-visual-studio.md). Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur la solution **ClassLibraryProjects** et, dans le menu contextuel, sélectionnez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, développez le nœud **Visual Basic** et sélectionnez le nœud **.NET Core**, puis choisissez le modèle de projet **Application console (.NET Core)** . Dans la zone de texte **Nom**, tapez « ShowCase », puis sélectionnez le bouton **OK**.

   ![Boîte de dialogue Ajouter un nouveau projet Visual Studio - Visual Basic](./media/consuming-library-with-visual-studio/add-new-vb-project-dialog.png)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ShowCase**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel. 

   ![Menu contextuel de projet Visual Studio pour définir le projet de démarrage - Visual Basic](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Initialement, votre projet n’a pas accès à votre bibliothèque de classes. Pour lui permettre d’appeler des méthodes dans votre bibliothèque de classes, vous créez une référence à la bibliothèque de classes. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet `ShowCase` et sélectionnez **Ajouter une référence**.

   ![Menu contextuel Ajouter une référence dans un projet Visual Studio - Visual Basic](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. Dans la boîte de dialogue **Gestionnaire de références**, sélectionnez **StringLibrary**, votre projet de bibliothèque de classe, puis sélectionnez le bouton **OK**.

   ![Boîte de dialogue Gérer les références dans Visual Studio - Visual Basic](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. Dans la fenêtre de code pour le fichier *Program.vb*, remplacez tout le code par le code suivant :

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console. Chaque fois que ce nombre est supérieur ou égal à 25, le code efface la fenêtre de console et envoie un message à l’utilisateur.

   Le programme invite l’utilisateur à entrer une chaîne. Il indique si la chaîne commence par une majuscule. Si l’utilisateur appuie sur la touche Entrée sans entrer une chaîne, l’application se termine et la fenêtre de console se ferme.

1. Si nécessaire, changez la barre d’outils pour compiler la version **Debug** du projet `ShowCase`. Compilez et exécutez le programme en sélectionnant la flèche verte sur le bouton **ShowCase**.

   ![Déboguer sur la barre d’outils - Visual Basic](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

---

Vous pouvez déboguer et publier l’application qui utilise cette bibliothèque en suivant les étapes de [Débogage de votre application Hello World avec Visual Studio 2017](debugging-with-visual-studio.md) et de [Publication de votre application Hello World avec Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="distributing-the-library-in-a-nuget-package"></a>Distribution de la bibliothèque dans un package NuGet

Vous pouvez rendre votre bibliothèque de classes disponible à grande échelle en la publiant sous forme de package NuGet. Visual Studio ne prend pas en charge la création des packages NuGet. Pour en créer un, vous utilisez l’[`dotnet`utilitaire de ligne de commande](../tools/dotnet.md) :

1. Ouvrez une fenêtre de console. Par exemple, dans la zone de texte **Posez-moi une question** dans la barre des tâches Windows, entrez `Command Prompt` (ou `cmd` en abrégé) et ouvrez une fenêtre de console en sélectionnant l’application de poste de travail **Invite de commandes** ou en appuyant sur Entrée si elle est sélectionnée dans les résultats de la recherche.

1. Accédez au répertoire de votre projet de bibliothèque. Sauf si vous avez reconfiguré l’emplacement habituel du fichier, il se trouve dans le répertoire *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary*. Le répertoire contient votre code source et un fichier projet, *StringLibrary.csproj*.

1. Émettez la commande `dotnet pack --no-build`. L’utilitaire `dotnet` génère un package avec une extension *.nupkg*.

   > [!TIP]
   > Si le répertoire contenant *dotnet.exe* ne se trouve pas dans votre chemin, vous pouvez trouver son emplacement en entrant `where dotnet.exe` dans la fenêtre de console.

Pour plus d’informations sur la création de packages NuGet, consultez [Création d’un Package NuGet avec les outils multiplateformes](../deploying/creating-nuget-packages.md).
