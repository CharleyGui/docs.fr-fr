---
title: Bien démarrer avec l’analyse de la syntaxe (API Roslyn)
description: Une introduction à la façon de parcourir et d’interroger les arborescences de syntaxe.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: 8b9dd909a83877755dc1ebafd58aae892e460b93
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756154"
---
# <a name="get-started-with-syntax-analysis"></a>Bien démarrer avec l’analyse de la syntaxe

Dans ce tutoriel, vous allez explorer **l’API Syntaxe**. L’API Syntaxe fournit un accès aux structures de données qui décrivent un programme C# ou Visual Basic. Ces structures de données ont suffisamment d’informations détaillées pour pouvoir représenter entièrement n’importe quel programme, quelle que soit sa taille. Ces structures peuvent décrire des programmes complets qui se compilent et s’exécutent correctement. Elles peuvent aussi décrire des programmes incomplets, au fil de leur écriture dans l’éditeur.

Pour permettre cette expression détaillée, les structures de données et les API qui composent l’API Syntaxe sont nécessairement complexes. Commençons par ce à quoi ressemble la structure de données pour le programme habituel « Hello World » :

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

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

Considérez le texte du programme précédent. Vous reconnaissez des éléments familiers. Le texte entier représente un même fichier source, ou une **unité de compilation**. Les trois premières lignes de ce fichier source sont des **directives using**. Le reste de la source est contenue dans une **déclaration d’espace de noms**. La déclaration d’espace de noms contient une **déclaration de classe** enfant. La déclaration de classe contient une **déclaration de méthode**.

L’API Syntaxe crée une arborescence dont la racine représente l’unité de compilation. Les nœuds de l’arborescence représentent les directives using, la déclaration d’espace de noms et tous les autres éléments du programme. L’ arborescence continue jusqu’aux niveaux les plus bas : la chaîne « Hello World! » est un **jeton de littéral de chaîne** qui est un descendant d’un **argument**. L’API Syntaxe fournit l’accès à la structure du programme. Vous pouvez rechercher des utilisations spécifiques du code, parcourir toute l’arborescence pour comprendre le code et créer des arborescences en modifiant l’arborescence existante.

Cette brève description fournit une vue d’ensemble des types d’informations accessibles avec l’API Syntaxe. L’API Syntaxe n’est rien de plus qu’une API formelle qui décrit les constructions de code familières que vous connaissez en C#. Les fonctionnalités complètes incluent des informations sur la façon dont le code est mis en forme, notamment les sauts de ligne, les espaces et l’indentation. Avec ces informations, vous pouvez représenter entièrement le code comme étant écrit et lu par des programmeurs ou par le compilateur. L’utilisation de cette structure vous permet d’interagir avec le code source à un niveau qui est vraiment significatif. Il ne s’agit plus de chaînes de texte, mais de données qui représentent la structure d’un programme C#.

Pour commencer, vous devez installer le kit **.NET Compiler Platform SDK** :

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Présentation des arborescences de syntaxe

Vous utilisez l’API Syntaxe pour les analyses de la structure du code C#. **L’API Syntaxe** expose les analyseurs, les arborescences de syntaxe, et des utilitaires pour l’analyse et la construction d’arborescences de syntaxe. C’est ainsi que vous recherchez le code pour des éléments de syntaxe spécifiques ou que vous lisez le code d’un programme.

Une arborescence de syntaxe est une structure de données utilisée par les compilateurs C# et Visual Basic pour comprendre les programmes C# et Visual Basic. Les arborescences de syntaxe sont produites par le même analyseur que celui qui s’exécute quand un projet est généré ou qu’un développeur appuie sur F5. Les arborescences de syntaxe sont parfaitement fidèles au langage : chaque élément d’information d’un fichier de code est représenté dans l’arborescence. L’écriture d’une arborescence de syntaxe en texte reproduit le texte d’origine exact qui a été analysé. Les arborescences de syntaxe sont également **immuables** : une fois créée, une arborescence de syntaxe ne peut jamais être modifiée. Les consommateurs des arborescences peuvent les analyser sur plusieurs threads, sans verrous ou d’autres mesures liées à la simultanéité des accès, sachant que les données ne changent jamais. Vous pouvez utiliser des API pour créer des arborescences qui sont le résultat de la modification d’une arborescence existante.

Les quatre principaux blocs de construction des arborescences de syntaxe sont :

* La classe <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, une instance de celle-ci représentant une arborescence d’analyse entière. <xref:Microsoft.CodeAnalysis.SyntaxTree> est une classe abstraite avec des dérivés spécifiques à un langage. Vous utilisez les méthodes parse de la <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> classe (ou <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType> ) pour analyser le texte en C# (ou Visual Basic).
* La classe <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>, dont les instances représentent des constructions syntaxiques, comme des déclarations, des instructions, des clauses et des expressions.
* La structure <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType>, qui représente un mot clé, un identificateur, un opérateur ou un signe de ponctuation individuel.
* Enfin, la structure <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType>, qui représente les éléments d’information non significatifs du point de vue syntaxique, comme l’espace entre des jetons, des directives de prétraitement et des commentaires.

Tout cela, les jetons et les nœuds sont composés de façon hiérarchique pour former une arborescence représentant complètement tous les éléments d’un fragment de code Visual Basic ou C#. Vous pouvez voir cette structure en utilisant la fenêtre **Visualiseur de syntaxe**. Dans Visual Studio, choisissez **Afficher**  >  **les autres**  >  **Syntax Visualizer**Windows. Par exemple, le fichier source C# précédent examiné avec le **Visualiseur de syntaxe** se présente comme dans la figure suivante :

**SyntaxNode** : Bleu | **SyntaxToken** : Vert | **SyntaxTrivia** : Rouge ![Fichier de code C#](media/walkthrough-csharp-syntax-figure1.png)

En parcourant cette arborescence, vous trouverez les instructions, expressions, jetons ou espaces, quels qu’ils soient, dans un fichier de code.

Vous pouvez rechercher n’importe quel élément dans un fichier de code à l’aide des API Syntaxe, mais la plupart des scénarios concernent l’examen de petits extraits de code, ou la recherche d’instructions ou de fragments particuliers. Les deux exemples qui suivent montrent des utilisations classiques d’exploration de la structure du code ou de recherche d’instructions individuelles.

## <a name="traversing-trees"></a>Exploration des arborescences

Vous pouvez examiner les nœuds d’une arborescence de syntaxe de deux façons. Vous pouvez parcourir l’arborescence pour examiner chaque nœud, ou vous pouvez rechercher des éléments ou des nœuds spécifiques.

### <a name="manual-traversal"></a>Exploration manuelle

Vous pouvez trouver le code complet de cet exemple dans [notre dépôt GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart).

> [!NOTE]
> Les types de l’arborescence de syntaxe utilisent l’héritage pour décrire les différents éléments de syntaxe qui sont valides à différents emplacements du programme. Utiliser ces API signifie souvent effectuer un cast des propriétés ou des membres de collection vers des types dérivés spécifiques. Dans les exemples suivants, l’affectation et les casts sont des instructions distinctes, qui utilisent des variables typées explicitement. Vous pouvez lire le code pour voir les types de retour de l’API et le type à l’exécution des objets retournés. Dans la pratique, il est plus courant d’utiliser des variables typées implicitement et de se baser sur des noms d’API pour décrire le type des objets examinés.

Créez un projet C# **Outil d’analyse du code autonome** :

* Dans Visual Studio, choisissez **fichier**  >  **nouveau**  >  **projet** pour afficher la boîte de dialogue Nouveau projet.
* Sous **extensibilité Visual C#**  >  **Extensibility**, choisissez **outil d’analyse du code autonome**.
* Nommez votre projet « **SyntaxTreeManualTraversal** » et cliquez sur OK.

Vous allez analyser le programme simple « Hello World! » montré précédemment.
Ajoutez le texte pour le programme Hello World en tant que constante dans votre classe `Program` :

[!code-csharp[Declare the program text](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Ensuite, ajoutez le code suivant pour générer **l’arborescence de syntaxe** pour le texte du code dans la constante `programText`.  Ajoutez la ligne suivante à votre méthode `Main` :

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Ces deux lignes créent l’arborescence et en récupèrent le nœud racine. Vous pouvez maintenant examiner les nœuds de l’arborescence. Ajoutez ces lignes à votre méthode `Main` pour afficher certaines des propriétés du nœud racine de l’arborescence :

[!code-csharp[Examine the root node](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Exécutez l’application pour voir ce que votre code a découvert sur le nœud racine de cette arborescence.

En règle générale, vous explorez l’arborescence pour en savoir plus sur le code. Dans cet exemple, vous analysez du code que vous connaissez pour explorer les API. Ajoutez le code suivant pour examiner le premier membre du nœud `root` :

[!code-csharp[Find the first member](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Ce membre est une <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>. Il représente tous les éléments de l’étendue de la déclaration `namespace HelloWorld`. Ajoutez le code suivant pour examiner les nœuds qui sont déclarés à l’intérieur de l’espace de noms `HelloWorld` :

[!code-csharp[Find the class declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Exécutez le programme pour voir ce que vous avez découvert.

Maintenant que vous savez que la déclaration est une <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>, déclarez une nouvelle variable de ce type pour examiner la déclaration de la classe. Cette classe contient seulement un membre : la méthode `Main`. Ajoutez le code suivant pour rechercher la méthode `Main` et en effectuer un cast en <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>.

[!code-csharp[Find the main declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Le nœud de la déclaration de la méthode contient toutes les informations syntaxiques relatives à la méthode. Affichons le type de retour de la méthode `Main`, le nombre et les types des arguments, et le texte du corps de la méthode. Ajoutez le code suivant :

[!code-csharp[Examine the syntax of the main method](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Exécutez le programme pour voir toutes les informations que vous avez découvertes sur ce programme :

```text
The tree is a CompilationUnit node.
The tree has 1 elements in it.
The tree has 4 using statements. They are:
        System
        System.Collections
        System.Linq
        System.Text
The first member is a NamespaceDeclaration.
There are 1 members declared in this namespace.
The first member is a ClassDeclaration.
There are 1 members declared in the Program class.
The first member is a MethodDeclaration.
The return type of the Main method is void.
The method has 1 parameters.
The type of the args parameter is string[].
The body text of the Main method follows:
        {
            Console.WriteLine("Hello, World!");
        }
```

### <a name="query-methods"></a>Méthodes de requête

En plus de parcourir les arborescences, vous pouvez aussi explorer l’arborescence de syntaxe avec les méthodes de requête définies sur <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Ces méthodes sont normalement immédiatement familières à toute personne connaissant XPath. Vous pouvez utiliser ces méthodes avec LINQ pour rechercher rapidement des éléments dans une arborescence. <xref:Microsoft.CodeAnalysis.SyntaxNode> a des méthodes de requête comme <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> et <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>.

Vous pouvez utiliser ces méthodes de requête pour rechercher l’argument de la méthode `Main`, au lieu de naviguer dans l’arborescence. Ajoutez le code suivant dans le bas de votre nouvelle méthode `Main` :

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

La première instruction utilise une expression LINQ et la méthode <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> pour localiser le même paramètre que dans l’exemple précédent.

Exécutez le programme : vous voyez que l’expression LINQ a trouvé le même paramètre que quand vous avez exploré manuellement l’arborescence.

L’exemple utilise des instructions `WriteLine` pour afficher des informations sur les arborescences de syntaxe au fil de leur exploration. Vous pouvez aussi découvrir beaucoup plus d’informations en exécutant le programme sous le débogueur. Vous pouvez examiner plus de propriétés et de méthodes qui font partie de l’arborescence de syntaxe créée pour le programme « Hello World ».

## <a name="syntax-walkers"></a>Parcoureurs de syntaxe

Vous voulez souvent rechercher tous les nœuds d’un type spécifique dans une arborescence de syntaxe, par exemple toutes les déclarations de propriété dans un fichier. En étendant la classe <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> et en remplaçant la méthode <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)>, vous traitez chaque déclaration de propriété d’une arborescence de syntaxe sans connaître préalablement sa structure. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> est un type spécifique de <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor>, qui visite de façon récursive un nœud et chacun de ses enfants.

Cet exemple implémente un <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> qui examine une arborescence de syntaxe. Il collecte les directives `using` qu’il trouve et qui n’importent pas un espace de noms `System`.

Créez un projet C# **Outil d’analyse du code autonome** et nommez-le « **SyntaxWalker** ».

Vous pouvez trouver le code complet de cet exemple dans [notre dépôt GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart). L’exemple sur GitHub contient les deux projets décrits dans ce tutoriel.

Comme dans l’exemple précédent, vous pouvez définir une constante de chaîne pour contenir le texte du programme que vous voulez analyser :

[!code-csharp[Define the code text to analyzer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Ce texte source contient des directives `using` réparties dans quatre emplacements différents : le niveau fichier, dans l’espace de noms du plus haut niveau et dans les deux espaces de noms imbriqués. Cet exemple met en évidence un scénario de base pour l’utilisation de la classe <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> pour interroger du code. Il serait fastidieux de visiter chaque nœud dans l’arborescence de syntaxe racine pour trouver les déclarations using. Au lieu de cela, vous créez une classe dérivée et vous remplacez la méthode qui est appelée seulement quand le nœud actuel de l’arborescence est une directive using. Votre visiteur n’effectue aucun travail sur les autres types de nœuds. Cette même méthode examine chacune des instructions `using` et génère une collection des espaces de noms qui ne figurent pas dans l’espace de noms `System`. Vous créez un <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> qui examine toutes les instructions `using`, mais uniquement les instructions `using`.

Maintenant que vous avez défini le texte du programme, vous devez créer un `SyntaxTree` et obtenir la racine de cette arborescence :

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Ensuite, créez une classe. Dans Visual Studio, choisissez **projet**  >  **Ajouter un nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément**, tapez *UsingCollector.cs* comme nom de fichier.

Vous implémentez la fonctionnalité de visiteur `using` dans la classe `UsingCollector`. Commencez par faire de la classe `UsingCollector` une dérivée <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>.

[!code-csharp[Declare the base class for the using collector](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Vous avez besoin d’un stockage pour contenir les nœuds d’espace de noms que vous collectez.  Déclarez une propriété publique en lecture seule dans la classe `UsingCollector` ; vous utilisez cette variable pour stocker les nœuds <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> que vous trouvez :

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

La classe de base, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>, implémente la logique pour visiter chaque nœud de l’arborescence de syntaxe. La classe dérivée remplace les méthodes appelées pour les nœuds spécifiques qui vous intéressent. Dans ce cas, vous êtes intéressé par toutes les directives `using`. Cela signifie que vous devez remplacer la méthode <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)>. Le seul argument de cette méthode est un objet <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType>. Utiliser des visiteurs a un avantage important : ils appellent les méthodes remplacées avec des arguments déjà castés au type de nœud spécifique. La classe <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> a une propriété <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> qui stocke le nom de l’espace de noms importé. Il s’agit d’une <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. Ajoutez le code suivant dans le remplacement de <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> :

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Comme avec l’exemple précédent, vous avez ajouté différentes instructions `WriteLine` pour faciliter la compréhension de cette méthode. Vous pouvez voir quand elle est appelée, ainsi que les arguments qui lui sont passés à chaque fois.

Enfin, vous devez ajouter deux lignes de code pour créer le `UsingCollector` et faire en sorte qu’il visite le nœud racine, en collectant toutes les instructions `using`. Ensuite, ajoutez une boucle `foreach` pour afficher toutes les instructions `using` trouvées par votre collecteur :

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

Compilez et exécutez le programme. Vous devez normalement voir la sortie suivante :

```console
        VisitUsingDirective called with System.
        VisitUsingDirective called with System.Collections.Generic.
        VisitUsingDirective called with System.Linq.
        VisitUsingDirective called with System.Text.
        VisitUsingDirective called with Microsoft.CodeAnalysis.
                Success. Adding Microsoft.CodeAnalysis.
        VisitUsingDirective called with Microsoft.CodeAnalysis.CSharp.
                Success. Adding Microsoft.CodeAnalysis.CSharp.
        VisitUsingDirective called with Microsoft.
                Success. Adding Microsoft.
        VisitUsingDirective called with System.ComponentModel.
        VisitUsingDirective called with Microsoft.Win32.
                Success. Adding Microsoft.Win32.
        VisitUsingDirective called with System.Runtime.InteropServices.
        VisitUsingDirective called with System.CodeDom.
        VisitUsingDirective called with Microsoft.CSharp.
                Success. Adding Microsoft.CSharp.
Microsoft.CodeAnalysis
Microsoft.CodeAnalysis.CSharp
Microsoft
Microsoft.Win32
Microsoft.CSharp
Press any key to continue . . .
```

Félicitations ! Vous avez utilisé **l’API Syntaxe** pour rechercher des types spécifiques d’instructions et de déclarations C# dans du code source C#.
