---
title: Nouveautés de C# 6 | Guide C#
description: Découvrez les nouvelles fonctionnalités de C# version 6
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224241"
---
# <a name="whats-new-in-c-6"></a>Nouveautés de C# 6

La version Release 6.0 de C# comprenait de nombreuses fonctionnalités qui améliorent la productivité des développeurs. Globalement, ces fonctionnalités vous permettent d’écrire du code plus concis et également plus lisible. La syntaxe est moins formelle concernant de nombreuses pratiques courantes. Moins de formalisme permet de voir plus facilement l’intention de conception. En apprenant bien ces fonctionnalités, vous gagnez en productivité et écrivez du code plus lisible. Vous pouvez également vous concentrer davantage sur vos fonctionnalités que sur les constructions du langage.

La suite de cet article fournit une vue d’ensemble de ces fonctionnalités, avec des liens pour explorer chacune d’entre elles. Vous pouvez également explorer les fonctionnalités dans une [exploration interactive sur C# 6](../tutorials/exploration/csharp-6.yml) dans la section des tutoriels.

## <a name="read-only-auto-properties"></a>Auto-properties en lecture seule

Les *auto-properties en lecture seule* offrent une syntaxe plus concise pour créer des types immuables. Vous déclarez l’auto-property avec uniquement un accesseur get :

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

Les propriétés `FirstName` et `LastName` peuvent être définies seulement dans le corps du constructeur de la même classe :

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Tenter de définir `LastName` dans une autre méthode génère une erreur de compilation `CS0200` :

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

Cette fonctionnalité permet une véritable prise en charge du langage pour la création de types immuables et utilise la syntaxe d’auto-property plus concise et plus pratique.

Si l’ajout de cette syntaxe ne supprime pas une méthode accessible, il s’agit d’un [changement compatible binaire](version-update-considerations.md#binary-compatible-changes).

## <a name="auto-property-initializers"></a>Initialiseurs de propriétés automatiques

Les *initialiseurs de propriétés automatiques* vous permettent de déclarer la valeur initiale d’une propriété automatique dans le cadre de la déclaration de la propriété.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

Le membre `Grades` est initialisé à l’emplacement où il est déclaré. Il est ainsi plus facile d’effectuer l’initialisation une seule fois. L’initialisation fait partie de la déclaration de propriété, facilitant ainsi la mise en correspondance de l’allocation de stockage et de l’interface publique pour les objets `Student`.

## <a name="expression-bodied-function-members"></a>Membres de fonction expression-bodied

De nombreux membres que vous écrivez sont des instructions uniques qui pourraient être des expressions simples. Écrivez un membre expression-bodied à la place. Cela fonctionne pour les méthodes et les propriétés en lecture seule. Par exemple, une substitution de `ToString()` est souvent un excellent candidat :

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Vous pouvez également utiliser cette syntaxe pour les propriétés en lecture seule :

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

La modification d’un membre existant en un membre expression-bodied est une [modification compatible binaire](version-update-considerations.md#binary-compatible-changes).

## <a name="using-static"></a>using static

L’amélioration de *using static* vous permet d’importer les méthodes statiques d’une classe unique. Vous spécifiez la classe que vous utilisez :

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<xref:System.Math> ne contient aucune méthode d’instance. Vous pouvez également utiliser `using static` pour importer les méthodes statiques d’une classe pour une classe qui comprend à la fois des méthodes statiques et des méthodes d’instance. Un des exemples les plus utiles est <xref:System.String> :

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Vous devez utiliser le nom de classe complet, `System.String`, dans une instruction static using.  Vous ne pouvez pas utiliser le mot clé `string` à la place.

Quand elles sont importées à partir d’une instruction `static using`, les méthodes d’extension ne sont dans la portée que si elles sont appelées à l’aide de la syntaxe d’invocation de méthode d’extension. Elle ne sont pas dans la portée si elles sont appelées en tant que méthode statique. Ce sera souvent le cas dans les requêtes LINQ. Vous pouvez importer le modèle LINQ en important <xref:System.Linq.Enumerable> ou <xref:System.Linq.Queryable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Vous appelez généralement les méthodes d’extension à l’aide d’expressions d’appel de méthode d’extension. Pour lever toute ambiguïté, ajoutez le nom de la classe dans les rares cas où vous les appelez à l’aide de la syntaxe d’appel de méthode statique.

La directive `static using` importe également n’importe quel type imbriqué. Vous pouvez référencer tous les types imbriqués sans qualification.

## <a name="null-conditional-operators"></a>Null - Opérateurs conditionnel

L’*opérateur conditionnel null* rend ces vérifications de valeur null beaucoup plus faciles et plus fluides. Remplacez l’accès aux membres `.` par `?.` :

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

Dans l’exemple précédent, la valeur `null` est assignée à la variable `first` si l’objet person a la valeur `null`. Sinon, la valeur de la propriété `FirstName` lui est assignée. Plus important encore, le `?.` signifie que cette ligne de code ne génère pas de `NullReferenceException` si la variable `person` a la valeur `null`. Au lieu de cela, elle court-circuite et retourne `null`. Vous pouvez également utiliser un opérateur conditionnel null pour l’accès au tableau ou à l’indexeur. Remplacez `[]` par `?[]` dans l’expression d’index.

L’expression suivante retourne un `string`, quelle que soit la valeur de `person`. Vous pouvez utiliser cette construction avec l’opérateur de *fusion null* pour assigner des valeurs par défaut quand l’une des propriétés a la valeur `null`. Quand l’expression court-circuite, la valeur `null` retournée est typée pour correspondre à l’expression complète.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Vous pouvez également utiliser `?.` pour appeler des méthodes de manière conditionnelle. L’utilisation la plus courante de fonctions membres avec l’opérateur conditionnel null consiste à appeler en toute sécurité des délégués (ou des gestionnaires d’événements) qui peuvent avoir la valeur `null`.  Appelez la méthode `Invoke` du délégué à l’aide de l’opérateur `?.` pour accéder au membre. Vous trouverez un exemple dans l’article relatif aux [modèles de délégués](../delegates-patterns.md#handling-null-delegates).

Les règles de l’opérateur `?.` garantissent que la partie gauche de l’opérateur n’est évalué qu’une seule fois. De nombreux idiomes sont permis, notamment l’exemple suivant qui utilise des gestionnaires d’événements :

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Le fait de vérifier que le côté gauche n’est évalué qu’une seule fois vous permet également d’utiliser n’importe quelle expression, notamment des appels de méthode, à gauche du `?.`

## <a name="string-interpolation"></a>Interpolation de chaîne

Avec C# 6, la nouvelle fonctionnalité d’[interpolation de chaîne](../language-reference/tokens/interpolated.md) vous permet d’incorporer des expressions dans une chaîne. Il vous suffit de faire précéder la chaîne de `$` et d’utiliser des expressions entre `{` et `}` à la place d’ordinaux :

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Cet exemple utilise des propriétés pour les expressions substituées. Vous pouvez utiliser n’importe quelle expression. Par exemple, vous pourrez calculer la moyenne pondérée cumulative d’un étudiant dans le cadre de l’interpolation :

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

La ligne de code précédente met en forme la valeur de `Grades.Average()` sous la forme d’un nombre à virgule flottante à deux décimales.

Souvent, vous devrez mettre en forme la chaîne produite à l’aide d’une culture spécifique. Vous utilisez le fait que l’objet résultant d’une interpolation de chaîne peut être converti implicitement en <xref:System.FormattableString?displayProperty=nameWithType>. L’instance <xref:System.FormattableString> contient la chaîne de format composite et les résultats de l’évaluation des expressions avant leur conversion en chaînes. Utilisez la méthode <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> pour spécifier la culture lors de la mise en forme d’une chaîne. L’exemple suivant produit une chaîne en utilisant la culture allemande (de-DE). (Par défaut, la culture allemande utilise le caractère « , » comme séparateur décimal et « . » comme séparateur des milliers.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Pour bien démarrer avec l’interpolation de chaîne, consultez le tutoriel interactif [Interpolation de chaîne en C#](../tutorials/exploration/interpolated-strings.yml), l’article [Interpolation de chaîne](../language-reference/tokens/interpolated.md) et le tutoriel [Interpolation de chaîne en C#](../tutorials/string-interpolation.md).

## <a name="exception-filters"></a>Filtres d’exceptions

Les *filtres d’exception* sont des clauses qui déterminent quand une clause catch donnée doit être appliquée. Si l’expression utilisée pour un filtre d’exception prend la valeur `true`, la clause catch effectue son traitement normal sur une exception. Si l’expression prend la valeur `false`, la clause `catch` est ignorée. Une de leurs utilisations consiste à examiner les informations concernant une exception pour déterminer si une clause `catch` peut la traiter :

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>Expression `nameof`

L’expression [nameof](../language-reference/operators/nameof.md) prend comme valeur le nom d’un symbole. C’est un très bon moyen d’obtenir les outils fonctionnant chaque fois que vous avez besoin du nom d’une variable, d’une propriété ou d’un champ de membre. L’une des utilisations les plus courantes de `nameof` est la fourniture du nom d’un symbole qui a provoqué une exception :

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Une autre utilisation concerne les applications XAML qui implémentent l’interface `INotifyPropertyChanged` :

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>await dans des blocs catch et finally

C# 5 présentait plusieurs restrictions concernant les emplacements où vous pouviez placer des expressions `await`. Avec C# 6, vous pouvez maintenant utiliser `await` dans des expressions `catch` ou `finally`. C’est le plus souvent le cas avec les scénarios de journalisation :

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Les détails d’implémentation relatifs à l’ajout de la prise en charge d’`await` dans des clauses `catch` et `finally` garantissent que le comportement est cohérent avec celui du code synchrone. Quand le code exécuté dans une clause `catch` ou `finally` est déclenché, l’exécution recherche une clause `catch` appropriée dans le bloc voisin suivant. S’il existait une exception actuelle, elle est perdue. Il en va de même pour les expressions await dans les clauses `catch` et `finally` : une clause `catch` appropriée est recherchée, et l’exception actuelle, le cas échéant, est perdue.  

> [!NOTE]
> De ce fait, il est recommandé d’écrire les clauses `catch` et `finally` avec précaution, afin d’éviter d’introduire de nouvelles exceptions.

## <a name="initialize-associative-collections-using-indexers"></a>Initialiser des collections associatives à l’aide d’indexeurs

Les *initialiseurs d’index* constituent l’une des deux fonctionnalités qui améliorent la cohérence des initialiseurs de collection avec l’utilisation des index. Dans les versions précédentes de C#, vous pouviez utiliser des *initialiseurs de collection* avec des collections de styles de séquence, notamment <xref:System.Collections.Generic.Dictionary%602>, en ajoutant des accolades autour des paires clé-valeur :

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Vous pouvez les utiliser avec des collections <xref:System.Collections.Generic.Dictionary%602> et d’autres types où la méthode `Add` accessible accepte plusieurs arguments. La nouvelle syntaxe prend en charge l’affectation à l’aide d’un index dans la collection :

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Cette fonctionnalité signifie que les conteneurs associatifs peuvent être initialisés à l’aide d’une syntaxe similaire à ce qui a été mis en place pour les conteneurs de séquence depuis plusieurs versions.

## <a name="extension-add-methods-in-collection-initializers"></a>Méthodes `Add` d’extension dans des initialiseurs de collections

La possibilité d’utiliser une *méthode d’extension* pour la méthode `Add` constitue une autre fonctionnalité qui simplifie l’initialisation des collections. Elle a été ajoutée à des fins de parité avec Visual Basic. Cette fonctionnalité est particulièrement utile pour ajouter sémantiquement de nouveaux éléments quand vous avez une classe de collection personnalisée dont une méthode porte un nom différent.

## <a name="improved-overload-resolution"></a>Résolution de surcharge améliorée

Il est probable que vous ne remarquerez pas cette dernière fonctionnalité. La précédente version du compilateur C# pouvait trouver, dans certaines constructions, des appels de méthode impliquant des expressions lambda ambigües. Prenons la méthode suivante :

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

Dans les versions antérieures de C#, l’appel de cette méthode à l’aide de la syntaxe de groupe de méthodes échouait :

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

Le compilateur précédent ne pouvait pas faire correctement la distinction entre `Task.Run(Action)` et `Task.Run(Func<Task>())`. Dans les versions précédentes, vous deviez utiliser une expression lambda comme argument :

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

Le compilateur C# 6 détermine correctement que `Task.Run(Func<Task>())` constitue un meilleur choix.

### <a name="deterministic-compiler-output"></a>Sortie du compilateur Deterministic

L’option `-deterministic` fait en sorte que le compilateur génère un assembly de sortie identique octet par octet pour les compilations successives d’un même fichier source.

Par défaut, chaque compilation génère une sortie unique. Le compilateur ajoute un horodateur et un GUID généré à partir de nombres aléatoires. Vous utilisez cette option si vous souhaitez comparer la sortie octet par octet afin de garantir la cohérence entre les builds.

Pour plus d’informations, consultez l’article [Option du compilateur -deterministic](../language-reference/compiler-options/deterministic-compiler-option.md).
