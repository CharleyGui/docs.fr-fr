---
title: Créer une bibliothèque de classes .NET à l’aide de Visual Studio Code
description: Découvrez comment créer une bibliothèque de classes .NET à l’aide de Visual Studio Code.
ms.date: 11/18/2020
ms.openlocfilehash: 4daa077fc54da3de2f808d831e06ee5f9bb3bde7
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916089"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-code"></a>Didacticiel : créer une bibliothèque de classes .NET à l’aide de Visual Studio Code

Dans ce didacticiel, vous allez créer une bibliothèque d’utilitaire simple qui contient une méthode de gestion de chaîne unique.

Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application. Si la bibliothèque cible .NET Standard 2,0, elle peut être appelée par n’importe quelle implémentation .NET (y compris .NET Framework) qui prend en charge .NET Standard 2,0. Si la bibliothèque cible .NET 5, elle peut être appelée par n’importe quelle application qui cible .NET 5. Ce didacticiel montre comment cibler .NET 5.

Lorsque vous créez une bibliothèque de classes, vous pouvez la distribuer en tant que composant tiers ou en tant que composant groupé avec une ou plusieurs applications.

## <a name="prerequisites"></a>Prérequis

1. [Visual Studio code](https://code.visualstudio.com/) avec l' [extension C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installée. Pour plus d’informations sur la façon d’installer des extensions sur Visual Studio Code, consultez [vs code d’extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).
2. Le [Kit de développement logiciel (SDK) .net 5,0 ou version ultérieure](https://dotnet.microsoft.com/download)

## <a name="create-a-solution"></a>Créer une solution

Commencez par créer une solution vide dans laquelle placer le projet de bibliothèque de classes. Une solution sert de conteneur pour un ou plusieurs projets. Vous ajouterez des projets connexes supplémentaires à la même solution.

1. Démarrez Visual Studio Code.

1. **File**  >  Dans le menu principal, sélectionnez fichier **ouvrir le dossier** (**Ouvrir...** sur MacOS).

1. Dans la boîte de dialogue **ouvrir un dossier** , créez un dossier *ClassLibraryProjects* , puis cliquez sur **Sélectionner un dossier** (**ouvrir** sur MacOS).

1. Ouvrez le **Terminal** dans Visual Studio code en sélectionnant **Afficher** le  >  **Terminal** dans le menu principal.

   Le **Terminal** s’ouvre avec l’invite de commandes dans le dossier *ClassLibraryProjects*

1. Dans le **Terminal**, entrez la commande suivante :

   ```dotnetcli
   dotnet new sln
   ```

   La sortie du terminal ressemble à l’exemple suivant :

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a>Créer un projet de bibliothèque de classes

Ajoutez un nouveau projet de bibliothèque de classes .NET nommé « StringLibrary » à la solution.

1. Dans le terminal, exécutez la commande suivante pour créer le projet de bibliothèque :

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   La `-o` `--output` commande ou spécifie l’emplacement où la sortie générée doit être placée.

   La sortie du terminal ressemble à l’exemple suivant :

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj (in 328 ms).
   Restore succeeded.
   ```

1. Exécutez la commande suivante pour ajouter le projet de bibliothèque à la solution :

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   La sortie du terminal ressemble à l’exemple suivant :

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. Assurez-vous que la bibliothèque cible .NET 5. Dans l' **Explorateur**, ouvrez *StringLibrary/StringLibrary. csproj*.

   L' `TargetFramework` élément indique que le projet cible .net 5,0.

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>net5.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. Ouvrez *Class1.cs* et remplacez le code par le code suivant.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   La bibliothèque de classes, `UtilityLibraries.StringLibrary` , contient une méthode nommée `StartsWithUpper` . Cette méthode retourne une <xref:System.Boolean> valeur qui indique si l’instance de chaîne en cours commence par un caractère majuscule. La norme Unicode distingue les caractères minuscules des caractères majuscules. La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.

1. Enregistrez le fichier .

1. Exécutez la commande suivante pour générer la solution et vérifier que le projet se compile sans erreur.

   ```dotnetcli
   dotnet build
   ```

   La sortie du terminal ressemble à l’exemple suivant :

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\net5.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a>Ajouter une application console à la solution

Ajoutez une application console qui utilise la bibliothèque de classes. L’application invite l’utilisateur à entrer une chaîne et signale si la chaîne commence par un caractère majuscule.

1. Dans le terminal, exécutez la commande suivante pour créer le projet d’application console :

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   La sortie du terminal ressemble à l’exemple suivant :

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj (in 210 ms).
   Restore succeeded.
   ```

1. Exécutez la commande suivante pour ajouter le projet d’application console à la solution :

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   La sortie du terminal ressemble à l’exemple suivant :

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. Ouvrez *Showcase/Program. cs* et remplacez tout le code par le code suivant.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console. Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.

   Le programme invite l’utilisateur à entrer une chaîne. Il indique si la chaîne commence par une majuscule. Si l’utilisateur appuie sur la touche <kbd>entrée</kbd> sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.

1. Enregistrez vos modifications.

## <a name="add-a-project-reference"></a>Ajouter une référence au projet

Initialement, le nouveau projet d’application console n’a pas accès à la bibliothèque de classes. Pour lui permettre d’appeler des méthodes dans la bibliothèque de classes, créez une référence de projet au projet de bibliothèque de classes.

1. Exécutez la commande suivante :

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   La sortie du terminal ressemble à l’exemple suivant :

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a>Exécuter l’application

1. Exécutez la commande suivante dans le terminal :

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. Essayez le programme en entrant des chaînes et en appuyant sur <kbd>entrée</kbd>, puis appuyez sur <kbd>entrée</kbd> pour quitter.

   La sortie du terminal ressemble à l’exemple suivant :

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a>Ressources supplémentaires

* [Développer des bibliothèques avec l’interface CLI .NET](libraries.md)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez créé une solution, ajouté un projet de bibliothèque et ajouté un projet d’application console qui utilise la bibliothèque. Dans le didacticiel suivant, vous allez ajouter un projet de test unitaire à la solution.

> [!div class="nextstepaction"]
> [Test d’une bibliothèque de classes .NET avec .NET à l’aide de Visual Studio Code](testing-library-with-visual-studio-code.md)
