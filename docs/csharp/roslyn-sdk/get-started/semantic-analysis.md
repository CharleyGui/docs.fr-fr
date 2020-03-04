---
title: Bien démarrer avec l’analyse sémantique
description: Ce tutoriel fournit une vue d’ensemble de l’utilisation de l’analyse sémantique avec le SDK du compilateur .NET.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: a6dcaeeb86acb5c0e1602f01dc5952ffd9d5e3f5
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240507"
---
# <a name="get-started-with-semantic-analysis"></a>Bien démarrer avec l’analyse sémantique

Ce tutoriel suppose que vous êtes familiarisé avec l’API Syntaxe. L’article [Bien démarrer avec l’analyse syntaxique](syntax-analysis.md) fournit une introduction suffisante.

Dans ce tutoriel, vous découvrez les API **Symbole** et **Liaison**. Ces API fournissent des informations sur la _signification sémantique_ d’un programme. Elles vous permettent de poser et de répondre à des questions sur les types représentés par un symbole dans votre programme.

Vous devez installer le SDK **.NET Compiler Platform** :

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Présentation des compilations et des symboles

Au fil de votre utilisation du SDK du compilateur .NET, vous allez mieux comprendre les différences entre l’API Syntaxe et l’API Sémantique. **L’API Syntaxe** vous permet d’examiner la _structure_ d’un programme. Cependant, des informations plus détaillées sur la sémantique ou la _signification_ d’un programme sont souvent nécessaires. Même si un fichier de code libre ou un extrait C# de Visual Basic ou du code peut être analysé de manière syntaxique de manière isolée, il n’est pas judicieux de poser des questions telles que « quel est le type de cette variable » dans un vide. La signification d’un nom de type peut dépendre de références d’assembly, d’importations d’espaces de noms ou d’autres fichiers de code. Ces questions sont traitées avec **l’API Sémantique**, plus précisément avec la classe <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType>.

Une instance de <xref:Microsoft.CodeAnalysis.Compilation> est analogue à un projet tel qu’il est vu par le compilateur et représente tout ce qui est nécessaire pour compiler un programme Visual Basic ou C#. La **compilation** comprend l’ensemble des fichiers sources à compiler, les références d’assembly et les options du compilateur. Vous pouvez analyser la signification du code en utilisant toutes les autres informations de ce contexte. Une <xref:Microsoft.CodeAnalysis.Compilation> vous permet de rechercher des **symboles**, qui sont des entités comme des types, des espaces de noms, des membres et des variables, qui sont référencées par des noms et d’autres expressions. Le processus consistant à associer des noms et des expressions à des **symboles** est appelé la **liaison**.

Comme <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> est une classe abstraite avec des dérivés spécifiques à un langage. Quand vous créez une instance de compilation, vous devez appeler une méthode de fabrique sur la classe <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (ou <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>).

## <a name="querying-symbols"></a>Interrogation des symboles

Dans ce tutoriel, vous examinez à nouveau le programme « Hello World ». Cette fois-ci, vous interrogez les symboles du programme pour comprendre quels types ces symboles représentent. Vous interrogez les types dans un espace de noms et vous découvrez comment trouver les méthodes disponibles sur un type.

Vous pouvez trouver le code complet de cet exemple dans [notre dépôt GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Les types de l’arborescence de syntaxe utilisent l’héritage pour décrire les différents éléments de syntaxe qui sont valides à différents emplacements du programme. Utiliser ces API signifie souvent effectuer un cast des propriétés ou des membres de collection vers des types dérivés spécifiques. Dans les exemples suivants, l’affectation et les casts sont des instructions distinctes, qui utilisent des variables typées explicitement. Vous pouvez lire le code pour voir les types de retour de l’API et le type à l’exécution des objets retournés. Dans la pratique, il est plus courant d’utiliser des variables typées implicitement et de se baser sur des noms d’API pour décrire le type des objets examinés.

Créez un projet C# **Outil d’analyse du code autonome** :

* Dans Visual Studio, choisissez **Fichier** > **Nouveau** > **Projet** pour afficher la boîte de dialogue Nouveau projet.
* Sous **Visual C#** > **Extensibilité**, choisissez **Outil d’analyse du code autonome**.
* Nommez votre projet « **SemanticQuickStart** » et cliquez sur OK.

Vous allez analyser le programme simple « Hello World! » montré précédemment.
Ajoutez le texte pour le programme Hello World en tant que constante dans votre classe `Program` :

[!code-csharp[Declare the program test](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Ensuite, ajoutez le code suivant pour générer l’arborescence de syntaxe pour le texte du code dans la constante `programText`.  Ajoutez la ligne suivante à votre méthode `Main` :

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Ensuite, générez une <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> à partir de l’arborescence que vous avez déjà créée. L’exemple « Hello World » est basé sur les types <xref:System.String> et <xref:System.Console>. Vous devez référencer l’assembly qui déclare ces deux types dans votre compilation. Ajoutez la ligne suivante à votre méthode `Main` pour créer une compilation de votre arborescence de syntaxe, en incluant la référence à l’assembly approprié :

[!code-csharp[Create the compilation](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

La méthode <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> ajoute des références à la compilation. La méthode <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> charge un assembly en tant que référence.

## <a name="querying-the-semantic-model"></a>Interrogation du modèle sémantique

Une fois que vous avez une <xref:Microsoft.CodeAnalysis.Compilation>, vous pouvez la demander pour un <xref:Microsoft.CodeAnalysis.SemanticModel> pour n’importe quelle <xref:Microsoft.CodeAnalysis.SyntaxTree> contenue dans <xref:Microsoft.CodeAnalysis.Compilation>. Vous pouvez considérer le modèle sémantique comme étant la source de toutes les informations que vous obtiendriez normalement d’IntelliSense. Un <xref:Microsoft.CodeAnalysis.SemanticModel> peut répondre à des questions comme « Quels noms se trouvent dans l’étendue à cet emplacement ? », « Quels membres sont accessibles à partir de cette méthode ? », « Quelles variables sont utilisées dans ce bloc de texte ? » et « À quoi ce nom ou cette expression font-ils référence ? ». Ajoutez cette instruction pour créer le modèle sémantique :

[!code-csharp[Create the semantic model](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Liaison d’un nom

<xref:Microsoft.CodeAnalysis.Compilation> crée <xref:Microsoft.CodeAnalysis.SemanticModel> à partir de <xref:Microsoft.CodeAnalysis.SyntaxTree>. Après avoir créé le modèle, vous pouvez l’interroger pour rechercher la première directive `using` et récupérer les informations des symboles pour l’espace de noms `System`. Ajoutez ces deux lignes à votre méthode `Main` pour créer le modèle sémantique et pour récupérer le symbole pour la première instruction using :

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Le code précédent montre comment lier le nom dans la première directive `using` pour récupérer un <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> pour l’espace de noms `System`. Le code précédent montre aussi que vous utilisez le **modèle de syntaxe** pour trouver la structure du code ; vous utilisez le **modèle sémantique** pour comprendre sa signification. Le **modèle de syntaxe** recherche la chaîne `System` dans l’instruction using. Le **modèle sémantique** a toutes les informations sur les types définis dans l’espace de noms `System`.

À partir de l’objet <xref:Microsoft.CodeAnalysis.SymbolInfo>, vous pouvez obtenir <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> en utilisant la propriété <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType>. Cette propriété retourne le symbole auquel cette expression fait référence. Pour les expressions qui ne font référence à rien (comme les littéraux numériques), cette propriété est `null`. Quand <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> n’est pas null, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> indique le type du symbole. Dans cet exemple, la propriété <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> est un <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. Ajoutez le code suivant à votre méthode `Main`. Il récupère le symbole pour l’espace de noms `System`, puis affiche tous les espaces de noms enfants déclarés dans l’espace de noms `System` :

[!code-csharp[Display all the child namespaces](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Exécutez le programme ; vous devez normalement voir la sortie suivante :

```output
System.Collections
System.Configuration
System.Deployment
System.Diagnostics
System.Globalization
System.IO
System.Numerics
System.Reflection
System.Resources
System.Runtime
System.Security
System.StubHelpers
System.Text
System.Threading
Press any key to continue . . .
```

> [!NOTE]
> La sortie n’inclut pas chaque espace de noms qui est un espace de noms enfant de l’espace de noms `System`. Elle affiche chaque espace de noms qui est présent dans cette compilation, qui référence seulement l’assembly où `System.String` est déclaré. Les espaces de noms déclarés dans d’autres assemblys ne sont pas connus de cette compilation.

### <a name="binding-an-expression"></a>Liaison d’une expression

Le code précédent montre comment trouver un symbole en le liant à un nom. D’autres expressions existent dans un programme C# qui peuvent être liées, mais qui ne sont pas des noms. Pour montrer cette possibilité, accédons à la liaison vers un littéral de chaîne simple.

Le programme « Hello World » contient un <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, : la chaîne « Hello, World! » affichée dans la console.

Vous trouvez la chaîne « Hello, World! » en recherchant le seul littéral de chaîne dans le programme. Ensuite, une fois que vous avez localisé le nœud de syntaxe, vous obtenez les informations de type pour ce nœud auprès du modèle sémantique. Ajoutez le code suivant à votre méthode `Main` :

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

La struct <xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> inclut une propriété <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> qui permet d’accéder aux informations sémantiques sur le type du littéral. Dans cet exemple, il s’agit du type `string`. Ajoutez une déclaration qui affecte cette propriété à une variable locale :

[!code-csharp[Find the semantic information about the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Pour terminer ce tutoriel, construisons une requête LINQ qui crée une séquence de toutes les méthodes publiques déclarées sur le type `string` qui retournent un type `string`. Cette requête est complexe : nous allons donc la construire ligne par ligne, puis la reconstruire pour former une seule requête. La source de cette requête est la séquence de tous les membres déclarés sur le type `string` :

[!code-csharp[Access the sequence of members on the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Cette séquence source contient tous les membres, notamment les propriétés et les champs ; filtrez-la avec la méthode <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> pour trouver les éléments qui sont des objets <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> :

[!code-csharp[Filter the sequence to only methods](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Ensuite, ajoutez un autre filtre pour retourner seulement les méthodes qui sont publiques et qui retournent un type `string` :

[!code-csharp[Filter on return type and accessibility](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Sélectionnez seulement la propriété name et seulement les noms distincts en supprimant les surcharges :

[!code-csharp[find the distinct names.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Vous pouvez aussi créer toute la requête avec la syntaxe de requête LINQ, puis afficher tous les noms de méthode dans la console :

[!code-csharp[build and display the results of this query.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

Générez et exécutez le programme. Vous devez normalement voir la sortie suivante.

```output
Join
Substring
Trim
TrimStart
TrimEnd
Normalize
PadLeft
PadRight
ToLower
ToLowerInvariant
ToUpper
ToUpperInvariant
ToString
Insert
Replace
Remove
Format
Copy
Concat
Intern
IsInterned
Press any key to continue . . .
```

Vous avez utilisé l’API Sémantique pour rechercher et afficher des informations sur les symboles qui font partie de ce programme.
