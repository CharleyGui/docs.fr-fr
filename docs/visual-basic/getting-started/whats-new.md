---
title: Nouveautés de Visual Basic
ms.date: 10/24/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
ms.openlocfilehash: 3ab468f6c68429a3a5cb8706152288afae520df3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187144"
---
# <a name="whats-new-for-visual-basic"></a>Nouveautés de Visual Basic

Cette rubrique liste les noms des principales fonctionnalités de chaque version de Visual Basic et décrit en détail les fonctionnalités nouvelles et améliorées des dernières versions du langage.

## <a name="current-version"></a>Version actuelle

Visual Basic 16.0 / Visual Studio 2019 version 16.0
Pour de nouvelles fonctionnalités, voir [Visual Basic 16.0](#visual-basic-160).

## <a name="previous-versions"></a>Versions précédentes

Visual Basic 15.8 / Visual Studio 2017 version 15.8
Pour de nouvelles fonctionnalités, voir [Visual Basic 15.8](#visual-basic-158).

Visual Basic 15.5 / Visual Studio 2017 version 15.5
Pour de nouvelles fonctionnalités, voir [Visual Basic 15.5](#visual-basic-155).

Visual Basic 15.3 / Visual Studio 2017 version 15.3
Pour de nouvelles fonctionnalités, voir [Visual Basic 15.3](#visual-basic-153).

Visual Basic 2017 / Visual Studio 2017
Pour de nouvelles fonctionnalités, voir [Visual Basic 2017](#visual-basic-2017).

Visual Basic / Visual Studio 2015
Pour de nouvelles fonctionnalités, voir [Visual Basic 14](#visual-basic-14).

Visual Basic / Visual Studio 2013
Aperçus technologiques de la plate-forme de compilateur .NET ("Roslyn")

Visual Basic / Visual Studio 2012
Mots clés `Async` et `await`, itérateurs, attributs des informations de l’appelant

Visual Basic, Visual Studio 2010
Propriétés implémentées automatiquement, initialiseurs de collection, continuation de ligne implicite, variance co/contra générique, dynamique, accès de l’espace de noms global

Visual Basic / Visual Studio 2008
Language Integrated Query (LINQ), littéraux XML, inférence de type local, initialiseurs d’objet, types anonymes, méthodes d’extension, inférence de type `var` local, expressions lambda, opérateur `if`, méthodes partielles, types de valeur nullable

Visual Basic / Visual Studio 2005
Type `My` et types d’assistance (accès à l’application, ordinateur, système de fichiers, réseau)

Visual Basic / Visual Studio .NET 2003
Opérateurs de décalage de bits, déclaration de variable de boucle

Visual Basic / Visual Studio .NET 2002
Première version de Visual Basic .NET

## <a name="visual-basic-160"></a>Base visuelle 16.0

Visual Basic 16.0 se concentre sur la fourniture d’une plus grande partie des fonctionnalités du Visual Basic Runtime (microsoft.visualbasic.dll) à .NET Core et est la première version de Visual Basic axée sur .NET Core. De nombreuses parties du Visual Basic Runtime dépendent de WinForms et celles-ci seront ajoutées dans une version ultérieure de Visual Basic.

**Commentaires autorisés dans plus d’endroits dans les déclarations**

Dans Visual Basic 15.8 et les versions antérieures, les commentaires ne sont autorisés que sur des lignes vierges, à la fin d’une déclaration, ou dans des endroits spécifiques dans une déclaration où une continuation implicite de la ligne est autorisée. En commençant par Visual Basic 16.0, les commentaires sont également autorisés après des continuations explicites de ligne et dans une déclaration sur une ligne commençant par un espace suivi d’un accent.

```vb
Public Sub Main()
    cmd.CommandText = ' Comment is allowed here without _
        "SELECT * FROM Titles JOIN Publishers " _ ' This is a comment
        & "ON Publishers.PubId = Titles.PubID " _
 _ ' This is a comment on a line without code
        & "WHERE Publishers.State = 'CA'"
End Sub
```

## <a name="visual-basic-158"></a>Visual Basic 15.8

**Conversion optimisée de valeurs à virgule flottante en valeurs entières**

Dans les versions précédentes de Visual Basic, la conversion de valeurs [Double](../language-reference/data-types/double-data-type.md) et [Single](../language-reference/data-types/single-data-type.md) en entiers offrait des performances relativement médiocres. Visual Basic 15.8 améliore considérablement les performances des conversions de valeurs à virgule flottante en entiers quand vous passez la valeur retournée par n’importe laquelle des méthodes suivantes à l’une des [fonctions de conversion d’entiers Visual Basic intrinsèques](../language-reference/functions/type-conversion-functions.md) (CByte, CShort, CInt, CLng, CSByte, CUShort, CUInt, CULng), ou si la valeur retournée par n’importe laquelle des méthodes suivantes est implicitement castée en un type intégral type quand [Option Strict](../language-reference/statements/option-strict-statement.md) est défini sur `Off` :

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

Cette optimisation permet au code de s’exécuter plus rapidement (jusqu’à deux fois plus rapidement pour le code qui effectue un grand nombre de conversions en types d’entier). L’exemple suivant illustre certains appels de méthode simples qui sont affectés par cette optimisation :

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

Notez que cette opération tronque les valeurs à virgule flottante au lieu de les arrondir.

## <a name="visual-basic-155"></a>Visual Basic 15.5

[Arguments nommés non placés en position de fin](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

Dans Visual Basic 15.3 et antérieur, lorsqu’un appel de méthode incluait des arguments par position et par nom, les arguments positionnels devaient précéder les arguments nommés. À compter de Visual Basic 15.5, les arguments nommés et positionnels peuvent apparaître dans n’importe quel ordre, pourvu que tous les arguments jusqu'au dernier argument positionnel soient dans la position correcte. C’est particulièrement utile lorsque des arguments nommés sont utilisés pour rendre le code plus lisible.

Par exemple, dans l’appel de méthode suivant un argument nommé est entouré de deux arguments positionnels. L’argument nommé indique clairement que la valeur 19 représente un âge.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[`Private Protected`modificateur d’accès des membres](../language-reference/modifiers/private-protected.md)

Cette nouvelle combinaison de mots clés définit un membre qui est accessible par tous les membres de sa classe conteneur ainsi que par des types dérivés de la classe conteneur, mais uniquement s’ils se trouvent également dans l’assembly conteneur. Étant donné que les structures ne peuvent pas être héritées, `Private Protected` peut uniquement être appliqué aux membres d’une classe.

**Séparateur hex/binaire/octal de début**

Dans Visual Basic 2017, la prise en charge du caractère de soulignement (`_`) comme séparateur numérique a été ajoutée. Depuis Visual Basic 15.5, vous pouvez utiliser le caractère de soulignement comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. L’exemple suivant utilise un séparateur numérique de début pour définir 3,271,948,384 comme un nombre hexadécimal :

```vb
Dim number As Integer = &H_C305_F860
```

Pour utiliser le trait de soulignement comme séparateur de début, vous devez ajouter l’élément suivant à votre fichier projet Visual Basic (\*.vbproj) :

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15.3

[**Inférence de tuple nommée**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Lorsque vous affectez la valeur des éléments de tuple à partir de variables, Visual Basic déduit le nom de ces éléments des noms de variables correspondants ; vous n’avez donc pas besoin de nommer explicitement un élément de tuple. L’exemple suivant utilise l’inférence pour créer un tuple de trois éléments nommés, `state`, `stateName` et `capital`.

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Commutateurs de compilation supplémentaires**

Le compilateur de ligne de commande de Visual Basic prend à présent en charge les options de compilation [**-refout**](../reference/command-line-compiler/refout-compiler-option.md) et [**-refonly**](../reference/command-line-compiler/refonly-compiler-option.md) pour contrôler la sortie des assemblys de référence. **-refout** définit le répertoire de sortie de l’assembly de référence, tandis que **-refonly** spécifie que la compilation doit générer uniquement un assembly de référence.

## <a name="visual-basic-2017"></a>Visual Basic 2017

[**Tuples**](../programming-guide/language-features/data-types/tuples.md)

Les tuples sont une structure de données légère qui est le plus souvent utilisée pour retourner plusieurs valeurs à partir d’un seul appel de méthode. En règle générale, pour retourner plusieurs valeurs à partir d’une méthode, vous devez effectuer l’une des opérations suivantes :

- Définir un type personnalisé (`Class` ou `Structure`). Il s’agit d’une solution lourde.

- Définir un ou plusieurs paramètres `ByRef`, en plus de retourner une valeur à partir de la méthode.

La prise en charge des tuples par Visual Basic vous permet de définir rapidement un tuple, d’affecter éventuellement des noms de sémantique à ses valeurs et de récupérer rapidement ses valeurs. L’exemple suivant encapsule un appel à la méthode <xref:System.Int32.TryParse%2A> et retourne un tuple.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Vous pouvez ensuite appeler la méthode et gérer le tuple retourné avec du code comme celui-ci.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

**Les littérals binaires et les séparateurs de chiffre**

Vous pouvez définir un littéral binaire à l’aide du préfixe `&B` ou `&b`. Vous pouvez aussi utiliser le trait de soulignement, `_`, comme séparateur numérique pour améliorer la lisibilité. L’exemple suivant utilise les deux fonctionnalités pour affecter une valeur `Byte` et l’afficher sous la forme d’un nombre décimal, hexadécimal et binaire.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Pour plus d’informations, consultez la section « Affectations de littéraux » des types de données [Byte](../language-reference/data-types/byte-data-type.md#literal-assignments), [Integer](../language-reference/data-types/integer-data-type.md#literal-assignments), [Long](../language-reference/data-types/long-data-type.md#literal-assignments), [Short](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [UInteger](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments) et [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments).

[**Prise en charge des valeurs de rendement de référence de C**](../programming-guide/language-features/procedures/ref-return-values.md)

À compter de C# 7.0, C# prend en charge les valeurs de retour de référence. Autrement dit, quand la méthode d’appel reçoit une valeur retournée par référence, elle peut modifier la valeur de la référence. Visual Basic ne vous autorise pas à créer des méthodes avec des valeurs de retour de référence, mais vous permet d’utiliser et de modifier ces valeurs.

Par exemple, la classe `Sentence` suivante écrite en C# inclut une méthode `FindNext` qui recherche le mot suivant dans une phrase qui commence par une sous-chaîne spécifiée. La chaîne est retournée comme valeur de retour de référence et une variable `Boolean` passée par référence à la méthode indique si la recherche a réussi. Cela signifie qu’en plus de lire la valeur retournée, l’appelant peut `Sentence` également la modifier, et cette modification se reflète dans la classe.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Sous sa forme la plus simple, vous pouvez modifier le mot trouvé dans la phrase à l’aide de code semblable au suivant. Notez que vous n’affectez pas de valeur à la méthode, mais plutôt à l’expression retournée par la méthode, qui est la valeur de retour de référence.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Ce code pose cependant un problème : si aucune correspondance n’est trouvée, la méthode retourne le premier mot. Comme l’exemple n’examine pas la valeur de l’argument `Boolean` pour déterminer si une correspondance est trouvée, il modifie le premier mot en l’absence de correspondance. L’exemple suivant corrige ce comportement en remplaçant le premier mot par lui-même en l’absence de correspondance.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Une meilleure solution consiste à utiliser une méthode d’assistance à laquelle la valeur de retour de référence est passée par référence. La méthode d’assistance peut ensuite modifier l’argument qui lui est passé par référence. L’exemple suivant effectue cette opération.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Pour plus d’informations, voir [Valeurs de rendement de référence](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[NomOf](../language-reference/operators/nameof.md)

Vous pouvez obtenir le nom de chaîne non qualifié d’un type ou membre et l’utiliser dans un message d’erreur sans effectuer de codage irréversible de chaîne.  Votre code reste alors correct lors de la refactorisation.  Cette fonctionnalité est également utile pour placer des liens MVC modèle-vue-contrôleur et activer des événements de modification de propriété.

[Interpolation de chaîne](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)

Vous pouvez utiliser des expressions d’interpolation de chaîne pour construire des chaînes.  Une expression de chaîne interpolée s’apparente à une chaîne de modèle contenant des expressions.  Les arguments d’une chaîne interpolée sont plus compréhensibles que dans une [Composite Formatting](../../standard/base-types/composite-formatting.md).

[Accès et indexation des membres conditionnels nuls](../language-reference/operators/null-conditional-operators.md)

Vous pouvez rechercher les valeurs Null à l’aide d’une syntaxe très légère avant d’effectuer une opération d’accès aux membres (`?.`) ou d’indexation (`?[]`).  Ils permettent d'écrire moins de code pour gérer les vérifications Null, notamment pour l'exploration des structures de données.  Si la référence objet ou l’opérande gauche est Null, l’opération renvoie la valeur Null.

[Littérales à cordes multi-lignes](../../visual-basic/programming-guide/language-features/strings/string-basics.md)

Les littéraux de chaîne peuvent contenir des séquences de saut de ligne.  Il n’est plus nécessaire de passer par la méthode `<xml><![CDATA[...text with newlines...]]></xml>.Value`.

**Commentaires**

Vous pouvez placer des commentaires après les continuations de lignes implicites, dans les expressions d’initialiseur et dans les termes d’expression LINQ.

**Résolution de nom entièrement qualifiée plus intelligente**

En présence de code tel que `Threading.Thread.Sleep(1000)`, Visual Basic recherchait l’espace de noms « Threading », détectait l’ambiguïté entre System.Threading et System.Windows.Threading, et signalait une erreur.  Visual Basic prend désormais en compte les deux espaces de noms possibles.  Lorsque vous affichez la liste de saisie semi-automatique, les membres de ces deux types y sont recensés par l’éditeur Visual Studio.

**Littérals de la première date**

Vous pouvez avoir des littéraux de date au format aaaa-mm-jj, `#2015-03-17 16:10 PM#`.

**Propriétés d’interface Readonly**

Vous pouvez implémenter des propriétés d’interface en lecture seule à l’aide d’une propriété readwrite. L’interface garantit les fonctionnalités minimales et n’empêche pas une classe d’implémentation d’autoriser la définition de la propriété.

[TypeOf \<expr> IsNot \<type>](../../visual-basic/language-reference/operators/typeof-operator.md)

Pour une meilleure lisibilité du code, vous pouvez maintenant utiliser `TypeOf` avec `IsNot`.

[#Disable Warning \<ID> et #Enable Warning \<ID>](../../visual-basic/language-reference/directives/index.md)

Vous pouvez désactiver et activer des avertissements spécifiques pour les zones d’un fichier source.

**Améliorations de la fonctionnalité de commentaires de document XML**

Lorsque vous écrivez des commentaires de document, vous bénéficiez d’un éditeur intelligent et de la prise en charge de version pour la validation des noms de paramètres, le gestion appropriée des `crefs` (génériques, opérateurs, etc.), la colorisation et la refactorisation.

[Définitions partielles de modules et d’interface](../../visual-basic/language-reference/modifiers/partial.md)

En plus des classes et structures, vous pouvez déclarer des interfaces et des modules partiels.

[#Region directives à l’intérieur des organes de méthode](../../visual-basic/language-reference/directives/region-directive.md)

Vous pouvez placer des délimiteurs #Region…#End Region n’importe où dans un fichier, dans des fonctions, ou encore répartis à différents endroits du corps d’une fonction.

[Les définitions de remplacement sont implicitement des surcharges](../../visual-basic/language-reference/modifiers/overrides.md)

Si vous ajoutez le modificateur `Overrides` à une définition, le compilateur ajoute `Overloads` de manière implicite, de sorte que vous pouvez taper moins de code dans les situations courantes.

**CObj autorisé dans les arguments attributs**

Le compilateur signalait l’erreur indiquant que CObj(...) n’est pas une constante lorsqu’il est utilisé dans les constructions d’attribut.

**Déclarer et consommer des méthodes ambigues de différentes interfaces**

Auparavant, le code suivant générait des erreurs qui vous empêchaient de déclarer `IMock` ou d’appeler `GetDetails` (s’ils avaient été déclarés en C#) :

```vb
Interface ICustomer
  Sub GetDetails(x As Integer)
End Interface

Interface ITime
  Sub GetDetails(x As String)
End Interface

Interface IMock : Inherits ICustomer, ITime
  Overloads Sub GetDetails(x As Char)
End Interface

Interface IMock2 : Inherits ICustomer, ITime
End Interface
```

À présent, le compilateur utilise les règles de résolution de surcharge normales pour choisir le `GetDetails` à appeler le plus approprié, et vous pouvez déclarer des relations d’interface dans Visual Basic comme indiqué dans l’exemple.

## <a name="see-also"></a>Voir aussi

- [Nouveautés dans Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017)
- [Nouveautés dans Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019)
