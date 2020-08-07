---
title: Options interactives
description: En savoir plus sur les options de ligne de commande prises en charge par F# Interactive, fsi.exe.
ms.date: 07/22/2020
ms.openlocfilehash: abddd1fd990be18ede139ab26ffe80513ba6e0dd
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855346"
---
# <a name="f-interactive-options"></a>Options de F# Interactive

Cet article décrit les options de ligne de commande prises en charge par F# Interactive, `fsi.exe` . F# Interactive accepte un grand nombre des mêmes options de ligne de commande que le compilateur F #, mais il accepte également quelques options supplémentaires.

## <a name="use-f-interactive-for-scripting"></a>Utiliser F# Interactive pour l’écriture de scripts

F# Interactive, `dotnet fsi` , peut être lancé de manière interactive ou peut être lancé à partir de la ligne de commande pour exécuter un script. La syntaxe de la ligne de commande est

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

L’extension de fichier pour les fichiers de script F # est `.fsx` .

## <a name="table-of-f-interactive-options"></a>Tableau des options de F# Interactive

Le tableau suivant récapitule les options prises en charge par F# Interactive. Vous pouvez définir ces options sur la ligne de commande ou à l’aide de l’IDE de Visual Studio. Pour définir ces options dans l’IDE de Visual Studio, ouvrez le menu **Outils** , sélectionnez **options**, développez le nœud **Outils F #** , puis sélectionnez **F# Interactive**.

Quand des listes apparaissent dans F# Interactive arguments de l’option, les éléments de liste sont séparés par des points-virgules ( `;` ).

|Option|Description|
|------|-----------|
|**--**|Permet d’indiquer à F# Interactive de traiter les arguments restants comme des arguments de ligne de commande pour le programme ou le script F #, auquel vous pouvez accéder dans le code à l’aide de la liste **FSI. CommandLineArgs**.|
|**--activé**[ **+**&#124;**-** ]|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--CodePage : &lt; int&gt;**|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--consolecolors**[ **+**&#124;**-** ]|Génère des messages d’avertissement et d’erreur en couleur.|
|**--crossoptimize**[ **+**&#124;**-** ]|Activez ou désactivez les optimisations entre modules.|
|**--Déboguer**[ **+**&#124;**-** ]<br /><br />**--Debug :**[**full**&#124;**pdbonly**&#124;**portable**&#124;**Embedded**]<br /><br />**-g**[ **+**&#124;**-** ]<br /><br />**-g :**[**full**&#124;**pdbonly**&#124;**portable**&#124;**Embedded**]|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--define : &lt; chaîne&gt;**|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--déterministe**[ **+**&#124;**-** ]|Produit un assembly déterministe (y compris le GUID de la version du module et l’horodateur).|
|**--exec**|Ordonne à F # interactive de se fermer après le chargement des fichiers ou l’exécution du fichier de script spécifié sur la ligne de commande.|
|**--fullpaths**|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--GUI**[ **+**&#124;**-** ]|Active ou désactive la boucle d’événements Windows Forms. Il est activé par défaut.|
|**--aide**<br /><br />**-?**|Utilisé pour afficher la syntaxe de la ligne de commande et une brève description de chaque option.|
|**--lib : &lt; Folder-List&gt;**<br /><br />**-I : &lt; dossier-liste&gt;**|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--Load : &lt; nom de fichier&gt;**|Compile le code source donné au démarrage et charge les constructions F # compilées dans la session. Si la source cible contient des directives de script telles que **#use** ou **#load**, vous devez utiliser **--use** ou **#use** à la place de **--Load** ou **#load**.|
|**--mlcompatibility**|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--noframework**|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez [Options du compilateur](compiler-options.md)|
|**--nologo**|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--nowarn : &lt; Avertissement-liste&gt;**|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--optimize**[ **+**&#124;**-** ]|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--preferreduilang : &lt; lang&gt;**| Spécifie le nom de culture de la langue de sortie par défaut (par exemple, es-ES, ja-JP). |
|**--quiet**|Supprime la sortie de F# Interactive dans le flux **stdout** .|
|**--Quotations-débogage**|Spécifie que des informations de débogage supplémentaires doivent être émises pour les expressions dérivées des littéraux de quotation F # et des définitions réfléchies. Les informations de débogage sont ajoutées aux attributs personnalisés d’un nœud d’arborescence d’expression F #. Consultez [Quotations de code](code-quotations.md) et [expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--ReadLine**[ **+**&#124;**-** ]|Activez ou désactivez la saisie semi-automatique par tabulation en mode interactif.|
|**--Référence : &lt; nom de fichier&gt;**<br /><br />**-r : &lt; nom_fichier&gt;**|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--tailcalls**[ **+**&#124;**-** ]|Activez ou désactivez l’utilisation de l’instruction IL tail, qui entraîne la réutilisation du frame de pile pour les fonctions récursives tail. Cette option est activée par défaut.|
|**--TargetProfile : &lt; chaîne&gt;**|Spécifie le profil du Framework cible de cet assembly. Les valeurs valides sont `mscorlib`, `netcore` ou `netstandard`. Par défaut, il s’agit de `mscorlib`.|
|**--Use : &lt; nom_fichier&gt;**|Indique à l’interpréteur d’utiliser le fichier donné au démarrage comme entrée initiale.|
|**--utf8output**|Identique à l’option du compilateur fsc.exe. Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--Warn : &lt; Warning-niveau&gt;**|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--warnaserror**[ **+**&#124;**-** ]|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|
|**--warnaserror**[ **+**&#124;**-** ] :** &lt; int-List &gt; **|Identique à l’option du compilateur **fsc.exe** . Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).|

## <a name="f-interactive-structured-printing"></a>F# Interactive l’impression structurée

F# Interactive ( `dotnet fsi` ) utilise une version étendue de la [mise en forme de texte brut structurée](plaintext-formatting.md) pour les valeurs de rapport.

1. Toutes les fonctionnalités de `%A` mise en forme de texte brut sont prises en charge, et d’autres sont personnalisables.

2. L’impression est colorée si les couleurs sont prises en charge par la console de sortie.

3. Une limite est placée sur la longueur des chaînes affichées, sauf si vous évaluez explicitement cette chaîne.

4. Un ensemble de paramètres définissables par l’utilisateur est disponible via l' `fsi` objet.

Les paramètres disponibles pour personnaliser l’impression en texte brut pour les valeurs signalées sont :

```fsharp
open System.Globalization

fsi.FormatProvider <- CultureInfo("de-DE")  // control the default culture for primitives

fsi.PrintWidth <- 120        // Control the width used for structured printing

fsi.PrintDepth <- 10         // Control the maximum depth of nested printing

fsi.PrintLength <- 10        // Control the length of lists and arrays

fsi.PrintSize <- 100         // Control the maximum overall object count

fsi.ShowProperties <- false  // Control whether properties of .NET objects are shown by default

fsi.ShowIEnumerable <- false // Control whether sequence values are expanded by default

fsi.ShowDeclarationValues <- false // Control whether values are shown for declaration outputs
```

### <a name="customize-with-addprinter-and-addprinttransformer"></a>Personnaliser avec `AddPrinter` et`AddPrintTransformer`

L’impression dans F# Interactive sorties peut être personnalisée à l’aide `fsi.AddPrinter` de et de `fsi.AddPrintTransformer` .
La première fonction donne du texte pour remplacer l’impression d’un objet. La deuxième fonction retourne un objet de substitution à afficher à la place. Par exemple, considérez le code F # suivant :

```fsharp
open System

fsi.AddPrinter<DateTime>(fun dt -> dt.ToString("s"))

type DateAndLabel =
    { Date: DateTime
      Label: string  }

let newYearsDay1999 =
    { Date = DateTime(1999, 1, 1)
      Label = "New Year" }
```

Si vous exécutez l’exemple dans F# Interactive, il est en sortie en fonction de l’option de mise en forme définie. Dans ce cas, il affecte la mise en forme de la date et de l’heure :

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

`fsi.AddPrintTransformer`peut être utilisé pour fournir un objet de substitution pour l’impression :

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

Voici les résultats :

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

Si la fonction de transformateur est passée à `fsi.AddPrintTransformer` returns `null` , le transformateur d’impression est ignoré.
Cela peut être utilisé pour filtrer toute valeur d’entrée en commençant par le type `obj` .  Par exemple :

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

Voici les résultats :

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----|-----------|
|[Options du compilateur](compiler-options.md)|Décrit les options de ligne de commande disponibles pour le compilateur F #, **fsc.exe**.|
