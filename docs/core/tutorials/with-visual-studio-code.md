---
title: Prise en main de C# et Visual Studio Code
description: Découvrez comment créer et déboguer votre première application .NET Core en C# à l’aide de Visual Studio Code.
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506884"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Prise en main de C# et Visual Studio Code

.NET Core vous offre une plateforme rapide et évolutive pour la création d’applications qui s’exécutent sur Windows, Linux et Mac OS. Utilisez Visual Studio Code avec l’extension de langage C# pour une expérience d’édition puissante avec prise en charge complète de C# IntelliSense (saisie semi-automatique intelligente de code).

## <a name="prerequisites"></a>Prérequis

1. Installez [Visual Studio Code](https://code.visualstudio.com/).
2. Installez le [kit de développement logiciel (SDK) .NET Core](https://dotnet.microsoft.com/download).
3. Installez l’[extension C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) pour Visual Studio Code. Pour plus d’informations sur l’installation d’extensions pour Visual Studio Code, consultez [Place de marché des extensions VS Code](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

Prise en main d’un simple programme « Hello World » sur .NET Core :

1. Ouvrez un projet :

    - Ouvrez Visual Studio Code.
    - Sélectionnez **fichier** > **ouvrir le dossier** dans le menu principal.
    - Créez un dossier nommé *HelloWorld*, puis cliquez sur **Sélectionner un dossier**. Le nom du dossier devient le nom du projet et le nom de l’espace de noms par défaut. Vous ajouterez du code ultérieurement dans le didacticiel qui suppose que l’espace de `HelloWorld`noms du projet est.

1. Initialiser un projet C# :

    - Ouvrez le terminal à partir de Visual Studio code en sélectionnant **Afficher** > le**Terminal** dans le menu principal.
    - Dans la fenêtre de terminal, `dotnet new console`entrez.

      Cette commande crée un fichier *Program.cs* dans votre dossier avec un simple programme « Hello World » déjà écrit, ainsi qu’un fichier projet C# nommé *HelloWorld. csproj*.

      ![La nouvelle commande dotnet](media/with-visual-studio-code/dotnet-new-command.png)

1. Exécutez le programme Hello World :

    - Dans la fenêtre de terminal, `dotnet run`entrez.

      ![La commande dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a>Débogage

1. Ouvrez *Program.cs* en cliquant dessus. La première fois que vous ouvrez un fichier C# dans Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) se charge dans l’éditeur.

    ![Ouvrez le fichier Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. Visual Studio Code vous invite à ajouter les ressources manquantes pour générer et déboguer votre application. Sélectionnez **Oui**.

    ![Invite pour les fichiers manquants](media/with-visual-studio-code/missing-assets.png)

1. Pour ouvrir la vue de débogage, cliquez sur l’icône de débogage dans le menu de gauche.

    ![Ouvrir l’onglet Débogage dans Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

1. Cherchez la flèche verte en haut du volet. Assurez-vous que la liste déroulante en regard du menu de **lancement de .net Core (console)** est sélectionnée.

    ![Sélection de .NET Core dans Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

1. Ajoutez un point d’arrêt à votre projet en cliquant sur la **marge de l’éditeur**, qui est l’espace à gauche des numéros de ligne dans l’éditeur, à côté de la ligne 9, ou déplacez le curseur texte vers la ligne 9 dans l’éditeur et appuyez sur <kbd>F9</kbd>.

    ![Définition d'un point d'arrêt](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. Pour démarrer le débogage, appuyez sur <kbd>F5</kbd> ou sélectionnez la flèche verte. Le débogueur arrête l’exécution de votre programme lorsqu’il atteint le point d’arrêt que vous avez défini à l’étape précédente.
    - Lors du débogage, vous pouvez afficher vos variables locales dans le volet supérieur gauche ou utiliser la console de débogage.

1. Sélectionnez la flèche bleue en haut pour continuer le débogage, ou le carré rouge en haut pour l’arrêter.

    ![Exécution et débogage dans Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Pour obtenir plus d’informations et de conseils de dépannage sur le débogage de .NET Core avec OmniSharp dans Visual Studio Code, consultez [Instructions de configuration du débogueur .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Ajouter une classe

1. Pour ajouter une nouvelle classe, cliquez avec le bouton droit dans l’Explorateur VSCode sous *Program.cs* et sélectionnez **nouveau fichier**. Un nouveau fichier est ajouté au dossier ouvert dans VS Code.
1. Nommez votre fichier *MyClass.cs*. Vous devez l’enregistrer avec l’extension `.cs` à la fin pour qu’il soit reconnu comme fichier C#.
1. Ajoutez le code suivant pour créer votre première classe.

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

1. Appelez votre nouvelle classe à partir `Main` de votre méthode en remplaçant le code dans *Program.cs* par le code suivant :

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

1. Enregistrez vos modifications.

1. Réexécutez le programme.

    ```dotnetcli
    dotnet run
    ```

    Le nouveau message s’affiche avec la chaîne ajoutée.

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>Questions fréquentes (FAQ)

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Je n’ai pas les ressources nécessaires pour générer et déboguer du code C# dans Visual Studio Code. Mon débogueur indique « Aucune configuration ».

L’extension Visual Studio Code C# peut générer automatiquement les ressources dont vous avez besoin pour les builds et le débogage. Visual Studio Code vous invite à générer ces ressources à la première ouverture d’un projet C#. Si vous n’avez pas généré ces ressources au départ, vous pouvez le faire à tout moment en exécutant cette commande : ouvrez la palette de commandes (**Affichage > Palette de commandes**) et tapez « >.NET: Generate Assets for Build and Debug ». La sélection de cette option génère les fichiers de configuration *. vscode*, *Launch. JSON*et *Tasks. JSON* dont vous avez besoin.

## <a name="see-also"></a>Voir aussi

- [Configurer Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
- [Débogage dans Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
