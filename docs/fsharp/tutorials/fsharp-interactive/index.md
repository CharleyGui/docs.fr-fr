---
title: Référence de F# Interactive (dotnet)
description: 'Découvrez comment F# Interactive (dotnet FSI) est utilisé pour exécuter le code F # de manière interactive sur la console ou pour exécuter des scripts F #.'
ms.date: 10/31/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 89570a54ecebe625a1612e4b97b01c3693e4707c
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400864"
---
# <a name="interactive-programming-with-f"></a>Programmation interactive avec F\#

F# Interactive (dotnet FSI) est utilisé pour exécuter le code F # de manière interactive sur la console ou pour exécuter des scripts F #. En d'autres termes, F# interactive exécute un REPL (Read, Evaluate, Print Loop) pour le langage F#.

Pour exécuter F# Interactive à partir de la console, exécutez `dotnet fsi` . Vous y trouverez `dotnet fsi` tous les kits de développement logiciel (SDK) .net.

Pour plus d’informations sur les options de ligne de commande disponibles, consultez [options de F# Interactive](../../language-reference/fsharp-interactive-options.md).

## <a name="executing-code-directly-in-f-interactive"></a>Exécution de code directement dans F# Interactive

Étant donné que F# Interactive est une boucle REPL (lecture-eval-Print), vous pouvez exécuter le code de manière interactive dans celui-ci. Voici un exemple de session interactive après `dotnet fsi` l’exécution à partir de la ligne de commande :

```console
Microsoft (R) F# Interactive version 11.0.0.0 for F# 5.0
Copyright (c) Microsoft Corporation. All Rights Reserved.

For help type #help;;

> let square x = x *  x;;
val square : x:int -> int

> square 12;;
val it : int = 144

> printfn "Hello, FSI!"
- ;;
Hello, FSI!
val it : unit = ()
```

Vous remarquerez deux choses principales :

1. Tout le code doit se terminer par un double point-virgule ( `;;` ) à évaluer
2. Le code est évalué et stocké dans une `it` valeur. Vous pouvez référencer de `it` manière interactive.

F# Interactive prend également en charge l’entrée multiligne. Vous devez simplement mettre fin à la soumission avec un double point-virgule ( `;;` ). Examinez l’extrait de code suivant qui a été collé dans et évalué par F# Interactive :

```console
> let getOddSquares xs =
-     xs
-     |> List.filter (fun x -> x % 2 <> 0)
-     |> List.map (fun x -> x * x)
-
- printfn "%A" (getOddSquares [1..10]);;
[1; 9; 25; 49; 81]
val getOddSquares : xs:int list -> int list
val it : unit = ()

>
```

La mise en forme du code est préservée et un double point-virgule ( `;;` ) termine l’entrée. F# Interactive ensuite évalué le code et imprimé les résultats !

## <a name="scripting-with-f"></a>Écriture de scripts avec F\#

L’évaluation interactive du code dans F# Interactive peut être un excellent outil d’apprentissage, mais vous découvrirez rapidement qu’il n’est pas aussi productif que d’écrire du code dans un éditeur normal. Pour prendre en charge la modification de code normale, vous pouvez écrire des scripts F #.

Les scripts utilisent l’extension de fichier **. FSX**. Au lieu de compiler le code source puis d’exécuter l’assembly compilé, vous pouvez simplement exécuter **dotnet FSI** et spécifier le nom de fichier du script du code source f #, et F # Interactive lit le code et l’exécute en temps réel. Par exemple, considérez le script suivant appelé `Script.fsx` :

```fsharp
let getOddSquares xs =
    xs
    |> List.filter (fun x -> x % 2 <> 0)
    |> List.map (fun x -> x * x)

getOddSquares [1..10]
```

Lorsque ce fichier est créé sur votre ordinateur, vous pouvez l’exécuter avec `dotnet fsi` et voir la sortie directement dans la fenêtre de votre terminal :

```console
dotnet fsi Script.fsx
[1; 9; 25; 49; 81]
```

Les scripts F # sont pris en charge en mode natif dans [Visual Studio](../../get-started/get-started-visual-studio.md), [Visual Studio code](../../get-started/get-started-vscode.md)et [Visual Studio pour Mac](../../get-started/get-started-with-visual-studio-for-mac.md).

## <a name="referencing-packages-in-f-interactive"></a>Référencement de packages dans F# Interactive

> [!NOTE]
> La gestion des packages est une fonctionnalité F # 5 qui est actuellement disponible à l’aide du dernier Kit de développement logiciel (SDK) .NET 5.

F# Interactive prend en charge le référencement de packages NuGet avec la `#r "nuget:"` syntaxe et une version facultative :

```fsharp
#r "nuget: Newtonsoft.Json"
open Newtonsoft.Json

let data = {| Name = "Don Syme"; Occupation = "F# Creator" |}
JsonConvert.SerializeObject(data)
```

Si aucune version n’est spécifiée, le package non préliminaire disponible le plus élevé est pris. Pour référencer une version spécifique, introduisez la version à l’aide d’une virgule. Cela peut être pratique lorsque vous référencez une version préliminaire d’un package. Par exemple, considérez ce script en utilisant une version préliminaire de [DiffSharp](https://diffsharp.github.io/):

```fsharp
#r "nuget: DiffSharp-lite,1.0.0-preview-328097867"
open DiffSharp

// A 1D tensor
let t1 = dsharp.tensor [ 0.0 .. 0.2 .. 1.0 ]

// A 2x2 tensor
let t2 = dsharp.tensor [ [ 0; 1 ]; [ 2; 2 ] ]

// Define a scalar-to-scalar function
let f (x: Tensor) = sin (sqrt x)

printfn "%A" (f (dsharp.tensor 1.2))
```

Vous pouvez spécifier autant de références de package que vous le souhaitez dans un script.

## <a name="referencing-assemblies-on-disk-with-f-interactive"></a>Référencement d’assemblys sur un disque avec F # Interactive

Sinon, si vous disposez d’un assembly sur le disque et que vous souhaitez le référencer dans un script, vous pouvez utiliser la `#r` syntaxe pour spécifier un assembly. Examinez le code suivant dans un projet compilé dans `MyAssembly.dll` :

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

Une fois compilé, vous pouvez le référencer dans un fichier appelé, par `Script.fsx` exemple :

```fsharp
#r "path/to/MyAssembly.dll"

printfn "%A" (MyAssembly.myFunction 10 40)
```

La sortie se présente comme suit :

```console
dotnet fsi Script.fsx
90
```

Vous pouvez spécifier autant de références d’assembly que vous le souhaitez dans un script.

## <a name="loading-other-scripts"></a>Chargement d’autres scripts

Lors de l’écriture de scripts, il peut souvent être utile d’utiliser différents scripts pour différentes tâches. Il peut arriver que vous souhaitiez réutiliser du code à partir d’un script dans un autre. Au lieu de copier-coller son contenu dans votre fichier, vous pouvez le charger et l’évaluer facilement avec `#load` .

Tenez compte des points suivants `Script1.fsx` :

```fsharp
let square x = x * x
```

Et le fichier de consommation `Script2.fsx` :

```fsharp
#load "Script1.fsx"
open Script1

printfn "%d" (square 12)
```

Notez que la `open Script1` déclaration est obligatoire. Cela est dû au fait que les constructions dans un script F # sont compilées dans un module de niveau supérieur qui est le nom du fichier de script dans lequel elle se trouve.

Vous pouvez évaluer `Script2.fsx` comme suit :

```console
dotnet fsi Script2.fsx
144
```

Vous pouvez spécifier autant `#load` de directives que vous le souhaitez dans un script.

## <a name="using-the-fsi-object-in-f-code"></a>Utilisation `fsi` de l’objet dans le code F #

Les scripts F # ont accès à un `fsi` objet personnalisé qui représente la session F# Interactive. Elle vous permet de personnaliser des éléments tels que la mise en forme de la sortie. C’est également la manière dont vous pouvez accéder aux arguments de ligne de commande.

L’exemple suivant montre comment récupérer et utiliser des arguments de ligne de commande :

```fsharp
let args = fsi.CommandLineArgs

for arg in args do
    printfn "%s" arg
```

Lorsqu’elle est évaluée, elle imprime tous les arguments. Le premier argument est toujours le nom du script évalué :

```dotnet
dotnet fsi Script1.fsx hello world from fsi
Script1.fsx
hello
world
from
fsi
```

Vous pouvez également utiliser `System.Environment.GetCommandLineArgs()` pour accéder aux mêmes arguments.

## <a name="f-interactive-directive-reference"></a>Informations de référence sur la directive F# Interactive

Les `#r` `#load` directives et présentées précédemment sont uniquement disponibles dans F# Interactive. Plusieurs directives sont uniquement disponibles dans F# Interactive :

|Directive|Description|
|---------|-----------|
|`#r "nuget:..."`|Fait référence à un package à partir de NuGet|
|`#r "assembly-name.dll"`|Référence un assembly sur le disque|
|`#load "file-name.fsx"`|Lit un fichier source, le compile et l'exécute.|
|`#help`|Affiche des informations sur les directives disponibles.|
|`#I`|Spécifie un chemin de recherche des assemblys entre guillemets.|
|`#quit`|Met fin à une session de F# Interactive.|
|`#time "on"` ou `#time "off"`|Par lui-même, `#time` active ou désactive l’affichage des informations de performances. Quand c’est le cas `"on"` , F# Interactive mesure le temps réel, le temps processeur et les informations garbage collection pour chaque section de code qui est interprétée et exécutée.|

Lorsque vous spécifiez des fichiers ou des chemins d'accès dans F# Interactive, un littéral de chaîne est attendu. Par conséquent, les fichiers et les chemins d'accès doivent être entre guillemets, et les caractères d'échappement habituels s'appliquent. Vous pouvez utiliser le `@` caractère pour que F# Interactive interprète une chaîne qui contient un chemin d’accès comme chaîne textuelle. Dans ce cas, F# Interactive ignore les caractères d'échappement.

## <a name="interactive-and-compiled-preprocessor-directives"></a>Directives de préprocesseurs interactives et compilées

Quand vous compilez du code dans F# Interactive, que vous exécutez de manière interactive ou que vous exécutiez un script, le symbole **interactif** est défini. Quand vous compilez du code dans le compilateur, le symbole **compilé** est défini. Par conséquent, si le code doit être différent dans les modes compilé et interactif, vous pouvez utiliser ces directives de préprocesseur pour la compilation conditionnelle afin de déterminer laquelle utiliser. Par exemple :

```fsharp
#if INTERACTIVE
// Some code that executes only in FSI
// ...
#endif
```

## <a name="using-f-interactive-in-visual-studio"></a>Utilisation de F# Interactive dans Visual Studio

Pour exécuter F# Interactive par l’intermédiaire de Visual Studio, vous pouvez cliquer sur le bouton de barre d’outils approprié intitulé **F# Interactive** ou utiliser les touches **Ctrl+Alt+F**. La fenêtre interactive, fenêtre Outil exécutant une session F# Interactive, s'affiche. Vous pouvez également sélectionner du code que vous souhaitez exécuter dans la fenêtre interactive et appuyer sur la combinaison de touches **Alt + Entrée**. F# Interactive démarre dans une fenêtre Outil nommée **F# Interactive**. Lorsque vous utilisez cette combinaison de touches, assurez-vous que la fenêtre de l'éditeur a le focus.

Que vous utilisiez la console ou Visual Studio, une invite de commandes apparaît et l'interpréteur attend votre entrée. Vous pouvez saisir le code comme vous le feriez dans un fichier de code. Pour compiler et exécuter le code, entrez deux points-virgules ( **;;** ) pour terminer une ligne ou plusieurs lignes d’entrée.

F# Interactive tente de compiler le code et, en cas de réussite, exécute le code et imprime la signature des types et des valeurs qu'il a compilés. Si des erreurs se produisent, l'interpréteur imprime les messages d'erreur.

Le code entré dans la même session ayant accès à toutes les constructions entrées précédemment, vous pouvez développer des programmes. Une mémoire tampon étendue de la fenêtre Outil vous permet de copier le code dans un fichier si nécessaire.

Comme lors de l'exécution dans Visual Studio, F# Interactive s'exécute indépendamment de votre projet, vous ne pouvez pas, par exemple, utiliser les constructions définies dans votre projet F# Interactive, sauf si vous copiez le code de la fonction dans la fenêtre interactive.

Vous pouvez contrôler les F# Interactive arguments de ligne de commande (options) en ajustant les paramètres. Dans le menu **Outils** , sélectionnez **Options** , puis développez **Outils F#**. Les deux paramètres que vous pouvez changer sont les options F# Interactive et le paramètre **F# Interactive 64 bits** , qui n’est pertinent que si vous exécutez F# Interactive sur un ordinateur 64 bits. Ce paramètre détermine si vous souhaitez exécuter la version 64 bits dédiée de **fsi.exe** ou **fsianycpu.exe** , qui utilise l’architecture de l’ordinateur pour déterminer s’il doit s’exécuter en tant que processus 32 bits ou 64 bits.

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----|-----------|
|[Options F# Interactive](../../language-reference/fsharp-interactive-options.md)|Décrit la syntaxe et les options de ligne de commande pour le F# Interactive, fsi.exe.|
