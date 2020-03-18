---
title: Prise en main de C# et Visual Studio Code
description: Découvrez comment créer et déboguer votre première application .NET Core en C# à l’aide de Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: 8eaf1ba2314dcab96db615a8691afed82c5011a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398880"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Prise en main de C# et Visual Studio Code

.NET Core vous offre une plateforme rapide et évolutive pour la création d’applications qui s’exécutent sur Windows, Linux et Mac OS. Utilisez Visual Studio Code avec l’extension de langage C# pour une expérience d’édition puissante avec prise en charge complète de C# IntelliSense (saisie semi-automatique intelligente de code).

## <a name="prerequisites"></a>Conditions préalables requises

1. Installer [Visual Studio Code](https://code.visualstudio.com/).
2. Installer le [.NET Core SDK](https://dotnet.microsoft.com/download).
3. Installez l’[extension C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) pour Visual Studio Code. Pour plus d’informations sur l’installation d’extensions pour Visual Studio Code, consultez [Place de marché des extensions VS Code](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

Commençons par un programme « Hello World » simple sur .NET Core :

1. Ouvrez un projet :

    - Ouvrez Visual Studio Code.
    - Cliquez sur l’icône Explorer dans le menu de gauche, puis sur **Ouvrir le dossier**.
    - Sélectionnez **Fichier** > **Open Folder** dans le menu principal pour ouvrir le dossier que vous souhaitez que votre projet C ' soit dedans et cliquez sur **Select Folder**. Dans notre exemple, nous créons un dossier pour notre projet nommé *HelloWorld*.

      ![Ouvrir un dossier Visual Studio Code](media/with-visual-studio-code/vs-code-open-folder.png)

2. Initialiser un projet C# :

    - Ouvrez le terminal intégré à partir du code Visual Studio en sélectionnant **View** > **Integrated Terminal** à partir du menu principal.
    - Dans la fenêtre de Terminal, tapez `dotnet new console`.
    - Cette commande crée un fichier *Program.cs* dans votre dossier avec un simple "Hello World" programme déjà écrit, avec un fichier de projet C nommé *HelloWorld.csproj*.

      ![La nouvelle commande dotnet](media/with-visual-studio-code/dotnet-new-command.png)

3. Résolution des ressources de génération :

    - Pour **.NET Core 1.x**, tapez `dotnet restore`. Exécuter `dotnet restore` vous donne accès aux packages .NET Core qui sont nécessaires pour générer votre projet.

      ![La commande dotnet restore](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Exécutez le programme Hello World :

    - Tapez `dotnet run`.

      ![La commande dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

Vous pouvez également regarder un court didacticiel vidéo pour plus d’informations sur la configuration sur [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) ou [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Débogage

1. Ouvrez *Program.cs* en cliquant dessus. La première fois que vous ouvrez un fichier C# dans Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) se charge dans l’éditeur.

    ![Ouvrez le fichier Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. Visual Studio Code doit vous inviter à ajouter les ressources manquantes pour générer et déboguer votre application. Sélectionnez **Oui**.

    ![Invite pour les fichiers manquants](media/with-visual-studio-code/missing-assets.png)

3. Pour ouvrir la vue de débogage, cliquez sur l’icône de débogage dans le menu de gauche.

    ![Ouvrir l’onglet Débogage dans Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

4. Cherchez la flèche verte en haut du volet. Assurez-vous que le drop-down à côté de lui a **.NET Core Launch (console)** sélectionné.

    ![Sélection de .NET Core dans Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. Ajoutez un point d’arrêt à votre projet en cliquant sur la **marge de l’éditeur**, qui est l’espace à gauche des numéros de ligne dans l’éditeur, à côté de la ligne 9, ou déplacez le curseur texte vers la ligne 9 dans l’éditeur et appuyez sur <kbd>F9</kbd>.

    ![Définition d'un point d'arrêt](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Pour commencer à débogage, appuyez sur <kbd>F5</kbd> ou sélectionnez la flèche verte. Le débogueur arrête l’exécution de votre programme lorsqu’il atteint le point d’arrêt que vous avez défini à l’étape précédente.
    - Pendant le débogage, vous pouvez afficher vos variables locales dans le volet supérieur gauche ou utiliser la console de débogage.

7. Sélectionnez la flèche bleue en haut pour continuer le débogage, ou le carré rouge en haut pour l’arrêter.

    ![Exécution et débogage dans Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Pour obtenir plus d’informations et de conseils de dépannage sur le débogage de .NET Core avec OmniSharp dans Visual Studio Code, consultez [Instructions de configuration du débogueur .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Ajouter une classe

1. Pour ajouter une nouvelle classe, cliquez à droite dans le VSCode Explorer et sélectionnez **New File**. Un nouveau fichier est ajouté au dossier ouvert dans VS Code.
2. Nommez votre fichier *MyClass.cs*. Vous devez l’enregistrer avec l’extension `.cs` à la fin pour qu’il soit reconnu comme fichier C#.
3. Ajoutez le code ci-dessous pour créer votre première classe. Assurez-vous d’inclure l’espace de nom correct afin que vous puissiez le référencer à partir de votre fichier *Program.cs* :

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

4. Appelez votre nouvelle classe à partir de votre méthode principale en *Program.cs* en ajoutant le code ci-dessous :

    ```csharp
    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

5. Enregistrez vos modifications et exécutez à nouveau votre programme. Le nouveau message devrait apparaître avec la chaîne ajoutée.

    ```dotnetcli
    dotnet run
    ```

    Vous obtenez la sortie suivante :

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>Questions fréquentes (FAQ)

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Je n’ai pas les ressources nécessaires pour générer et déboguer du code C# dans Visual Studio Code. Mon débogueur indique « Aucune configuration ».

L’extension Visual Studio Code C# peut générer automatiquement les ressources dont vous avez besoin pour les builds et le débogage. Visual Studio Code vous invite à générer ces ressources à la première ouverture d’un projet C#. Si vous n’avez pas généré ces ressources au départ, vous pouvez le faire à tout moment en exécutant cette commande : ouvrez la palette de commandes (**Affichage > Palette de commandes**) et tapez « >.NET: Generate Assets for Build and Debug ». La sélection de ce produit génère le *.vscode*, *launch.json*, et les fichiers de configuration *tasks.json* dont vous avez besoin.

## <a name="see-also"></a>Voir aussi

- [Configurer Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
- [Débogage dans Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
