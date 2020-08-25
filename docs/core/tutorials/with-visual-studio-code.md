---
title: Créer une application console .NET Core à l’aide de Visual Studio Code
description: Découvrez comment créer une application console .NET Core à l’aide de Visual Studio Code et du CLI .NET Core.
ms.date: 05/22/2020
ms.openlocfilehash: e936c23d8525e42a9d2781cc680067c9da2ce42f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811924"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-code"></a>Didacticiel : créer une application console .NET Core à l’aide de Visual Studio Code

Ce didacticiel montre comment créer et exécuter une application console .NET Core à l’aide de Visual Studio Code et du CLI .NET Core. Les tâches de projet, telles que la création, la compilation et l’exécution d’un projet, sont effectuées à l’aide de l’CLI .NET Core. Vous pouvez suivre ce didacticiel avec un autre éditeur de code et exécuter des commandes dans un terminal, si vous le souhaitez.

## <a name="prerequisites"></a>Prérequis

1. [Visual Studio code](https://code.visualstudio.com/) avec l' [extension C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installée. Pour plus d’informations sur la façon d’installer des extensions sur Visual Studio Code, consultez [vs code d’extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).
2. Le [Kit de développement logiciel (SDK) .net Core 3,1 ou version ultérieure](https://dotnet.microsoft.com/download)

## <a name="create-the-app"></a>Créer l’application

Créez un projet d’application console .NET Core nommé « HelloWorld ».

1. Démarrer Visual Studio Code

1. **File**  >  Dans le menu principal, sélectionnez fichier**ouvrir le dossier** (**fichier**  >  **Ouvrir..** . sur MacOS).

1. Dans la boîte de dialogue **ouvrir un dossier** , créez un dossier *HelloWorld* , puis cliquez sur **Sélectionner un dossier** (**ouvrir** sur MacOS).

   Le nom du dossier devient le nom du projet et le nom de l’espace de noms par défaut. Vous ajouterez du code ultérieurement dans le didacticiel qui suppose que l’espace de noms du projet est `HelloWorld` .

1. Ouvrez le **Terminal** dans Visual Studio code en sélectionnant **Afficher**le  >  **Terminal** dans le menu principal.

   Le **Terminal** s’ouvre avec l’invite de commandes dans le dossier *HelloWorld* .

1. Dans le **Terminal**, entrez la commande suivante :

   ```dotnetcli
   dotnet new console
   ```

Le modèle crée une application « Hello World » simple. Elle appelle la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> méthode pour afficher « :::no-loc text="Hello World!"::: » dans la fenêtre de console.

Le code du modèle définit une classe, `Program` , avec une méthode unique, `Main` , qui prend un <xref:System.String> tableau en tant qu’argument :

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application. Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.

## <a name="run-the-app"></a>Exécuter l’application

Exécutez la commande suivante dans le **Terminal**:

```dotnetcli
dotnet run
```

Le programme affiche « Hello World ! » et se termine.

![La commande dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a>Améliorer l’application

Améliorez l’application pour inviter l’utilisateur à entrer son nom et l’afficher avec la date et l’heure.

1. Ouvrez *Program.cs* en cliquant dessus.

   La première fois que vous ouvrez un fichier C# dans Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) se charge dans l’éditeur.

   ![Ouvrez le fichier Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. Sélectionnez **Oui** lorsque Visual Studio code vous invite à ajouter les ressources manquantes pour générer et déboguer votre application.

   ![Invite pour les fichiers manquants](media/with-visual-studio-code/missing-assets.png)

1. Remplacez le contenu de la `Main` méthode dans *Program.cs*, qui est la ligne qui appelle `Console.WriteLine` , avec le code suivant :

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   Ce code affiche une invite dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche <kbd>entrée</kbd> . Elle stocke cette chaîne dans une variable nommée `name` . Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`. Et affiche ces valeurs dans la fenêtre de console. Enfin, il affiche une invite dans la fenêtre de console et appelle la <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> méthode pour attendre l’entrée utilisateur.

   `\n`Représente un caractère de saut de ligne.

   Le signe dollar ( `$` ) devant une chaîne vous permet de placer des expressions telles que des noms de variable entre accolades dans la chaîne. La valeur de l’expression est insérée dans la chaîne à la place de l’expression. Cette syntaxe est appelée « [chaînes interpolées](../../csharp/language-reference/tokens/interpolated.md)».

1. Enregistrez vos modifications.

   > [!IMPORTANT]
   > Dans Visual Studio Code, vous devez enregistrer explicitement les modifications. Contrairement à Visual Studio, les modifications de fichiers ne sont pas enregistrées automatiquement quand vous générez et exécutez une application.

1. Réexécutez le programme :

   ```dotnetcli
   dotnet run
   ```

1. Répondez à l’invite en entrant un nom et en appuyant sur la touche <kbd>entrée</kbd> .

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Fenêtre de terminal avec sortie de programme modifiée":::

1. Appuyez sur n’importe quelle touche pour quitter le programme.

## <a name="additional-resources"></a>Ressources supplémentaires

- [Configurer Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez créé une application console .NET Core. Dans le didacticiel suivant, vous allez déboguer l’application.

> [!div class="nextstepaction"]
> [Déboguer une application console .NET Core à l’aide de Visual Studio Code](debugging-with-visual-studio-code.md)
