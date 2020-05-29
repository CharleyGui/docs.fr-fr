---
title: Bien démarrer avec la transformation de la syntaxe (API Roslyn)
description: Une introduction à la façon de parcourir et d’interroger les arborescences de syntaxe.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 5879dfd6ed0a5f6465829eec496d10cfcfd07362
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202122"
---
# <a name="get-started-with-syntax-transformation"></a>Bien démarrer avec la transformation de la syntaxe

Ce tutoriel s’appuie sur les concepts et techniques décrits dans les démarrages rapides [Bien démarrer avec l’analyse de la syntaxe](syntax-analysis.md) et [Bien démarrer avec l’analyse sémantique](semantic-analysis.md). Si vous ne l’avez pas déjà fait, vous devez terminer ces démarrages rapides avant de commencer celui-ci.

Dans ce démarrage rapide, vous découvrez les techniques de création et de transformation des arborescences de syntaxe. En association avec les techniques que vous avez apprises dans les démarrages rapides précédents, vous créez votre première refactorisation de ligne de commande !

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Immuabilité et plateforme de compilateur .NET

L’**immuabilité** est un principe fondamental de la plateforme de compilateur .NET. Une fois créées, les structures de données immuables ne peuvent plus être modifiées. Les structures de données immuables peuvent être partagées et analysées simultanément par plusieurs consommateurs, en toute sécurité. Il n’existe aucun risque qu’un consommateur n’en perturbe un autre de manière imprévisible. Votre analyseur n’a pas besoin de verrous ou d’autres mesures de concurrence. Cette règle s’applique aux arborescences de syntaxe, compilations, symboles, modèles sémantiques et toute autre structure de données que vous rencontrez. Au lieu de modifier des structures existantes, les API créent de nouveaux objets en fonction des différences spécifiés dans les anciens objets. Vous appliquez ce concept aux arborescences de syntaxe pour créer de nouvelles arborescences à l’aide de transformations.

## <a name="create-and-transform-trees"></a>Créer et transformer des arborescences

Vous choisissez une des deux stratégies pour les transformations de syntaxe. Les **méthodes de fabrique** sont particulièrement utiles lorsque vous recherchez des nœuds spécifiques à remplacer, ou des emplacements spécifiques dans lesquelles vous souhaitez insérer le nouveau code. Les **modules de réécriture** sont recommandés lorsque vous souhaitez analyser un projet complet et y rechercher des modèles de code à remplacer.

### <a name="create-nodes-with-factory-methods"></a>Créer des nœuds avec des méthodes de fabrique

La première transformation de syntaxe montre les méthodes de fabrique. Vous allez remplacer une instruction `using System.Collections;` par une instruction `using System.Collections.Generic;`. Cet exemple montre comment créer des objets <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> à l’aide des méthodes de fabrique <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType>. Pour chaque type de **nœud**, **jeton** ou **trivia**, il existe une méthode de fabrique qui crée une instance de ce type. Vous créez des arborescences de syntaxe en composant hiérarchiquement des nœuds de façon ascendante. Puis vous transformez le programme existant en remplaçant les nœuds existants par la nouvelle arborescence que vous avez créée.

Démarrez Visual Studio, puis créez un nouveau projet C# **Outil d’analyse du code autonome**. Dans Visual Studio, choisissez **fichier**  >  **nouveau**  >  **projet** pour afficher la boîte de dialogue Nouveau projet. Sous **extensibilité Visual C#**  >  **Extensibility** , choisissez un **outil d’analyse du code autonome**. Ce démarrage rapide inclut deux exemples de projets, par conséquent, nommez la solution **SyntaxTransformationQuickStart**, puis nommez le projet **ConstructionCS**. Cliquez sur **OK**.

Ce projet utilise les méthodes de classe <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> pour construire un élément <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> représentant l’espace de noms `System.Collections.Generic`.

Ajoutez la directive using suivante au début de `Program.cs` .

[!code-csharp[import the SyntaxFactory class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Vous allez créer des **nœuds de syntaxe du nom** pour générer l’arborescence qui représente l’instruction `using System.Collections.Generic;`. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> est la classe de base pour les quatre types de noms qui s’affichent en C#. Vous composez ces quatre types de noms à la fois pour créer n’importe quel nom pouvant s’afficher en langage C# :

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, qui représente des noms d’identificateur unique simples comme `System` et `Microsoft`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, qui représente un nom de type ou de méthode générique comme `List<int>`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, qui représente un nom qualifié de formulaire `<left-name>.<right-identifier-or-generic-name>` comme `System.IO`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, qui représente un nom en utilisant un alias d’assembly externe comme `LibraryV2::Foo`.

Vous utilisez la méthode <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> pour créer un nœud <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>. Ajoutez le code suivant à votre méthode `Main`, dans `Program.cs` :

[!code-csharp[create the system identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Le code précédent crée un objet <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> et l’assigne à la variable `name`. La plupart des API Roslyn renvoient des classes de base pour les rendre plus faciles à utiliser avec les types associés. La variable `name`, une <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>, peut être réutilisée lorsque vous générez la <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. N’utilisez pas l’inférence de type lorsque vous générez l’exemple. Vous allez automatiser cette étape dans ce projet.

Vous avez créé le nom. Maintenant, il est temps de créer d’autres nœuds dans l’arborescence en générant une <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. La nouvelle arborescence utilise `name` comme partie gauche du nom et une nouvelle <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> pour l’espace de noms `Collections` comme partie droite de la <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Ajoutez le code suivant à `program.cs` :

[!code-csharp[create the collections identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Exécutez à nouveau le code et affichez les résultats. Vous créez une arborescence de nœuds qui représente le code. Vous allez continuer à utiliser ce modèle pour générer la <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> pour l’espace de noms `System.Collections.Generic`. Ajoutez le code suivant à `Program.cs` :

[!code-csharp[create the full identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Réexécutez le programme pour voir que vous avez créé l’arborescence pour le code à ajouter.

### <a name="create-a-modified-tree"></a>Créer une arborescence modifiée

Vous avez créé petite arborescence de syntaxe contenant une instruction. Les API permettant de créer de nouveaux nœuds représentent la solution idéale pour créer des instructions uniques ou d’autres petits blocs de code. Toutefois, pour générer de plus grands blocs de code, vous devez utiliser des méthodes qui remplacent les nœuds ou insèrent des nœuds dans une arborescence existante. N’oubliez pas que les arborescences de syntaxe sont immuables. L’**API Syntaxe** ne fournit aucun mécanisme permettant de modifier une arborescence de syntaxe existante après la construction. Au lieu de cela, elle fournit des méthodes qui génèrent de nouvelles arborescences en fonction des modifications apportées aux arborescences existantes. Les méthodes `With*` sont définies dans des classes concrètes qui dérivent de <xref:Microsoft.CodeAnalysis.SyntaxNode> ou dans des méthodes d’extension déclarées dans la classe <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions>. Ces méthodes créent un nouveau nœud en appliquant les modifications apportées aux propriétés enfants d’un nœud existant. En outre, la méthode d’extension <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> peut être utilisée pour remplacer un nœud descendant dans une sous-arborescence. Cette méthode met également à jour le parent pour pointer vers l’enfant qui vient d’être créé, et répète ce processus pour l’arborescence complète. Ce processus est appelé « _re-spining_ » d’arborescence.

L’étape suivante consiste à créer une arborescence qui représente un (petit) programme complet puis à le modifier. Ajoutez le code suivant au début de la classe `Program` :

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> L’exemple de code utilise l’espace de noms `System.Collections` et non pas l’espace de noms `System.Collections.Generic`.

Ensuite, ajoutez le code suivant en bas de la méthode `Main` pour analyser le texte et créer une arborescence :

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

Cet exemple utilise la méthode <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> pour remplacer le nom dans un nœud <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> par celui construit dans le code précédent.

Créez un nouveau nœud <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> à l’aide de la méthode <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> pour mettre à jour le nom `System.Collections` avec le nom que vous avez créé dans le code précédent. Ajoutez le code suivant dans le bas de la méthode `Main` :

[!code-csharp[create a new subtree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Exécutez le programme et examinez attentivement la sortie. `newusing` n’a pas été placé dans l’arborescence racine. L’arborescence d’origine n’a pas été modifiée.

Ajoutez le code suivant à l’aide de la méthode d'extension <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> pour créer une nouvelle arborescence. La nouvelle arborescence est le résultat du remplacement de l’importation existante par le nœud `newUsing` mis à jour. Vous affectez cette nouvelle arborescence à la variable `root` existante :

[!code-csharp[create a new root tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Réexécutez le programme. Cette fois, l’arborescence importe correctement l’espace de noms `System.Collections.Generic`.

### <a name="transform-trees-using-syntaxrewriters"></a>Transformer des arborescences avec `SyntaxRewriters`

Les méthodes `With*` et <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> constituent une solution pratique pour transformer des branches individuelles en une arborescence de syntaxe. La classe <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> effectue plusieurs transformations sur une arborescence de syntaxe. La classe <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> est une sous-classe de <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> applique une transformation à un type spécifique de <xref:Microsoft.CodeAnalysis.SyntaxNode>. Vous pouvez appliquer des transformations à plusieurs types d’objets <xref:Microsoft.CodeAnalysis.SyntaxNode> là où elles apparaissent dans une arborescence de syntaxe. Le second projet de ce démarrage rapide crée une refactorisation de ligne de commande qui supprime des types explicites dans des déclarations de variables locales partout où une inférence de type peut être utilisée.

Créez un nouveau projet C# d' **outil d’analyse du code** autonome. Dans Visual Studio, cliquez avec le bouton droit sur le nœud de la solution `SyntaxTransformationQuickStart`. Choisissez **Ajouter**  >  **un nouveau projet** pour afficher la **boîte de dialogue Nouveau projet**. Sous **extensibilité Visual C#**  >  **Extensibility**, choisissez **outil d’analyse du code autonome**. Nommez votre projet `TransformationCS`, puis cliquez sur OK.

La première étape consiste à créer une classe dérivée de <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> pour effectuer vos transformations. Ajoutez un nouveau fichier de classe au projet. Dans Visual Studio, choisissez **projet**  >  **Ajouter une classe...**. Dans la boîte de dialogue **Ajouter un nouvel élément** `TypeInferenceRewriter.cs` , tapez comme nom de fichier.

Ajoutez le code suivant à l’aide de directives dans le fichier `TypeInferenceRewriter.cs` :

[!code-csharp[add necessary usings](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Ensuite, étendez la classe `TypeInferenceRewriter` à la classe <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> :

[!code-csharp[add base class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Ajoutez le code suivant pour déclarer un champ en lecture seule privé qui contiendra une <xref:Microsoft.CodeAnalysis.SemanticModel> et initialisez-le dans le constructeur. Vous aurez besoin de ce champ ultérieurement pour déterminer où l’inférence de type peut être utilisée :

[!code-csharp[initialize members](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Remplacez la méthode <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> :

```csharp
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> De nombreuses API Roslyn déclarent des types de retour représentant des classes de base des types Runtime réels retournés. Dans de nombreux scénarios, il est possible de remplacer un type de nœud par un autre, voire de le supprimer. Dans cet exemple, la méthode <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> retourne un <xref:Microsoft.CodeAnalysis.SyntaxNode>, au lieu du type dérivé de <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>. Ce module de réécriture retourne un nouveau nœud <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> en fonction du nœud existant.

Ce démarrage rapide gère les déclarations de variables locales. Vous pouvez l’étendre à d’autres déclarations telles que des boucles `foreach`, des boucles `for`, des expressions LINQ et des expressions lambda. En outre, ce module de réécriture transformera les déclarations dans la forme la plus simple :

```csharp
Type variable = expression;
```

Si vous souhaitez explorer votre propre déclaration, vous pouvez étendre l’exemple terminé pour ces types de déclarations de variables :

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Ajoutez le code suivant au corps de la méthode `VisitLocalDeclarationStatement` pour ignorer la réécriture de ces formes de déclarations :

[!code-csharp[exclude other declarations](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

La méthode indique qu’aucune réécriture n’a lieu en retournant le paramètre `node` inchangé. Si aucune de ces expressions `if` n’est vraie, le nœud représente une déclaration possible avec initialisation. Ajoutez les instructions suivantes pour extraire le nom du type spécifié dans la déclaration et liez-le à l’aide du champ <xref:Microsoft.CodeAnalysis.SemanticModel> pour obtenir un symbole de type :

[!code-csharp[extract type name](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Ajoutez maintenant cette instruction pour lier l’expression de l’initialiseur :

[!code-csharp[bind initializer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Enfin, ajoutez l’instruction `if` suivante pour remplacer le nom de type existant par le mot clé `var` si le type de l’expression de l’initialiseur correspond au type spécifié :

[!code-csharp[ReplaceNode](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ReplaceNode "Replace the initializer node")]

Cette condition est nécessaire car la déclaration peut effectuer un cast de l’expression de l’initialiseur dans une classe de base ou une interface. Si vous le souhaitez, les types à gauche et à droite de l’affectation ne correspondent pas. Dans ce cas, la suppression du type explicite modifierait la sémantique d’un programme. `var` est spécifié comme un identificateur plutôt qu’un mot clé car `var` est un mot clé contextuel. Les trivias de début et de fin (espaces blancs) sont transférés de l’ancien nom de type vers le mot clé `var` afin de conserver les espaces blancs verticaux et l’indentation. Il est plus simple d’utiliser `ReplaceNode` plutôt que `With*` pour transformer la <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>, car le nom de type est en fait le petit-enfant de l’instruction de déclaration.

Vous avez terminé le `TypeInferenceRewriter`. Revenez maintenant à votre fichier `Program.cs` pour terminer l’exemple. Créez un test <xref:Microsoft.CodeAnalysis.Compilation> et obtenez le <xref:Microsoft.CodeAnalysis.SemanticModel> à partir de celui-ci. Utilisez <xref:Microsoft.CodeAnalysis.SemanticModel> pour tester votre `TypeInferenceRewriter`. Vous effectuerez cette étape en dernier. En attendant, déclarez une variable d’espace réservé représentant votre compilation de test :

[!code-csharp[DeclareCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Après une pause, vous devriez voir apparaître une erreur sous forme de tilde, indiquant qu’il n’existe aucune méthode `CreateTestCompilation`. Appuyez sur **Ctrl+point** pour ouvrir l’ampoule, puis sur Entrée pour appeler la commande **Générer un stub de méthode**. Cette commande va générer un stub de méthode pour la méthode `CreateTestCompilation` dans la classe `Program`. Vous y reviendrez pour remplir cette méthode :

![C# - Générer une méthode à partir de l’utilisation](./media/syntax-transformation/generate-from-usage.png)

Écrivez le code suivant pour effectuer une itération sur chaque <xref:Microsoft.CodeAnalysis.SyntaxTree> dans le test de <xref:Microsoft.CodeAnalysis.Compilation>. Pour chacune d’elles, initialisez un nouveau `TypeInferenceRewriter` avec le <xref:Microsoft.CodeAnalysis.SemanticModel> pour cet arborescence :

[!code-csharp[IterateTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

Dans l’instruction `foreach` que vous avez créée, ajoutez le code suivant pour effectuer la transformation sur chaque arborescence source. Ce code écrit de façon conditionnelle la nouvelle arborescence transformée si des modifications ont été effectuées. Votre module de réécriture doit uniquement modifier une arborescence si elle rencontre une ou plusieurs déclarations de variables locales qui pourraient être simplifiées à l’aide de l’inférence de type :

[!code-csharp[TransformTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

Vous devriez voir des tildes sous le code `File.WriteAllText`. Sélectionnez l’ampoule et ajoutez l’instruction `using System.IO;` nécessaire.

Vous avez presque terminé. Il y a une étape restante : création d’un test <xref:Microsoft.CodeAnalysis.Compilation> . Étant donné que vous n’avez pas utilisé du tout l’inférence de type pendant ce démarrage rapide, cela aurait été un cas de test parfait. Malheureusement, la création d’une compilation à partir d’un fichier de projet C# dépasse le cadre de cette procédure pas à pas. Heureusement, si vous avez suivi attentivement les instructions, il reste un espoir. Remplacez le contenu de la méthode `CreateTestCompilation` par le code suivant : Il crée une compilation de test correspondant par coïncidence au projet décrit dans ce démarrage rapide :

[!code-csharp[CreateTestCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Croisez les doigts et exécutez le projet. Dans Visual Studio, choisissez **Déboguer**  >  **Démarrer le débogage**. Visual Studio devrait vous avertir que les fichiers de votre projet ont été modifiés. Cliquez sur «**Oui pour tout**» pour recharger les fichiers modifiés. Examinez ces fichiers pour vérifier la qualité de votre travail. Remarquez à quel point le code serait plus propre sans tous ces spécificateurs de type explicites et redondants.

Félicitations ! Vous avez utilisé les **API du compilateur** pour écrire votre propre refactorisation qui recherche certains modèles syntaxiques dans tous les fichiers d’un projet C#, analyse la sémantique du code source correspondant à ces modèles puis la transforme. Vous êtes maintenant officiellement un auteur de refactorisation !
