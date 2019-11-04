---
title: Bien démarrer avec .NET Core à l’aide de l’interface CLI
description: Didacticiel pas à pas montrant comment démarrer avec .NET Core sur Windows, Linux ou Mac OS à l’aide de l’interface de ligne de commande (CLI) .NET Core.
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: c7e314e9712c3b569ecc813a72670942651feda1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454740"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Bien démarrer avec .NET Core sur Windows/Linux/macOS en ligne de commande

Cette rubrique décrit comment commencer à développer des applications multiplateformes sur votre ordinateur à l’aide des outils CLI .NET Core.

Si vous n’êtes pas familiarisé avec l’ensemble d’outils CLI .NET Core, consultez [Vue d’ensemble du SDK .NET Core](../tools/index.md).

## <a name="prerequisites"></a>Configuration requise

- [Kit SDK .NET Core 2,1](https://dotnet.microsoft.com/download) ou versions ultérieures.
- Un éditeur de texte ou un éditeur de code de votre choix.

## <a name="hello-console-app"></a>Application console Hello

Vous pouvez [afficher ou télécharger l’exemple de code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) à partir du dépôt GitHub dotnet/samples. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Ouvrez une invite de commandes et créez un dossier nommé *Hello*. Accédez au dossier créé et tapez ce qui suit :

```dotnetcli
dotnet new console
dotnet run
```

Suivons une procédure pas à pas rapide :

1. `dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) crée un fichier projet *Hello. csproj* à jour avec les dépendances nécessaires pour générer une application console. Il crée également un *Program.cs*, un fichier de base contenant le point d’entrée de l’application.

   *Bonjour. csproj*:

   [!code-xml[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   Le fichier projet spécifie tout ce qui est nécessaire pour restaurer les dépendances et générer le programme.

   - La balise `OutputType` spécifie que nous générons un fichier exécutable, autrement dit une application console.
   - La balise `TargetFramework` spécifie l’implémentation .NET que nous ciblons. Dans un scénario avancé, vous pouvez spécifier plusieurs frameworks cibles et y effectuer une génération globale en une seule opération. Dans ce tutoriel, nous nous en tiendrons à une génération limitée à .NET Core 2.1.

   *Program.cs* :

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   Le programme commence par `using System`, ce qui signifie « placer tout ce qui se trouve dans l’espace de noms `System` dans la portée de ce fichier ». L’espace de noms `System` inclut des constructions de base, telles que `string`, ou des types numériques.

   Ensuite, nous définissons un espace de noms appelé `Hello`. Vous pouvez le modifier à votre gré. Une classe nommée `Program` est définie dans cet espace de noms avec une méthode `Main` qui accepte un tableau de chaînes comme argument. Ce tableau contient la liste des arguments passés quand le programme compilé est appelé. Tel quel, ce tableau n’est pas utilisé : le programme se limite à écrire « Hello World! » dans la console. Plus tard, nous apporterons des modifications au code qui utilisent cet argument.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   `dotnet new` appelle [`dotnet restore`](../tools/dotnet-restore.md) implicitement. `dotnet restore` appelle [NuGet](https://www.nuget.org/) (gestionnaire de package .NET) pour restaurer l’arborescence de dépendances. NuGet analyse le fichier *Hello.csproj*, télécharge les dépendances définies dans le fichier (ou les récupère dans un cache sur votre ordinateur) et écrit le fichier *obj/project.assets.json*, nécessaire pour compiler et exécuter l’exemple.

   > [!IMPORTANT]
   > Si vous utilisez une version .NET Core 1.x du SDK, vous devrez appeler `dotnet restore` vous-même après l’appel de `dotnet new`.

2. `dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) appelle [`dotnet build`](../tools/dotnet-build.md) pour garantir que les cibles de génération ont été générées, puis appelle `dotnet <assembly.dll>` pour exécuter l’application cible.

    ```console
    $ dotnet run
    Hello World!
    ```

    Si vous préférez, vous pouvez exécuter [`dotnet build`](../tools/dotnet-build.md) pour compiler le code sans exécuter les applications console de la build. Il en résulte une application compilée sous forme de fichier DLL qui peut être exécutée avec `dotnet bin\Debug\netcoreapp2.1\Hello.dll` sur Windows (utilisez `/` sur les autres systèmes). Vous pouvez également spécifier des arguments pour l’application, comme nous le verrons par la suite dans la rubrique.

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    Dans le cadre d’un scénario avancé, vous pouvez générer l’application comme un ensemble autonome de fichiers spécifiques à la plateforme qui peuvent être déployés et exécutés sur un ordinateur sur lequel .NET Core n’est pas nécessairement installé. Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../deploying/index.md).

### <a name="augmenting-the-program"></a>Augmentation du programme

Modifions un peu le programme. Les nombres de Fibonacci sont amusants, nous allons donc les ajouter en plus de l’argument pour accueillir la personne qui exécute l’application.

1. Remplacez le contenu du fichier *Program.cs* par le code suivant :

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. Exécutez [`dotnet build`](../tools/dotnet-build.md) pour compiler les modifications.

3. Exécutez le programme en passant un paramètre à l’application :

   ```console
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

Et voilà !  Vous pouvez augmenter `Program.cs` comme vous le souhaitez.

## <a name="working-with-multiple-files"></a>Utilisation de plusieurs fichiers

Les fichiers uniques conviennent à des programmes simples et ponctuels, mais si vous créez une application plus complexe, vous avez probablement plusieurs fichiers sources dans votre projet.
Reprenons l’exemple précédent de Fibonacci en mettant en cache certaines valeurs de Fibonacci et en ajoutant des fonctionnalités récursives.

1. Ajoutez un nouveau fichier nommé *FibonacciGenerator.cs* dans le répertoire *Hello* avec le code suivant :

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. Modifiez la méthode `Main` dans votre fichier *Program.cs* pour instancier la nouvelle classe et appelez sa méthode comme dans l’exemple suivant :

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Exécutez [`dotnet build`](../tools/dotnet-build.md) pour compiler les modifications.

4. Exécutez votre application en exécutant [`dotnet run`](../tools/dotnet-run.md). Voici la sortie du programme :

   ```console
   $ dotnet run
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

## <a name="publish-your-app"></a>Publier une application

Lorsque vous êtes prêt à distribuer votre application, utilisez la commande [`dotnet publish`](../tools/dotnet-publish.md) pour générer le dossier _publish_ dans _bin\\debug\\netcoreapp2.1\\publish\\_ (utilisez `/` pour les systèmes non Windows). Vous pouvez distribuer le contenu du dossier _publish_ sur d'autres plates-formes tant qu'elles ont déjà installé le runtime dotnet.

Vous pouvez exécuter votre application publiée avec la commande [dotnet](../tools/dotnet.md) :

```console
$ dotnet bin\Debug\netcoreapp2.1\publish\Hello.dll
Hello World!
```

## <a name="conclusion"></a>Conclusion

Et voilà ! À présent, vous pouvez commencer à utiliser les concepts de base que vous avez appris ici pour créer vos propres programmes.

## <a name="see-also"></a>Voir aussi

- [Organisation et test de projets avec les outils CLI .NET Core](testing-with-cli.md)
- [Publier des applications .NET Core avec l’interface CLI](../deploying/deploy-with-cli.md)
- [Pour en savoir plus sur le déploiement](../deploying/index.md)
