---
title: Nouveautés de C# 9,0-Guide C#
description: Profitez d’une vue d’ensemble des nouvelles fonctionnalités disponibles dans C# 9,0.
ms.date: 09/04/2020
ms.openlocfilehash: 57fd5f8775f95b2588e4a7120e35d6d531be4f01
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434829"
---
# <a name="whats-new-in-c-90"></a>Nouveautés dans C# 9.0

C# 9,0 ajoute les fonctionnalités et améliorations suivantes au langage C# :

- [Enregistrements](#record-types)
- [Setter init uniquement](#init-only-setters)
- [Instructions de niveau supérieur](#top-level-statements)
- [Améliorations des critères spéciaux](#pattern-matching-enhancements)
- Entiers dimensionnés natifs
- Pointeurs fonction
- Supprimer l’émission de l’indicateur localsinit
- Nouvelles expressions typées cibles
- fonctions anonymes statiques
- Expressions conditionnelles typées cible
- Types de retour covariant
- `GetEnumerator`Prise en charge des extensions pour les `foreach` boucles
- Paramètres d’abandon lambda
- Attributs sur des fonctions locales
- Initialiseurs de module
- Nouvelles fonctionnalités pour les méthodes partielles

C# 9,0 est pris en charge sur **.net 5**. Pour plus d’informations, consultez contrôle de [version du langage C#](../language-reference/configure-language-version.md).

## <a name="record-types"></a>Types d’enregistrements

C# 9,0 introduit **_types d’enregistrements_*_, qui sont un type référence qui fournit des méthodes synthétisées pour fournir une sémantique de valeur pour l’égalité. Les enregistrements sont immuables par défaut.

Les types d’enregistrements facilitent la création de types référence immuables dans .NET. Historiquement, les types .NET sont largement classés comme types référence (y compris les classes et les types anonymes) et les types valeur (y compris les structs et les tuples). Bien que les types de valeurs immuables soient recommandés, les types valeur mutables n’introduisent pas souvent des erreurs. Les variables de type valeur contiennent les valeurs afin que les modifications soient apportées à une copie des données d’origine lorsque les types valeur sont passés aux méthodes.

Il existe également de nombreux avantages par rapport aux types de référence immuables. Ces avantages sont plus prononcés dans les programmes simultanés avec des données partagées. Malheureusement, C# vous obligeait à écrire un peu de code supplémentaire pour créer des types de référence immuables. Les enregistrements fournissent une déclaration de type pour un type référence immuable qui utilise une sémantique de valeur pour l’égalité. Les méthodes synthétisées pour l’égalité et les codes de hachage considèrent deux enregistrements comme égaux si leurs propriétés sont toutes égales. Tenez compte de cette définition :

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="RecordDefinition":::

La définition d’enregistrement crée un `Person` type qui contient deux propriétés ReadOnly : `FirstName` et `LastName` . Le `Person` type est un type référence. Si vous avez regardé le langage intermédiaire, il s’agit d’une classe. Elle est immuable dans la mesure où aucune des propriétés ne peut être modifiée une fois qu’elle a été créée. Lorsque vous définissez un type d’enregistrement, le compilateur synthétise plusieurs autres méthodes pour vous :

- Méthodes pour les comparaisons d’égalité basées sur des valeurs
- Remplacer pour <xref:System.Object.GetHashCode>
- Copier et cloner des membres
- `PrintMembers` et <xref:System.Object.ToString>

Les enregistrements prennent en charge l’héritage. Vous pouvez déclarer un nouvel enregistrement dérivé de `Person` comme suit :

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="InheritedRecord":::

Vous pouvez également sceller les enregistrements pour éviter toute dérivation supplémentaire :

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="SealedRecord":::

Le compilateur synthétise différentes versions des méthodes ci-dessus. Les signatures de méthode dépendent de si le type d’enregistrement est sealed et si la classe de base directe est Object. Les enregistrements doivent avoir les fonctionnalités suivantes :

- L’égalité est basée sur la valeur et comprend une vérification de la correspondance des types. Par exemple, un `Student` ne peut pas être égal à un `Person` , même si les deux enregistrements partagent le même nom.
- Une représentation sous forme de chaîne cohérente est générée pour les enregistrements.
- Les enregistrements prennent en charge la construction de copie. La bonne construction de copie doit inclure des hiérarchies d’héritage et des propriétés ajoutées par les développeurs.
- Les enregistrements peuvent être copiés avec modification. Ces opérations de copie et de modification prennent en charge la mutation non destructrice.

En plus des `Equals` surcharges familières, `operator ==` et `operator !=` , le compilateur synthétise une nouvelle `EqualityContract` propriété. La propriété retourne un `Type` objet qui correspond au type de l’enregistrement. Si le type de base est `object` , la propriété est `virtual` . Si le type de base est un autre type d’enregistrement, la propriété est un `override` . Si le type d’enregistrement est `sealed` , la propriété est `sealed` . La synthèse `GetHashCode` utilise le `GetHashCode` de toutes les propriétés et les champs déclarés dans le type de base et le type d’enregistrement. Ces méthodes synthétisées appliquent l’égalité basée sur les valeurs dans une hiérarchie d’héritage. Cela signifie qu’un `Student` ne sera jamais considéré comme égal à un `Person` portant le même nom. Les types des deux enregistrements doivent correspondre, et toutes les propriétés partagées entre les types d’enregistrements sont égales.

Les enregistrements ont également un constructeur synthétisé et une méthode de clonage pour créer des copies. Le constructeur synthétisé a un argument du type d’enregistrement. Il génère un nouvel enregistrement avec les mêmes valeurs pour toutes les propriétés de l’enregistrement. Ce constructeur est privé si l’enregistrement est sealed, sinon il est protégé. La méthode « Clone » synthétisée prend en charge la construction de copie pour les hiérarchies d’enregistrement. Le terme « clone » est placé entre guillemets, car le nom réel est généré par le compilateur. Vous ne pouvez pas créer une méthode nommée `Clone` dans un type d’enregistrement. La méthode « Clone » synthétisée renvoie le type d’enregistrement copié à l’aide de la répartition virtuelle. Le compilateur ajoute des modificateurs différents pour la méthode « Clone » en fonction des modificateurs d’accès sur le `record` :

- Si le type d’enregistrement est `abstract` , la méthode « Clone » est également `abstract` . Si le type de base n’est pas `object` , la méthode est également `override` .
- Pour les types d’enregistrements qui ne sont pas `abstract` lorsque le type de base est `object` :
  - Si l’enregistrement est `sealed` , aucun modificateur supplémentaire n’est ajouté à la méthode « Clone » (ce qui signifie qu’il ne l’est pas `virtual` ).
  - Si l’enregistrement n’est pas `sealed` , la méthode « Clone » est `virtual` .
- Pour les types d’enregistrements qui ne sont `abstract` pas lorsque le type de base n’est pas `object` :
  - Si l’enregistrement est `sealed` , la méthode « Clone » est également `sealed` .
  - Si l’enregistrement n’est pas `sealed` , la méthode « Clone » est `override` .

Le résultat de toutes ces règles est l’égalité est implémentée de manière cohérente dans n’importe quelle hiérarchie de types d’enregistrements. Deux enregistrements sont égaux si leurs propriétés sont égales et que leurs types sont identiques, comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="RecordsEquality":::

Le compilateur synthétise deux méthodes qui prennent en charge la sortie imprimée : une <xref:System.Object.ToString> substitution et `PrintMembers` . `PrintMembers`Prend <xref:System.Text.StringBuilder?displayProperty=nameWithType> comme argument. Elle ajoute une liste séparée par des virgules de noms et de valeurs de propriété pour toutes les propriétés du type d’enregistrement. `PrintMembers` appelle l’implémentation de base pour tous les enregistrements dérivés d’autres enregistrements. La <xref:System.Object.ToString> substitution retourne la chaîne produite par `PrintMembers` , entourée de `{` et de `}` . Par exemple, la <xref:System.Object.ToString> méthode pour `Student` retourne un `string` semblable au code suivant :

```csharp
"Student { LastName = Wagner, FirstName = Bill, Level = 11 }"
```

Les exemples indiqués jusqu’à présent utilisent la syntaxe traditionnelle pour déclarer des propriétés. Il existe une forme plus concise appelée _*_enregistrements positionnels_*_.  Voici les trois types d’enregistrements définis précédemment en tant qu’enregistrements positionnels :

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="PositionalRecords":::

Ces déclarations créent les mêmes fonctionnalités que la version antérieure (avec quelques fonctionnalités supplémentaires décrites dans la section suivante). Ces déclarations se terminent par un point-virgule au lieu de crochets, car ces enregistrements n’ajoutent pas de méthodes supplémentaires. Vous pouvez ajouter un corps et inclure également des méthodes supplémentaires :

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="RecordsWithMethods":::

Le compilateur produit une `Deconstruct` méthode pour les enregistrements positionnels. La `Deconstruct` méthode a des paramètres qui correspondent aux noms de toutes les propriétés publiques dans le type d’enregistrement. La `Deconstruct` méthode peut être utilisée pour déconstruire l’enregistrement dans ses propriétés de composant :

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="DeconstructRecord":::

Enfin, les enregistrements prennent en charge _*_les expressions-_*_. Une instruction _*_with-expression_*_ demande au compilateur de créer une copie d’un enregistrement, mais les propriétés spécifiées _with * sont modifiées :

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="Wither":::

La ligne ci-dessus crée un nouvel `Person` enregistrement où la `LastName` propriété est une copie de `person` , et le `FirstName` est « Paul ». Vous pouvez définir n’importe quel nombre de propriétés dans une expression with.  Tous les membres synthétisés, à l’exception de la méthode « Clone », peuvent être écrits par vous-même. Si un type d’enregistrement a une méthode qui correspond à la signature d’une méthode synthétisée, le compilateur ne synthétise pas cette méthode. L' `Dog` exemple d’enregistrement précédent contient une méthode codée à la main <xref:System.String.ToString> à titre d’exemple.

## <a name="init-only-setters"></a>Setter init uniquement

*Les **Setters init uniquement**_ fournissent une syntaxe cohérente pour initialiser les membres d’un objet. Les initialiseurs de propriété permettent de savoir clairement quelle valeur définit la propriété. L’inconvénient est que ces propriétés doivent pouvoir être définies. À compter de C# 9,0, vous pouvez créer des `init` accesseurs au lieu d' `set` accesseurs pour les propriétés et les indexeurs. Les appelants peuvent utiliser la syntaxe de l’initialiseur de propriété pour définir ces valeurs dans les expressions de création, mais ces propriétés sont en lecture seule une fois que la construction est terminée. Les Setters init uniquement fournissent une fenêtre pour modifier l’État. Cette fenêtre se ferme à la fin de la phase de construction. La phase de construction se termine effectivement après toute initialisation, y compris les initialiseurs de propriété et les expressions with-.

L’exemple précédent pour les enregistrements positionnels illustre l’utilisation d’un accesseur Set init-only pour définir une propriété à l’aide d’une expression with. Vous pouvez déclarer des accesseurs set init uniquement dans n’importe quel type que vous écrivez. Par exemple, le struct suivant définit une structure d’observation météorologique :

:::code language="csharp" source="snippets/whats-new-csharp9/WeatherObservation.cs" ID="DeclareWeatherObservation":::

Les appelants peuvent utiliser la syntaxe de l’initialiseur de propriété pour définir les valeurs, tout en préservant l’immuabilité :

:::code language="csharp" source="snippets/whats-new-csharp9/WeatherObservation.cs" ID="UseWeatherObservation":::

Toutefois, la modification d’une observation après l’initialisation est une erreur en affectant à une propriété init-only en dehors de l’initialisation :

```csharp
// Error! CS8852.
now.TemperatureInCelsius = 18;
```

Les Setters init uniquement peuvent être utiles pour définir des propriétés de classe de base à partir de classes dérivées. Ils peuvent également définir des propriétés dérivées par le biais d’assistances dans une classe de base. Les enregistrements positionnels déclarent des propriétés à l’aide des accesseurs set init only. Ces accesseurs set sont utilisés dans les expressions with. Vous pouvez déclarer des Setters init uniquement pour n’importe quel `class` ou `struct` vous définissez.

## <a name="top-level-statements"></a>Instructions de niveau supérieur

_*_Les instructions de niveau supérieur_*_ suppriment la cérémonie inutile de nombreuses applications. Prenons le « Hello World ! » canonique. table

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

Il n’y a qu’une seule ligne de code qui fait quoi que ce soit. Avec les instructions de niveau supérieur, vous pouvez remplacer tout ce qui est réutilisable par l' `using` instruction et la ligne unique qui effectue le travail :

:::code language="csharp" source="snippets/whats-new-csharp9/Program.cs" ID="TopLevelStatements":::

Si vous souhaitez un programme à une seule ligne, vous pouvez supprimer la `using` directive et utiliser le nom de type complet :

```csharp
System.Console.WriteLine("Hello World!");
```

Un seul fichier de votre application peut utiliser des instructions de niveau supérieur. Si le compilateur trouve des instructions de niveau supérieur dans plusieurs fichiers sources, il s’agit d’une erreur. C’est également une erreur si vous combinez des instructions de niveau supérieur avec une méthode de point d’entrée de programme déclarée, généralement une `Main` méthode. Dans un sens, vous pouvez penser qu’un fichier contient les instructions qui seraient normalement dans la `Main` méthode d’une `Program` classe.  

L’une des utilisations les plus courantes de cette fonctionnalité est la création de documents pédagogiques. Les développeurs C# débutants peuvent écrire le « Hello World ! » canonique dans une ou deux lignes de code. Aucune des cérémonie supplémentaires n’est nécessaire. Toutefois, les développeurs chevronnés trouveront de nombreuses utilisations pour cette fonctionnalité également. Les instructions de niveau supérieur permettent une expérience de type script pour les expérimentations similaires à celles fournies par les blocs-notes Jupyter. Les instructions de niveau supérieur sont idéales pour les petits programmes et utilitaires de console. Azure Functions est un cas d’usage idéal pour les instructions de niveau supérieur.

Plus important encore, les instructions de niveau supérieur ne limitent pas la portée ou la complexité de votre application. Ces instructions peuvent accéder ou utiliser n’importe quelle classe .NET. Ils ne limitent pas non plus l’utilisation des arguments de ligne de commande ou des valeurs de retour. Les instructions de niveau supérieur peuvent accéder à un tableau de chaînes nommées args. Si les instructions de niveau supérieur retournent une valeur entière, cette valeur devient le code de retour de l’entier d’une méthode synthétisée `Main` . Les instructions de niveau supérieur peuvent contenir des expressions Async. Dans ce cas, le point d’entrée synthétisé retourne un `Task` , ou `Task<int>` .

## <a name="pattern-matching-enhancements"></a>Améliorations des critères spéciaux

C# 9 comprend de nouvelles améliorations de la mise en correspondance des modèles :

- Les _*_modèles de type_*_ correspondent à une variable est un type
- Les _*_modèles entre parenthèses_*_ appliquent ou mettent en évidence la précédence des combinaisons de modèles
- _*_Les `and` modèles conjonctives_*_ nécessitent que les deux modèles correspondent
- _*_Les `or` modèles disjonctive_*_ nécessitent un modèle de correspondance
- Les _*_ `not` modèles de négation_*_ requièrent qu’un modèle ne corresponde pas
- Les _*_modèles relationnels_*_ requièrent que l’entrée soit inférieure à, supérieure à, inférieure ou égale à une constante donnée, ou supérieure ou égale à celle-ci.

Ces modèles enrichissent la syntaxe des modèles. Prenons les exemples suivants :

:::code language="csharp" source="snippets/whats-new-csharp9/PatternUtilities.cs" ID="IsLetterPattern":::

En guise d’alternative, avec des parenthèses facultatives pour qu’elle soit claire et qu’elle `and` a une priorité plus élevée que `or` :

:::code language="csharp" source="snippets/whats-new-csharp9/PatternUtilities.cs" ID="IsLetterOrSeparatorPattern":::

L’une des utilisations les plus courantes est une nouvelle syntaxe pour un contrôle de valeur NULL :

```csharp
if (e is not null)
{
    // ...
}
```

L’un de ces modèles peut être utilisé dans n’importe quel contexte où les modèles sont autorisés : `is` les expressions de modèle, les `switch` expressions, les modèles imbriqués et le modèle de l’étiquette d’une `switch` instruction `case` .

## <a name="performance-and-interop"></a>Performances et interopérabilité

Trois nouvelles fonctionnalités améliorent la prise en charge de l’interopérabilité native et des bibliothèques de bas niveau qui requièrent des performances élevées : les entiers de taille native, les pointeurs de fonction et l’omission de l' `localsinit` indicateur.

Les entiers de taille native, `nint` et `nuint` , sont des types entiers. Elles sont exprimées par les types sous-jacents <xref:System.IntPtr?displayProperty=nameWithType> et <xref:System.UIntPtr?displayProperty=nameWithType> . Le compilateur recadre les conversions et les opérations supplémentaires pour ces types comme des ints natifs. Les entiers de taille native définissent des propriétés pour `MaxValue` ou `MinValue` . Ces valeurs ne peuvent pas être exprimées comme des constantes de compilation, car elles dépendent de la taille native d’un entier sur l’ordinateur cible. Ces valeurs sont en lecture seule au moment de l’exécution. Vous pouvez utiliser des valeurs constantes pour `nint` dans la plage [ `int.MinValue` .. `int.MaxValue`]. Vous pouvez utiliser des valeurs constantes pour `nuint` dans la plage [ `uint.MinValue` .. `uint.MaxValue`]. Le compilateur exécute un repli constant pour tous les opérateurs unaires et binaires à l’aide des <xref:System.Int32?displayProperty=nameWithType> <xref:System.UInt32?displayProperty=nameWithType> types et. Si le résultat ne tient pas dans 32 bits, l’opération est exécutée au moment de l’exécution et n’est pas considérée comme une constante. Les entiers de taille native peuvent augmenter les performances dans les scénarios où les calculs d’entiers sont largement utilisés et doivent avoir les performances les plus rapides possibles.

Les pointeurs fonction fournissent une syntaxe simple pour accéder aux opcodes IL `ldftn` et `calli` . Vous pouvez déclarer des pointeurs de fonction à l’aide de la nouvelle `delegate_` syntaxe. Un `delegate*` type est un type pointeur. L’appel du `delegate*` type utilise `calli` , contrairement à un délégué qui utilise `callvirt` sur la `Invoke()` méthode. Syntaxiquement, les appels sont identiques. L’appel du pointeur de fonction utilise la `managed` Convention d’appel. Vous ajoutez le `unmanaged` mot clé après la `delegate*` syntaxe pour déclarer que vous souhaitez la `unmanaged` Convention d’appel. D’autres conventions d’appel peuvent être spécifiées à l’aide d’attributs sur la `delegate*` déclaration.

Enfin, vous pouvez ajouter le <xref:System.Runtime.CompilerServices.SkipLocalsInitAttribute?displayProperty=nameWithType> pour indiquer au compilateur de ne pas émettre l' `localsinit` indicateur. Cet indicateur indique au CLR d’initialiser à zéro toutes les variables locales. L' `localsinit` indicateur a été le comportement par défaut pour C# depuis 1,0. Toutefois, l’initialisation sans zéro supplémentaire peut avoir un impact mesurable sur les performances dans certains scénarios. En particulier, lorsque vous utilisez `stackalloc` . Dans ce cas, vous pouvez ajouter le <xref:System.Runtime.CompilerServices.SkipLocalsInitAttribute> . Vous pouvez l’ajouter à une méthode ou une propriété unique, ou à un `class` , `struct` , `interface` ou même un module. Cet attribut n’affecte pas `abstract` les méthodes ; il affecte le code généré pour l’implémentation.

Ces fonctionnalités peuvent améliorer les performances dans certains scénarios. Elles doivent être utilisées uniquement après un test minutieux avant et après l’adoption. Le code impliquant des entiers de taille native doit être testé sur plusieurs plateformes cibles avec différentes tailles d’entier. Les autres fonctionnalités nécessitent du code non sécurisé.

## <a name="fit-and-finish-features"></a>Fonctionnalités d’ajustement et de fin

La plupart des autres fonctionnalités vous aident à écrire du code plus efficacement. En C# 9,0, vous pouvez omettre le type dans une [ `new` expression](../language-reference/operators/new-operator.md) lorsque le type de l’objet créé est déjà connu. L’utilisation la plus courante est dans les déclarations de champ :

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="WeatherStationField":::

Le type cible `new` peut également être utilisé lorsque vous devez créer un nouvel objet à passer en tant qu’argument à une méthode. Envisagez une `ForecastFor()` méthode avec la signature suivante :

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="ForecastSignature":::

Vous pouvez l’appeler comme suit :

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="TargetTypeNewArgument":::

Une autre utilisation intéressante de cette fonctionnalité est de l’associer aux propriétés init only pour initialiser un nouvel objet :

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="InitWeatherStation":::

Vous pouvez retourner une instance créée par le constructeur par défaut à l’aide d’une `return new();` instruction.

Une fonctionnalité similaire améliore la résolution de type cible des [expressions conditionnelles](../language-reference/operators/conditional-operator.md). Avec cette modification, les deux expressions n’ont pas besoin d’une conversion implicite de l’une à l’autre, mais elles peuvent toutes deux avoir des conversions implicites en un type cible. Vous ne remarquerez probablement pas cette modification. Ce que vous remarquerez, c’est que certaines expressions conditionnelles qui nécessitaient auparavant des casts ou ne seraient pas compilées.

À compter de C# 9,0, vous pouvez ajouter le `static` modificateur aux [expressions lambda](../language-reference/operators/lambda-expressions.md) ou aux [méthodes anonymes](../language-reference/operators/delegate-operator.md). Les expressions lambda statiques sont analogues aux `static` fonctions locales : une méthode lambda statique ou anonyme ne peut pas capturer les variables locales ou l’état de l’instance. Le `static` modificateur empêche la capture accidentelle d’autres variables.

Les types de retour covariants fournissent la flexibilité pour les types de retour des méthodes [override](../language-reference/keywords/override.md) . Une méthode override peut retourner un type dérivé du type de retour de la méthode de base substituée. Cela peut être utile pour les enregistrements et pour d’autres types qui prennent en charge les méthodes de fabrique ou de clonage virtuel.

En outre, la [ `foreach` boucle](../language-reference/keywords/foreach-in.md) reconnaît et utilise une méthode d’extension `GetEnumerator` qui, autrement, satisfait le `foreach` modèle. Ce changement signifie `foreach` qu’il est cohérent avec d’autres constructions basées sur des modèles, telles que le modèle asynchrone et la déconstruction basée sur des modèles. Dans la pratique, cette modification signifie que vous pouvez ajouter la `foreach` prise en charge à n’importe quel type. Vous devez limiter son utilisation à lorsque l’énumération d’un objet est logique dans votre conception.

Ensuite, vous pouvez utiliser des éléments ignorés comme paramètres pour les expressions lambda. Cela vous permet d’éviter de nommer l’argument et le compilateur peut ne pas l’utiliser. Vous utilisez `_` pour n’importe quel argument. Pour plus d’informations, consultez la section [paramètres d’entrée d’une expression lambda](../language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression) de l’article [expressions lambda](../language-reference/operators/lambda-expressions.md) .

Enfin, vous pouvez maintenant appliquer des attributs à des [fonctions locales](../programming-guide/classes-and-structs/local-functions.md). Par exemple, vous pouvez appliquer des [annotations d’attribut Nullable](../language-reference/attributes/nullable-analysis.md) aux fonctions locales.

## <a name="support-for-code-generators"></a>Prise en charge des générateurs de code

Deux fonctionnalités finales prennent en charge les générateurs de code C#. Les générateurs de code C# sont un composant que vous pouvez écrire et qui est semblable à un Roslyn Analyzer ou à un correctif de code. La différence est que les générateurs de code analysent le code et écrivent de nouveaux fichiers de code source dans le cadre du processus de compilation. Un générateur de code standard recherche des attributs ou d’autres conventions dans le code.

Un générateur de code lit des attributs ou d’autres éléments de code à l’aide des API d’analyse Roslyn. À partir de ces informations, il ajoute un nouveau code à la compilation. Les générateurs de source peuvent uniquement ajouter du code ; ils ne sont pas autorisés à modifier le code existant dans la compilation.

Les deux fonctionnalités ajoutées pour les générateurs de code sont les extensions de la**syntaxe de méthode partielle**_ et les _*_initialiseurs de module_*_. Tout d’abord, les modifications apportées aux méthodes partielles. Avant C# 9,0, les méthodes partielles sont, `private` mais ne peuvent pas spécifier un modificateur d’accès, ont un `void` retour et ne peuvent pas avoir de `out` paramètres. Ces restrictions signifiaient que si aucune implémentation de méthode n’est fournie, le compilateur supprime tous les appels à la méthode partielle. C# 9,0 supprime ces restrictions, mais exige que les déclarations de méthode partielles aient une implémentation. Les générateurs de code peuvent fournir cette implémentation. Pour éviter d’introduire une modification avec rupture, le compilateur considère toute méthode partielle sans modificateur d’accès pour suivre les anciennes règles. Si la méthode partielle comprend le `private` modificateur d’accès, les nouvelles règles gouvernent cette méthode partielle.

La deuxième nouvelle fonctionnalité pour les générateurs de code est _ *_initialiseurs de module_* *. Les initialiseurs de module sont des méthodes auxquelles l' <xref:System.Runtime.CompilerServices.ModuleInitializerAttribute> attribut est attaché. Ces méthodes sont appelées par le runtime lors du chargement de l’assembly. Méthode d’initialiseur de module :

- Doit être statique
- Doit être sans paramètre
- Doit retourner void
- Ne doit pas être une méthode générique
- Ne doit pas être contenu dans une classe générique
- Doit être accessible à partir du module conteneur

Ce dernier point à puce signifie effectivement que la méthode et sa classe conteneur doivent être internes ou publiques. La méthode ne peut pas être une fonction locale.
