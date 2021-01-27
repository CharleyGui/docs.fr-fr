---
title: Utiliser le modèle syntaxique du SDK .NET Compiler Platform
description: Cette présentation fournit des informations sur les types que vous utilisez pour comprendre et manipuler les nœuds de syntaxe.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 3666b0ec875b465954780c3c313ca87c9a4e6676
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899137"
---
# <a name="work-with-syntax"></a>Utiliser la syntaxe

L' *arborescence de syntaxe* est une structure de données immuables fondamentale exposée par les API du compilateur. Ces arborescences représentent la structure lexicale et syntaxique du code source. Elles ont deux utilités principales :

- Pour autoriser les outils, tels qu’un IDE, des compléments, des outils d’analyse du code et des refactorisations, pour afficher et traiter la structure syntaxique du code source dans le projet d’un utilisateur.
- Pour activer les outils, tels que les refactorisations et un IDE, pour créer, modifier et réorganiser le code source de manière naturelle sans avoir à utiliser des modifications de texte direct. Par la création et la manipulation des arborescences, les outils peuvent facilement créer et réorganiser le code source.

## <a name="syntax-trees"></a>Arborescences de syntaxe

Les arborescences de syntaxe sont la structure principale utilisée pour la compilation, l’analyse de code, la liaison, la refactorisation, les fonctionnalités de l’IDE et la génération de code. Aucune partie du code source ne peut être comprise sans avoir au préalable été identifiée et classée dans l’un des nombreux éléments de langage structurel connus.

Les arborescences de syntaxe ont trois attributs principaux :

- Elles contiennent toutes les informations sources en toute fidélité. Une fidélité complète signifie que l’arborescence de syntaxe contient chaque information trouvée dans le texte source, chaque construction grammaticale, chaque jeton lexical et tout le reste entre, y compris les espaces blancs, les commentaires et les directives de préprocesseur. Par exemple, chaque littéral mentionné dans la source est représenté exactement comme il a été tapé. Les arborescences de syntaxe capturent également les erreurs dans le code source lorsque le programme est incomplet ou incorrect en représentant des jetons ignorés ou manquants.
- Ils peuvent produire le texte exact à partir duquel ils ont été analysés. À partir de n’importe quel nœud de syntaxe, il est possible d’extraire la représentation textuelle de la sous-arborescence enracinée sur ce nœud. Cette capacité signifie que les arborescences de syntaxe peuvent être utilisées pour construire et modifier le texte source. En créant une arborescence, par implication, en créant le texte équivalent et en rendant une nouvelle arborescence des modifications apportées à une arborescence existante, vous avez modifié le texte.
- Ils sont immuables et thread-safe. Après l’obtention d’une arborescence, il s’agit d’un instantané de l’état actuel du code et ne change jamais. Cela permet à plusieurs utilisateurs d’interagir simultanément avec la même arborescence de syntaxe dans différents threads sans verrouillage ou duplication. Étant donné que les arborescences sont immuables et qu’elles ne peuvent pas être modifiées directement, les méthodes de fabrique facilitent la création et la modification des arborescences de syntaxe en créant des instantanés supplémentaires de l’arborescence. Les arborescences réutilisent avantageusement les nœuds sous-jacents pour accélérer la génération d’une nouvelle version, sans consommer beaucoup plus de mémoire.

Une arborescence de syntaxe est littéralement une structure de données arborescente, où des éléments structurels non terminaux sont parents d’autres éléments. Chaque arborescence de syntaxe est constituée de nœuds, de jetons et de trivia.

## <a name="syntax-nodes"></a>Nœuds de syntaxe

Les nœuds de syntaxe figurent parmi les principaux éléments des arborescences de syntaxe. Ces nœuds représentent des constructions syntaxiques, telles que des déclarations, des instructions, des clauses et des expressions. Chaque catégorie de nœuds de syntaxe est représentée par une classe distincte dérivée de <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. L’ensemble de classes de nœud n’est pas extensible.

Tous les nœuds de syntaxe sont des nœuds non terminaux dans l’arborescence de syntaxe ; ils ont donc toujours d’autres nœuds et jetons comme enfants. Chaque nœud enfant d’un autre nœud a un nœud parent qui est accessible via la propriété <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType>. Comme les nœuds et les arborescences sont immuables, le parent d’un nœud ne change jamais. La racine de l’arborescence a un parent Null.

Chaque nœud a une méthode <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType>, qui retourne une liste des nœuds enfants dans l’ordre séquentiel déterminé par leur position dans le texte source. Cette liste ne contient pas de jetons. Chaque nœud a également des méthodes permettant d’examiner les descendants, tels que <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> , <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A> ou, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> qui représentent une liste de tous les nœuds, jetons ou anecdotes qui existent dans la sous-arborescence associée à ce nœud.

En outre, chaque sous-classe de nœud de syntaxe expose les mêmes enfants par le biais de propriétés fortement typées. Par exemple, une classe de nœud <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> a trois propriétés supplémentaires propres aux opérateurs binaires : <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> et <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>. Le type de <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> et <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> est <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>, et le type de <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> est <xref:Microsoft.CodeAnalysis.SyntaxToken>.

Certains nœuds de syntaxe ont des enfants facultatifs. Par exemple, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> a un <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax> facultatif. Si l’enfant n’est pas trouvé, la propriété retourne la valeur Null.

## <a name="syntax-tokens"></a>Jetons de syntaxe

Les jetons de syntaxe sont les éléments terminaux dans la grammaire d’un langage ; ils représentent les plus petits fragments syntaxiques du code. Ils ne sont jamais parents d’autres nœuds ou jetons. Les jetons de syntaxe se composent de mots clés, d’identificateurs, de littéraux et de caractères de ponctuation.

Par souci d’efficacité, le type <xref:Microsoft.CodeAnalysis.SyntaxToken> est un type valeur CLR. Par conséquent, contrairement aux nœuds de syntaxe, il n’y a qu’une seule structure pour tous les genres de jetons, avec une combinaison de propriétés dont le sens dépend du genre du jeton représenté.

Par exemple, un jeton de littéral d’entier représente une valeur numérique. En plus du texte source brut sur lequel s’étend le jeton, le jeton de littéral a une propriété <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> qui indique précisément la valeur entière décodée. Cette propriété est typée en <xref:System.Object>, car elle peut être l’un des nombreux types primitifs.

La propriété <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> fournit les mêmes informations que la propriété <xref:Microsoft.CodeAnalysis.SyntaxToken.Value>, mais elle est toujours typée en <xref:System.String>. Dans du texte source C#, un identificateur peut inclure des caractères d’échappement Unicode, mais la syntaxe de la séquence d’échappement n’est pas considérée comme faisant partie du nom de l’identificateur. Même si le texte brut sur lequel s’étend le jeton inclut la séquence d’échappement, la propriété <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> ne l’inclut pas. À la place, elle inclut les caractères Unicode identifiés par la séquence d’échappement. Par exemple, si le texte source contient un identificateur écrit sous la forme `\u03C0`, la propriété <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> pour ce jeton retourne `π`.

## <a name="syntax-trivia"></a>Trivia de syntaxe

Les trivia de syntaxe représentent les parties du texte source qui n’ont pas une grande utilité pour la compréhension générale du code. Il s’agit notamment des espaces blancs, des commentaires et des directives de préprocesseur. Comme les jetons de syntaxe, les trivia sont des types valeur. Le type <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> unique est utilisé pour décrire tous les genres de trivia.

Du fait que les trivia ne font pas partie de la syntaxe du langage à proprement parler et qu’ils peuvent se trouver n’importe où entre deux jetons, ils ne sont pas représentés dans l’arborescence de syntaxe comme enfants d’un nœud. Les trivia sont toutefois inclus dans l’arborescence de syntaxe, car ils sont importants lors de l’implémentation d’une fonctionnalité telle que la refactorisation, mais aussi pour garantir une haute fidélité avec le texte source.

Vous pouvez accéder à la anecdote en inspectant le ou les collections d’un jeton <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> . Quand le texte source est analysé, les séquences de trivia sont associées aux jetons. En règle générale, un jeton est propriétaire de tous les trivia qui se trouvent après lui sur la même ligne. Les trivia situés après cette ligne dépendent du jeton suivant. Dans le fichier source, le premier jeton obtient tous les trivia initiaux, et la dernière séquence de trivia est associée au jeton de fin de fichier, qui a sinon une largeur égale à zéro.

Contrairement aux nœuds et jetons de syntaxe, les trivia de syntaxe n’ont pas de parents. Toutefois, comme les trivia font partie de l’arborescence et que chacun d’eux est associé à un jeton unique, vous pouvez accéder au jeton correspondant à l’aide de la propriété <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType>.

## <a name="spans"></a>Étendues

Chaque nœud, jeton ou trivia connaît sa position dans le texte source et le nombre de caractères qui le composent. La position du texte est représentée par un entier 32 bits, qui est un index `char` de base zéro. L’objet <xref:Microsoft.CodeAnalysis.Text.TextSpan> représente la position de début et le nombre de caractères sous forme de deux entiers. Si <xref:Microsoft.CodeAnalysis.Text.TextSpan> a une longueur nulle, il fait référence à une position entre deux caractères.

Chaque nœud a deux propriétés <xref:Microsoft.CodeAnalysis.Text.TextSpan> : <xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A> et <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A>.

La <xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A> propriété est l’étendue de texte à partir du début du premier jeton dans la sous-arborescence du nœud jusqu’à la fin du dernier jeton. Cette étendue n’inclut pas les trivia de début ou de fin.

La <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A> propriété est l’étendue de texte qui comprend l’étendue normale du nœud, plus l’étendue des anecdotes de début ou de fin.

Par exemple :

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

L’étendue du nœud de l’instruction dans le bloc est délimitée par deux barres verticales simples (|). Elle inclut les caractères `throw new Exception("Not right.");`. L’étendue complète est délimitée par les deux barres verticales doubles (||). Elle inclut les mêmes caractères que l’étendue du nœud, plus les caractères associés aux trivia de début et de fin.

## <a name="kinds"></a>Genres

Chaque nœud, jeton ou trivia a une propriété <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> de type <xref:System.Int32?displayProperty=nameWithType>, qui identifie précisément l’élément de syntaxe représenté. Cette valeur peut être convertie en une énumération spécifique au langage. Chaque langage, C# ou Visual Basic, possède une `SyntaxKind` énumération unique ( <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> et <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType> , respectivement) qui répertorie tous les nœuds, jetons et éléments de anecdotes possibles dans la grammaire. Cette conversion peut être effectuée automatiquement en accédant aux méthodes d’extension <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A?displayProperty=nameWithType> ou <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind%2A?displayProperty=nameWithType>.

La propriété <xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> permet de lever facilement toute ambiguïté sur les types de nœud de syntaxe qui utilisent la même classe de nœud. Pour les jetons et les trivia, cette propriété est le seul moyen de différencier les types d’élément entre eux.

Prenons l’exemple d’une classe <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax>, qui a les enfants <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> et <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>. La propriété <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A> détermine si le nœud de syntaxe est du genre <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression> ou <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression>.

> [!TIP]
> Il est recommandé de vérifier les types à l’aide <xref:Microsoft.CodeAnalysis.CSharpExtensions.IsKind%2A> des méthodes d’extension (pour C#) ou <xref:Microsoft.CodeAnalysis.VisualBasicExtensions.IsKind%2A> (pour VB).

## <a name="errors"></a>Erreurs

Même si le texte source contient des erreurs de syntaxe, une arborescence de syntaxe complète avec aller-retour au code source est exposée. Lorsque l’analyseur rencontre du code qui n’est pas conforme à la syntaxe définie du langage, il utilise l’une des deux techniques suivantes pour créer une arborescence de syntaxe :

- Si l’analyseur attend un type particulier de jeton, mais ne le trouve pas, il peut insérer un jeton manquant dans l’arborescence de syntaxe à l’emplacement où le jeton était attendu. Un jeton manquant représente le jeton qui était attendu, mais du fait qu’il a une étendue vide, sa propriété <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> retourne `true`.

- L’analyseur peut ignorer les jetons jusqu’à ce qu’il en trouve un dans lequel il peut continuer l’analyse. Dans ce cas, les jetons ignorés sont attachés en tant que nœud de trivia avec le genre <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.
