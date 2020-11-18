---
title: Types référence Nullable-référence C#
description: En savoir plus sur les types de référence Nullable C# et leur utilisation
ms.date: 04/06/2020
ms.openlocfilehash: d961af9ba3b4776e6b4ec3eeea5392fb0d0394ce
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822423"
---
# <a name="nullable-reference-types-c-reference"></a>Types référence Nullable (référence C#)

> [!NOTE]
> Cet article traite des types de référence Nullable. Vous pouvez également déclarer des [types valeur Nullable](nullable-value-types.md).

Les types référence Nullable sont disponibles à partir de C# 8,0, dans le code qui a opté pour un *contexte reconnaissant* la valeur null. Les types de référence Nullable, les avertissements d’analyse statique null et l' [opérateur null-indulgent avec](../operators/null-forgiving.md) sont des fonctionnalités de langage facultatives. Tous sont désactivés par défaut. Un *contexte Nullable* est contrôlé au niveau du projet à l’aide des paramètres de génération, ou dans le code à l’aide de pragmas.

 Dans un contexte qui prend en charge la valeur NULL :

- Une variable d’un type référence `T` doit être initialisée avec une valeur non null et ne peut jamais être assignée à une valeur qui peut être `null` .
- Une variable d’un type référence `T?` peut être initialisée avec `null` ou assignée `null` , mais doit être vérifiée `null` avant d’être déréférencée.
- Une variable `m` de type `T?` est considérée comme non NULL lorsque vous appliquez l’opérateur null-indulgent avec, comme dans `m!` .

Les différences entre un type de référence non Nullable `T` et un type de référence Nullable `T?` sont appliquées par l’interprétation du compilateur des règles précédentes. Une variable de type `T` et une variable de type `T?` sont représentées par le même type .net. L’exemple suivant déclare une chaîne non Nullable et une chaîne Nullable, puis utilise l’opérateur null-indulgent avec pour assigner une valeur à une chaîne qui n’accepte pas les valeurs NULL :

:::code language="csharp" source="snippets/shared/NullableReferenceTypes.cs" id="SnippetCoreSyntax":::

Les variables `notNull` et `nullable` sont toutes les deux représentées par le <xref:System.String> type. Étant donné que les types non Nullable et Nullable sont tous deux stockés sous le même type, il existe plusieurs emplacements où l’utilisation d’un type de référence Nullable n’est pas autorisée. En général, un type de référence Nullable ne peut pas être utilisé comme classe de base ou comme interface implémentée. Un type de référence Nullable ne peut pas être utilisé dans une expression de création d’objet ou de test de type. Un type de référence Nullable ne peut pas être le type d’une expression d’accès de membre. Les exemples suivants illustrent ces constructions :

```csharp
public MyClass : System.Object? // not allowed
{
}

var nullEmpty = System.String?.Empty; // Not allowed
var maybeObject = new object?(); // Not allowed
try
{
    if (thing is string? nullableString) // not allowed
        Console.WriteLine(nullableString);
} catch (Exception? e) // Not Allowed
{
    Console.WriteLine("error");
}
```

## <a name="nullable-references-and-static-analysis"></a>Références Nullable et analyse statique

Les exemples de la section précédente illustrent la nature des types de référence Nullable. Les types de référence Nullable ne sont pas de nouveaux types de classe, mais plutôt des annotations sur les types de référence existants. Le compilateur utilise ces annotations pour vous aider à identifier les erreurs de référence null potentielles dans votre code. Il n’existe aucune différence d’exécution entre un type de référence non Nullable et un type de référence Nullable. Le compilateur n’ajoute pas de vérification du runtime pour les types de référence non Nullable. Les avantages sont liés à l’analyse au moment de la compilation. Le compilateur génère des avertissements qui vous aident à trouver et à corriger les erreurs null potentielles dans votre code. Vous déclarez votre intention et le compilateur vous avertit lorsque votre code viole cet objectif.

Dans un contexte activé avec la valeur null, le compilateur effectue une analyse statique sur les variables de tout type référence, à la fois Nullable et non Nullable. Le compilateur effectue le suivi de l’État null de chaque variable de référence comme *not null* ou *peut être null*. L’État par défaut d’une référence qui n’accepte pas les valeurs NULL n’est *pas null*. L’État par défaut d’une référence Nullable est *peut-être null*.

Les types référence non Nullable doivent toujours être déréférencés, car leur état NULL n’est *pas null*. Pour appliquer cette règle, le compilateur émet des avertissements si un type de référence non Nullable n’est pas initialisé à une valeur non null. Les variables locales doivent être assignées là où elles sont déclarées. Chaque constructeur doit assigner chaque champ, dans son corps, à un constructeur appelé ou à l’aide d’un initialiseur de champ. Le compilateur émet des avertissements si une référence qui n’accepte pas les valeurs NULL est assignée à une référence dont l’État est *peut-être null*. Toutefois, étant donné qu’une référence non Nullable n’est *pas null*, aucun avertissement n’est émis lorsque ces variables sont déréférencées.

Les types référence Nullable peuvent être initialisés ou assignés à `null` . Par conséquent, l’analyse statique doit déterminer qu’une variable n’a *pas la valeur null* avant d’être déréférencée. Si une référence Nullable est peut-être *null*, elle ne peut pas être assignée à une variable de référence n’acceptant pas les valeurs NULL. La classe suivante montre des exemples de ces avertissements :

:::code language="csharp" source="snippets/shared/NullableReferenceTypes.cs" id="SnippetClassWithNullable":::

L’extrait de code suivant indique où le compilateur émet des avertissements lors de l’utilisation de cette classe :

:::code language="csharp" source="snippets/shared/NullableReferenceTypes.cs" id="SnippetLocalWarnings":::

Les exemples précédents illustrent l’analyse statique du compilateur pour déterminer l’État null des variables de référence. Le compilateur applique des règles de langage pour les vérifications et les assignations null afin d’en informer l’analyse.  Le compilateur ne peut pas faire d’hypothèses sur la sémantique des méthodes ou des propriétés. Si vous appelez des méthodes qui effectuent des vérifications de valeur null, le compilateur ne peut pas savoir que ces méthodes affectent l’État null d’une variable. Vous pouvez ajouter plusieurs attributs à vos API pour informer le compilateur de la sémantique des arguments et des valeurs de retour. Ces attributs ont été appliqués à de nombreuses API communes dans les bibliothèques .NET Core. Par exemple, <xref:System.String.IsNullOrEmpty%2A> a été mis à jour et le compilateur interprète correctement cette méthode comme une vérification de valeur null. Pour plus d’informations sur les attributs qui s’appliquent à l’analyse statique d’État null, consultez l’article sur les [attributs Nullable](../attributes/nullable-analysis.md).

## <a name="setting-the-nullable-context"></a>Définition du contexte Nullable

Il existe deux façons de contrôler le contexte Nullable. Au niveau du projet, vous pouvez ajouter le `<Nullable>enable</Nullable>` paramètre de projet. Dans un seul fichier source C#, vous pouvez ajouter le `#nullable enable` pragma pour activer le contexte Nullable. Consultez l’article sur la [définition d’une stratégie Nullable](../../nullable-migration-strategies.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les propositions suivantes pour la [spécification du langage C#](~/_csharplang/spec/introduction.md):

- [Types références Nullables](~/_csharplang/proposals/csharp-8.0/nullable-reference-types.md)
- [Spécification des types de référence Nullable Draft](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Types valeur Nullable](nullable-value-types.md)
