---
title: Application console
description: Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 4c32b08c3e7eeaedce687ea5bc572e6a7bee0d3e
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804892"
---
# <a name="console-app"></a>Application console

Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#. Vous apprendrez ce qui suit :

- Les principes de base du CLI .NET Core
- La structure d’une application de console C#
- E/S console
- Les principes fondamentaux des API d’E/S de fichier dans .NET
- Les principes fondamentaux de la programmation asynchrone basée sur des tâches dans .NET

Vous allez générer une application qui lit un fichier texte et renvoie le contenu de ce fichier texte sur la console. La sortie sur la console se fait à un rythme permettant de la lire à haute voix. Vous pouvez accélérer ou ralentir le rythme en appuyant sur les clés « < » (inférieure à) ou « > » (supérieur à).

Il existe un grand nombre de fonctionnalités dans ce didacticiel. Créons-les un par un.

## <a name="prerequisites"></a>Prérequis

- Configurez votre ordinateur pour exécuter .NET Core. Vous trouverez les instructions d’installation dans la page [téléchargements .net Core](https://dotnet.microsoft.com/download) . Vous pouvez exécuter cette application sur Windows, Linux, macOS ou dans un conteneur d’ancrage.

- Installez votre éditeur de code favori.

## <a name="create-the-app"></a>Créer l’application

La première étape consiste à créer une nouvelle application. Ouvrez une invite de commandes et créez un nouveau répertoire pour votre application. Réglez-le comme répertoire actuel. Saisissez la commande `dotnet new console` à l’invite. Elle crée les fichiers de démarrage d’une application « Hello World » de base.

Avant de commencer à apporter des modifications, suivez les étapes pour exécuter l’application simple Hello World. Après avoir créé l’application, saisissez `dotnet restore` à l’invite de commandes. Cette commande exécute le processus de restauration de package NuGet. NuGet est un gestionnaire de packages .NET. Cette commande télécharge les dépendances manquantes pour votre projet. Comme il s’agit d’un nouveau projet, aucune des dépendances n’est en place, donc la première exécution téléchargera le framework .NET Core. Après cette étape initiale, vous devrez exécuter `dotnet restore` lorsque vous ajoutez de nouveaux packages dépendants ou mettez à jour les versions de vos dépendances.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Après la restauration des packages, vous exécutez `dotnet build`. Cela exécute le moteur de génération et crée l’exécutable de votre application. Enfin, vous exécutez `dotnet run` pour lancer votre application.

Le code d’application Hello World simple se trouve intégralement dans le fichier Program.cs. Ouvrez ce fichier avec votre éditeur de texte préféré. Nous allons apporter nos premières modifications. En haut du fichier, remarquez l’instruction using :

```csharp
using System;
```

Cette instruction indique au compilateur que tous les types de l’espace de noms `System` sont dans la portée. Comme d’autres langages orientés objet que vous avez peut-être utilisés, C# utilise des espaces de noms pour organiser les types. Ce programme Hello World ne fait pas exception. Vous pouvez voir que le programme est placé dans l’espace de noms nommé d’après le nom du répertoire actuel. Pour ce tutoriel, nous changeons le nom de l’espace de noms en `TeleprompterConsole` :

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Lecture et affichage du fichier

La première fonctionnalité à ajouter est la capacité à lire un fichier texte et à afficher tout le texte dans la console. Tout d’abord, nous allons ajouter un fichier texte. Copiez le fichier [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) à partir du dépôt GitHub pour cet [exemple](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) dans votre répertoire de projet. Il servira de script pour votre application. Si vous voulez des informations sur la façon de télécharger l’exemple d’application de cette rubrique, consultez les instructions de la rubrique [Exemples et didacticiels](../../samples-and-tutorials/index.md#view-and-download-samples).

Ensuite, ajoutez la méthode suivante dans votre classe `Program` (juste en dessous de la méthode `Main`) :

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

Cette méthode utilise les types de deux nouveaux espaces de noms. Pour compiler, vous devez ajouter les deux lignes suivantes au début du fichier :

```csharp
using System.Collections.Generic;
using System.IO;
```

L'interface <xref:System.Collections.Generic.IEnumerable%601> est définie dans l’espace de noms <xref:System.Collections.Generic>. La classe <xref:System.IO.File> est définie dans l’espace de noms <xref:System.IO>.

Cette méthode est un type spécial de méthode C# appelé *méthode d’itérateur*. Les méthodes d’énumérateur retournent des séquences qui sont évaluées de manière tardive. Cela signifie que chaque élément de la séquence est généré lorsque cela est demandé par le code utilisant la séquence. Les méthodes d’énumérateur sont des méthodes qui contiennent une ou plusieurs [`yield return`](../language-reference/keywords/yield.md) instructions. L’objet retourné par la méthode `ReadFrom` contient le code pour générer chaque élément dans la séquence. Dans cet exemple, cela implique la lecture de la ligne de texte suivante à partir du fichier source et le renvoi de cette chaîne. Chaque fois que le code appelant demande l’élément suivant de la séquence, le code lit la ligne suivante du texte à partir du fichier et la renvoie. Quand le fichier est entièrement lu, la séquence indique qu’il n’y a pas d’autres éléments.

Il existe deux autres éléments de syntaxe de C# qui peuvent être nouveaux pour vous. L' [`using`](../language-reference/keywords/using-statement.md) instruction dans cette méthode gère le nettoyage des ressources. La variable initialisée dans l’instruction `using` (`reader`, dans cet exemple) doit implémenter l’interface <xref:System.IDisposable>. Cette interface définit une méthode unique, `Dispose`, qui doit être appelée lorsque les ressources doivent être libérées. Le compilateur génère l’appel lorsque l’exécution atteint l’accolade fermante de l’instruction `using`. Le code généré par le compilateur garantit que la ressource est libérée même si une exception est levée à partir du code dans le bloc défini par l’instruction using.

La variable `reader` est définie à l’aide du mot-clé `var`. [`var`](../language-reference/keywords/var.md) définit une *variable locale implicitement typée*. Cela signifie que le type de la variable est déterminé par le type au moment de la compilation de l’objet assigné à la variable. Ici, c’est la valeur retournée par la méthode <xref:System.IO.File.OpenText(System.String)>, qui est un objet <xref:System.IO.StreamReader>.

À présent, nous allons renseigner le code pour lire le fichier dans la `Main` méthode :

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Exécutez le programme (à l’aide de `dotnet run`). Chaque ligne est envoyée sur la console.

## <a name="adding-delays-and-formatting-output"></a>Ajout de délais et de mise en forme à la sortie

Ce que vous avez s’affiche beaucoup trop rapidement pour le lire à haute voix. Vous devez maintenant ajouter des délais à la sortie. Au démarrage, vous allez générer un code de base qui permet un traitement asynchrone. Toutefois, ces premières étapes suivront quelques anti-modèles. Les anti-modèles sont signalés dans les commentaires lorsque vous ajoutez le code, et le code sera actualisé ultérieurement.

Il existe deux étapes dans cette section. Tout d’abord, vous allez mettre à jour la méthode Iterator pour retourner des mots uniques au lieu de lignes entières. Cela se fait avec ces modifications. Remplacez l’instruction `yield return line;` par le code suivant :

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Ensuite, vous devez modifier la façon dont vous consommez les lignes du fichier, et ajoutez un délai après chaque mot. Remplacez l’instruction `Console.WriteLine(line)` dans la méthode `Main` avec le bloc suivant :

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

La classe <xref:System.Threading.Tasks.Task> se trouve dans l’espace de noms <xref:System.Threading.Tasks>, vous devez donc ajouter cette instruction `using` au début du fichier :

```csharp
using System.Threading.Tasks;
```

Exécutez l’exemple et vérifiez le résultat. À présent, chaque mot unique est affiché séparément, suivi d’un délai de 200 ms. Toutefois, la sortie affichée présente certains problèmes, car le fichier texte source possède plusieurs lignes qui ont plus de 80 caractères sans saut de ligne. Ce qui peut être difficile à lire lors du défilement. C’est facile à corriger. Il vous suffit d’effectuer le suivi de la longueur de chaque ligne et de générer une nouvelle ligne chaque fois que la longueur de la ligne atteint un certain seuil. Déclarez une variable locale après la déclaration de `words` dans la méthode `ReadFrom` qui contient la longueur de ligne :

```csharp
var lineLength = 0;
```

Ensuite, ajoutez le code suivant après l’instruction `yield return word + " ";` (avant l’accolade fermante) :

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

Exécutez l’exemple et vous serez en mesure de lire à haute voix à son rythme préconfiguré.

## <a name="async-tasks"></a>Tâches asynchrones

Dans cette étape finale, vous allez ajouter le code pour écrire la sortie de façon asynchrone dans une tâche, tout en exécutant également une autre tâche pour lire l’entrée de l’utilisateur s’il souhaite accélérer ou ralentir l’affichage du texte, ou arrêter complètement l’affichage du texte. Il y a quelques étapes dans l’informatique et, à la fin, vous disposerez de toutes les mises à jour dont vous avez besoin. La première étape consiste à créer une <xref:System.Threading.Tasks.Task> méthode de retour asynchrone qui représente le code que vous avez créé jusqu’à présent pour lire et afficher le fichier.

Ajoutez cette méthode à votre `Program` classe (elle est extraite du corps de votre `Main` méthode) :

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

Vous remarquerez deux modifications. Tout d’abord, dans le corps de la méthode, au lieu d’appeler <xref:System.Threading.Tasks.Task.Wait> pour attendre de manière synchrone qu’une tâche se termine, cette version utilise le mot-clé `await`. Pour ce faire, vous devez ajouter le modificateur `async` pour la signature de méthode. Cette méthode renvoie une `Task`. Notez qu’il n’y a aucune instruction de retour renvoyant un objet `Task`. Au lieu de cela, cet objet `Task` est créé par le code que le compilateur génère lorsque vous utilisez l’opérateur `await`. Vous pouvez imaginer que cette méthode renvoie une valeur lorsqu’elle atteint un `await`. La `Task` renvoyée indique que la tâche n’a pas été effectuée. La méthode reprend lorsque la tâche attendue se termine. Lorsqu’elle a terminé son exécution, la `Task` renvoyée indique qu’elle est terminée.
Le code appelant peut surveiller cette `Task` renvoyée pour déterminer si elle est terminée.

Vous pouvez appeler cette nouvelle méthode dans votre méthode `Main` :

```csharp
ShowTeleprompter().Wait();
```

Ici, dans `Main`, le code attend de façon synchrone. Vous devez utiliser l’opérateur `await` au lieu d’attendre de manière synchrone lorsque cela est possible. Toutefois, dans la méthode d’une application console `Main` , vous ne pouvez pas utiliser l' `await` opérateur. Cela entraînerait la fermeture de l’application avant la fin de toutes les tâches.

> [!NOTE]
> Si vous utilisez C# 7.1 ou une version ultérieure, vous pouvez créer des applications de console à l’aide de la méthode [`async` `Main`](../whats-new/csharp-7.md#async-main).

Ensuite, vous devez écrire la deuxième méthode asynchrone pour lire à partir de la console et surveiller les clés « < » (inférieur à), « > » (supérieur à) et « X » ou « x ». Voici la méthode que vous ajoutez pour cette tâche :

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

Cela crée une expression lambda pour représenter un <xref:System.Action> délégué qui lit une clé à partir de la console et modifie une variable locale représentant le délai quand l’utilisateur appuie sur les clés « < » (inférieur à) ou « > » (supérieur à). La méthode déléguée se termine lorsque l’utilisateur appuie sur les touches « X » ou « x », ce qui permet à l’utilisateur d’arrêter l’affichage du texte à tout moment. Cette méthode utilise <xref:System.Console.ReadKey> pour bloquer et attendre que l’utilisateur appuie sur une touche.

Pour terminer cette fonctionnalité, vous devez créer une nouvelle méthode de retour `async Task` qui démarre ces deux tâches (`GetInput` et `ShowTeleprompter`) et gère également les données partagées entre ces deux tâches.

Il est temps de créer une classe capable de gérer les données partagées entre ces deux tâches. Cette classe contient deux propriétés publiques : le délai et un indicateur `Done` pour indiquer que le fichier a été entièrement lu :

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            DelayInMilliseconds = newDelay;
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

Placez cette classe dans un nouveau fichier et ajoutez-la à l’espace de noms `TeleprompterConsole`, comme indiqué ci-dessus. Vous devez également ajouter une `using static` instruction pour pouvoir référencer les `Min` `Max` méthodes et sans les noms de classe ou d’espace de noms englobants. Une [`using static`](../language-reference/keywords/using-static.md) instruction importe les méthodes d’une classe. Cela est en opposition avec les instructions `using` utilisées jusqu'à présent, et qui avaient importé toutes les classes à partir d’un espace de noms.

```csharp
using static System.Math;
```

Ensuite, vous devez mettre à jour les méthodes `ShowTeleprompter` et `GetInput` pour utiliser le nouvel objet `config`. Écrivez une dernière `Task` renvoyant une méthode `async` pour démarrer les deux tâches et quitter lorsque la première tâche est terminée :

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Ici, la nouvelle méthode est l’appel <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])>. Elle crée une `Task` qui se termine dès que les tâches de sa liste d’arguments se terminent.

Ensuite, vous devez mettre à jour les méthodes `ShowTeleprompter` et `GetInput` pour utiliser l’objet `config` pour le délai :

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
                config.SetDone();
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

Cette nouvelle version de `ShowTeleprompter` appelle une nouvelle méthode dans la classe `TeleprompterConfig`. À présent, vous devez mettre à jour `Main` pour appeler `RunTeleprompter` au lieu de `ShowTeleprompter` :

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Conclusion

Ce didacticiel vous a montré certaines des fonctionnalités du langage C# et les bibliothèques .NET Core liées au travail dans les applications console. Vous pouvez utiliser ces connaissances pour explorer davantage le langage ainsi que les classes présentées ici. Vous avez vu les principes de base des e/s de fichier et de console, l’utilisation de blocage et de non-blocage de la programmation asynchrone basée sur des tâches, une visite guidée du langage C# et de la façon dont les programmes C# sont organisés, et les CLI .NET Core.

Pour plus d’informations sur les E/S de fichier, consultez la rubrique [E/S de fichier et de flux](../../standard/io/index.md). Pour plus d’informations sur le modèle de programmation asynchrone utilisé dans ce tutoriel, consultez la rubrique [Programmation asynchrone basée sur les tâches](../../standard/parallel-programming/task-based-asynchronous-programming.md) et la rubrique [Programmation asynchrone](../async.md).
