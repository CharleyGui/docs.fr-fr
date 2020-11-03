---
title: Instructions de niveau supérieur-didacticiel C#
description: Ce didacticiel montre comment vous pouvez utiliser des instructions de niveau supérieur pour expérimenter et prouver des concepts tout en explorant vos idées
ms.date: 10/28/2020
ms.openlocfilehash: 5e5dc6cec382baa69ac8cb4625684315bb2cd5e0
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282261"
---
# <a name="tutorial-explore-ideas-using-top-level-statements-to-build-code-as-you-learn"></a>Didacticiel : Explorez des idées à l’aide d’instructions de niveau supérieur pour générer du code à mesure que vous en Apprenez

Ce didacticiel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
>
> - Découvrez les règles qui régissent l’utilisation des instructions de niveau supérieur.
> - Utilisez les instructions de niveau supérieur pour explorer les algorithmes.
> - Refactorisez les explorations dans des composants réutilisables.

## <a name="prerequisites"></a>Prérequis

Vous devez configurer votre ordinateur pour exécuter .NET 5, qui comprend le compilateur C# 9. Le compilateur C# 9 est disponible à partir de [Visual Studio 2019 version 16,9 Preview 1](https://visualstudio.microsoft.com/vs/preview/) ou [.net 5,0 SDK](https://dot.net/get-dotnet5).

Ce tutoriel suppose de connaître C# et .NET, y compris Visual Studio ou l’interface CLI .NET Core.

## <a name="start-exploring"></a>Commencez à explorer

Les instructions de niveau supérieur vous permettent d’éviter la cérémonie supplémentaire requise en plaçant le point d’entrée de votre programme dans une méthode statique dans une classe. Le point de départ classique d’une nouvelle application console ressemble au code suivant :

```csharp
using System;

namespace Application
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

Le code précédent est le résultat de l’exécution de la `dotnet new console` commande et de la création d’une nouvelle application console. Ces 11 lignes contiennent une seule ligne de code exécutable. Vous pouvez simplifier ce programme avec la nouvelle fonctionnalité d’instructions de niveau supérieur. Cela vous permet de supprimer toutes les lignes, sauf deux, dans ce programme :

```csharp
using System;

Console.WriteLine("Hello World!");
```

Cette action simplifie ce qui est nécessaire pour commencer à explorer de nouvelles idées. Vous pouvez utiliser des instructions de niveau supérieur pour les scénarios de script ou pour explorer. Une fois les principes de base opérationnels, vous pouvez commencer à refactoriser le code et créer des méthodes, des classes ou d’autres assemblys pour des composants réutilisables que vous avez générés. Les instructions de niveau supérieur permettent d’effectuer des expérimentations rapides et des didacticiels débutants. Ils fournissent également un chemin lisse entre l’expérimentation et les programmes complets.

Les instructions de niveau supérieur sont exécutées dans l’ordre dans lequel elles apparaissent dans le fichier. Les instructions de niveau supérieur ne peuvent être utilisées que dans un seul fichier source dans votre application. Le compilateur génère une erreur si vous les utilisez dans plusieurs fichiers.

## <a name="build-a-magic-net-answer-machine"></a>Créer un ordinateur de réponse Magic .NET

Pour ce didacticiel, nous allons créer une application console qui répond à une question « oui » ou « non » avec une réponse aléatoire. Vous allez créer les fonctionnalités pas à pas. Vous pouvez vous concentrer sur votre tâche plutôt que sur la cérémonie nécessaire à la structure d’un programme standard. Ensuite, une fois que vous êtes satisfait de la fonctionnalité, vous pouvez refactoriser l’application comme vous le souhaitez.

Un bon point de départ consiste à réécrire la question sur la console. Vous pouvez commencer par écrire le code suivant :

```csharp
using System;

Console.WriteLine(args);
```

Vous ne déclarez pas de `args` variable. Pour le fichier source unique qui contient vos instructions de niveau supérieur, le compilateur reconnaît `args` les arguments de ligne de commande. Le type des arguments est un `string[]` , comme dans tous les programmes C#.

Vous pouvez tester votre code en exécutant la `dotnet run` commande suivante :

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?
```

Les arguments qui suivent le `--` sur la ligne de commande sont passés au programme. Vous pouvez voir le type de la `args` variable, car il s’agit de l’impression sur la console :

```console
System.String[]
```

Pour écrire la question dans la console, vous devez énumérer les arguments et les séparer par un espace. Remplacez l' `WriteLine` appel par le code suivant :

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="EchoInput":::

Désormais, lorsque vous exécutez le programme, la question est correctement affichée sous la forme d’une chaîne d’arguments.

## <a name="respond-with-a-random-answer"></a>Répondre avec une réponse aléatoire

Après avoir renvoyé la question, vous pouvez ajouter le code pour générer la réponse aléatoire. Commencez par ajouter un tableau de réponses possibles :

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="Answers":::

Ce tableau a 12 réponses positives, six qui ne sont pas valides et six négatives. Ensuite, ajoutez le code suivant pour générer et afficher une réponse aléatoire à partir du tableau :

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="GenerateAnswer":::

Vous pouvez réexécuter l’application pour voir les résultats. Vous devriez voir une sortie semblable à la suivante :

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?

Should I use top level statements in all my programs?
Better not tell you now.
```

Ce code répond aux questions, mais nous allons ajouter une fonctionnalité supplémentaire. Vous aimeriez que votre application de question simule une réflexion sur la réponse. Vous pouvez le faire en ajoutant un peu d’animations ASCII et en interrompant le travail.  Ajoutez le code suivant après la ligne qui renvoie la question :

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="AnimationFirstPass":::

Vous devez également ajouter une `using` instruction en haut du fichier source :

```csharp
using System.Threading.Tasks;
```

Les `using` instructions doivent être antérieures à toute autre instruction dans le fichier. Dans le cas contraire, il s’agit d’une erreur du compilateur. Vous pouvez réexécuter le programme et voir l’animation. Cela offre une meilleure expérience. Expérimentez la longueur du délai pour vous adapter à votre goût.

Le code précédent crée un ensemble de lignes en rotation séparées par un espace. L’ajout du `await` mot clé indique au compilateur de générer le point d’entrée du programme en tant que méthode avec le `async` modificateur et retourne un <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> . Ce programme ne retourne pas de valeur, donc le point d’entrée du programme retourne un `Task` . Si votre programme retourne une valeur entière, vous devez ajouter une instruction return à la fin de vos instructions de niveau supérieur. Cette instruction return spécifie la valeur entière à retourner. Si vos instructions de niveau supérieur incluent une `await` expression, le type de retour devient <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> .

## <a name="refactoring-for-the-future"></a>Refactorisation à l’avenir

Votre programme doit ressembler au code suivant :

```csharp
using System;
using System.Threading.Tasks;

Console.WriteLine();
foreach(var s in args)
{
    Console.Write(s);
    Console.Write(' ');
}
Console.WriteLine();

for (int i = 0; i < 20; i++)
{
    Console.Write("| -");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("/ \\");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("- |");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("\\ /");
    await Task.Delay(50);
    Console.Write("\b\b\b");
}
Console.WriteLine();

string[] answers =
{
    "It is certain.",       "Reply hazy, try again.",     "Don’t count on it.",
    "It is decidedly so.",  "Ask again later.",           "My reply is no.",
    "Without a doubt.",     "Better not tell you now.",   "My sources say no.",
    "Yes – definitely.",    "Cannot predict now.",        "Outlook not so good.",
    "You may rely on it.",  "Concentrate and ask again.", "Very doubtful.",
    "As I see it, yes.",
    "Most likely.",
    "Outlook good.",
    "Yes.",
    "Signs point to yes.",
};

var index = new Random().Next(answers.Length - 1);
Console.WriteLine(answers[index]);
```

Le code précédent est raisonnable. Il fonctionne. Mais il n’est pas réutilisable. Maintenant que l’application fonctionne, il est temps de tirer parti des parties réutilisables.

Un candidat est le code qui affiche l’animation en attente. Cet extrait de code peut devenir une méthode :

Vous pouvez commencer par créer une fonction locale dans votre fichier. Remplacez l’animation actuelle par le code suivant :

```csharp
await ShowConsoleAnimation();

static async Task ShowConsoleAnimation()
{
    for (int i = 0; i < 20; i++)
    {
        Console.Write("| -");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("/ \\");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("- |");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("\\ /");
        await Task.Delay(50);
        Console.Write("\b\b\b");
    }
    Console.WriteLine();
}
```

Le code précédent crée une fonction locale à l’intérieur de votre méthode main. Cela n’est toujours pas réutilisable. Ainsi, extrayez ce code dans une classe. Créez un nouveau fichier nommé *Utilities.cs* et ajoutez le code suivant :

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="SnippetUtilities":::

Les instructions de niveau supérieur ne peuvent figurer que dans un seul fichier, et ce fichier ne peut pas contenir d’espaces de noms ou de types.

Enfin, vous pouvez nettoyer le code de l’animation pour supprimer des doublons :

:::code language="csharp" source="snippets/top-level-statements/Utilities.cs" ID="Animation":::

Vous disposez maintenant d’une application complète et vous avez refactorisé les parties réutilisables pour une utilisation ultérieure.

## <a name="summary"></a>Résumé

Les instructions de niveau supérieur facilitent la création de programmes simples à utiliser pour explorer les nouveaux algorithmes. Vous pouvez expérimenter des algorithmes en essayant différents extraits de code. Une fois que vous avez appris ce qui fonctionne, vous pouvez Refactoriser le code pour qu’il soit plus facile à gérer.

Les instructions de niveau supérieur simplifient les programmes basés sur les applications console. Il s’agit notamment des fonctions Azure, des actions GitHub et d’autres petits utilitaires.
