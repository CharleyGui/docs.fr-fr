---
title: Référence de F# Interactive (dotnet)
description: 'Découvrez comment F# Interactive (dotnet FSI) est utilisé pour exécuter le code F # de manière interactive sur la console ou pour exécuter des scripts F #.'
ms.date: 08/20/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: b1020d8ab8f2282c792fb5d00656b6d43c2c6610
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064117"
---
# <a name="interactive-programming-with-f"></a>Programmation interactive avec F\#

F# Interactive (dotnet FSI) est utilisé pour exécuter le code F # de manière interactive sur la console ou pour exécuter des scripts F #. En d'autres termes, F# interactive exécute un REPL (Read, Evaluate, Print Loop) pour le langage F#.

Pour exécuter F# Interactive à partir de la console, exécutez `dotnet fsi` . Vous y trouverez `dotnet fsi` tous les kits de développement logiciel (SDK) .net.

Pour plus d’informations sur les options de ligne de commande disponibles, consultez [Options de F# Interactive](../../language-reference/fsharp-interactive-options.md).

Pour exécuter F# Interactive par l’intermédiaire de Visual Studio, vous pouvez cliquer sur le bouton de barre d’outils approprié intitulé **F# Interactive** ou utiliser les touches **Ctrl+Alt+F** . La fenêtre interactive, fenêtre Outil exécutant une session F# Interactive, s'affiche. Vous pouvez également sélectionner du code que vous souhaitez exécuter dans la fenêtre interactive et appuyer sur la combinaison de touches **Alt + Entrée** . F# Interactive démarre dans une fenêtre Outil nommée **F# Interactive** . Lorsque vous utilisez cette combinaison de touches, assurez-vous que la fenêtre de l'éditeur a le focus.

Que vous utilisiez la console ou Visual Studio, une invite de commandes apparaît et l'interpréteur attend votre entrée. Vous pouvez saisir le code comme vous le feriez dans un fichier de code. Pour compiler et exécuter le code, entrez deux points-virgules ( **;;** ) pour terminer une ligne ou plusieurs lignes d’entrée.

F# Interactive tente de compiler le code et, en cas de réussite, exécute le code et imprime la signature des types et des valeurs qu'il a compilés. Si des erreurs se produisent, l'interpréteur imprime les messages d'erreur.

Le code entré dans la même session ayant accès à toutes les constructions entrées précédemment, vous pouvez développer des programmes. Une mémoire tampon étendue de la fenêtre Outil vous permet de copier le code dans un fichier si nécessaire.

Comme lors de l'exécution dans Visual Studio, F# Interactive s'exécute indépendamment de votre projet, vous ne pouvez pas, par exemple, utiliser les constructions définies dans votre projet F# Interactive, sauf si vous copiez le code de la fonction dans la fenêtre interactive.

Si vous avez un projet ouvert qui fait référence à des bibliothèques, vous pouvez référencer celles-ci dans F# Interactive par l’intermédiaire de l’ **Explorateur de solutions** . Pour référencer une bibliothèque dans F# Interactive, développez le nœud **Références** , ouvrez le menu contextuel de la bibliothèque et choisissez **Envoyer à F# Interactive** .

Vous pouvez contrôler les arguments de ligne de commande F# Interactive (options) en réglant les paramètres. Dans le menu **Outils** , sélectionnez **Options** , puis développez **Outils F#** . Les deux paramètres que vous pouvez changer sont les options F# Interactive et le paramètre **F# Interactive 64 bits** , qui n’est pertinent que si vous exécutez F# Interactive sur un ordinateur 64 bits. Ce paramètre détermine si vous souhaitez exécuter la version 64 bits dédiée de fsi.exe ou fsianycpu.exe, qui utilise l'architecture de l'ordinateur pour déterminer s'il doit s'exécuter comme processus 32 bits ou 64 bits.

## <a name="scripting-with-f"></a>Écriture de scripts avec F\#

Les scripts utilisent l’extension de fichier **.fsx** ou **.fsscript** . Au lieu de compiler le code source puis d’exécuter l’assembly compilé, vous pouvez simplement exécuter **dotnet FSI** et spécifier le nom de fichier du script du code source f #, et F # Interactive lit le code et l’exécute en temps réel.

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Différences entre les environnements interactifs, de script et compilés

Quand vous compilez du code en F# Interactive, que vous l’exécutiez interactivement ou exécutiez un script, le symbole **INTERACTIVE** est défini. Quand vous compilez le code dans le compilateur, le symbole **COMPILED** est défini. Par conséquent, si le code doit être différent dans les modes compilé et interactif, vous pouvez utiliser les directives du préprocesseur pour qu'une compilation conditionnelle déterminer quel code utiliser.

Certaines directives sont disponibles lorsque vous exécutez des scripts en F# Interactive qui ne sont pas disponibles lorsque vous exécutez le compilateur. Le tableau suivant résume les directives qui sont disponibles lorsque vous utilisez F# Interactive.

|Directive|Description|
|---------|-----------|
|**#help**|Affiche des informations sur les directives disponibles.|
|**#I**|Spécifie un chemin de recherche des assemblys entre guillemets.|
|**#load**|Lit un fichier source, le compile et l'exécute.|
|**#quit**|Met fin à une session de F# Interactive.|
|**#r**|Fait référence à un assembly.|
|**#time ["on"&#124;"off"]**|Seul, **#time** active ou désactive l’affichage des informations sur les performances. Lorsque cette option est activée, F# Interactive mesure le temps réel, le temps processeur et les informations de garbage collection pour chaque section du code qui est interprétée et exécutée.|

Lorsque vous spécifiez des fichiers ou des chemins d'accès dans F# Interactive, un littéral de chaîne est attendu. Par conséquent, les fichiers et les chemins d'accès doivent être entre guillemets, et les caractères d'échappement habituels s'appliquent. En outre, vous pouvez utiliser le caractère @ pour que F# Interactive interprète une chaîne qui contient un chemin d'accès comme chaîne textuelle. Dans ce cas, F# Interactive ignore les caractères d'échappement.

L’une des différences entre le mode compilé et le mode interactif est la façon d’accéder aux arguments de ligne de commande. En mode compilé, utilisez **System.Environment.GetCommandLineArgs** . Dans les scripts, utilisez **fsi.CommandLineArgs** .

Le code suivant illustre comment créer une fonction qui lit les arguments de ligne de commande dans un script et montre également comment référencer un autre assembly à partir d’un script. Le premier fichier de code, **MyAssembly.fs** , est le code de l’assembly référencé. Compilez ce fichier avec la ligne de commande **fsc -a MyAssembly.fs** , puis exécutez le second fichier comme script avec la ligne de commande **fsi --exec file1.fsx** test.

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

La sortie se présente comme suit :

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="package-management-in-f-interactive"></a>Package Management dans F# Interactive

[!NOTE] La gestion des packages est disponible sous la forme d’une fonctionnalité en version préliminaire dans les versions de `dotnet fsi` livrées avec `3.1.300` et versions ultérieures du kit de développement logiciel (SDK) .net, ainsi que toutes les `5.*` versions du kit de développement logiciel (SDK) .net. Pour l’activer dans cette version préliminaire, exécutez `dotnet fsi` avec l' `--langversion:preview` argument.

La `#r` syntaxe permettant de référencer une dll dans F# Interactive peut également être utilisée pour référencer un package NuGet à l’aide de la syntaxe suivante :

```fsharp
#r "nuget: <package name>"
```

Par exemple, pour référencer le `FSharp.Data` package, utilisez la `#r` référence suivante :

```fsharp
#r "nuget: FSharp.Data"
```

Après l’exécution de cette ligne, la version la plus récente du `FSharp.Data` package est téléchargée dans votre cache NuGet et référencée dans la session de F# Interactive actuelle.

En plus du nom du package, les versions spécifiques d’un package peuvent être référencées à l’aide d’une syntaxe abrégée :

```fsharp
#r "nuget: FSharp.Data, 3.3.2"
```

ou de manière plus explicite :

```fsharp
#r "nuget: FSharp.Data, Version=3.3.2"
```

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----|-----------|
|[Options F# Interactive](../../language-reference/fsharp-interactive-options.md)|Décrit la syntaxe et les options de ligne de commande pour le F# Interactive, fsi.exe.|
