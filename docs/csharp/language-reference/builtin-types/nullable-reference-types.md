---
title: Types de référence nuls - Référence C
description: Renseignez-vous sur les types de référence nuls et sur la façon de les utiliser
ms.date: 04/06/2020
ms.openlocfilehash: cb61b162b06faa51faabbcdd91e55618cdeaca73
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102695"
---
# <a name="nullable-reference-types-c-reference"></a>Types de référence nuls (référence C)

> [!NOTE]
> Cet article couvre les types de référence in annulables. Vous pouvez également déclarer [les types de valeur nuls](nullable-value-types.md).

Les types de référence nuls sont disponibles à partir de C 8.0, dans le code qui a opté dans un *contexte de conscience nulle*. Les types de référence nuls, les avertissements d’analyse statique nul et [l’opérateur null-indulgent](../operators/null-forgiving.md) sont des caractéristiques linguistiques facultatives. Tous sont désactivés par défaut. Un *contexte inquérable* est contrôlé au niveau du projet à l’aide de paramètres de construction ou de code à l’aide de pragmas.

 Dans un contexte de connaissance nulle :

- Une variable d’un type `T` de référence doit être parasitée avec `null`non-null, et ne peut jamais être attribué une valeur qui peut être .
- Une variable d’un `T?` type de `null` référence `null`peut être parasiffée ou assignée, mais doit être vérifiée `null` avant de procéder au démosation.
- Une `m` variable `T?` de type est considérée comme non nulle lorsque vous appliquez `m!`l’opérateur null-indulgent, comme dans .

Les distinctions entre un type `T` de référence non `T?` annulable et un type de référence nul sont appliquées par l’interprétation par le compilateur des règles précédentes. Une variable `T` de type et `T?` une variable de type sont représentées par le même type .NET. L’exemple suivant déclare une corde non annulable et une clause annulable, puis utilise l’opérateur qui pardonne l’annulation pour attribuer une valeur à une chaîne non annulable :

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetCoreSyntax":::

Les `notNull` variables `nullable` et sont toutes <xref:System.String> deux représentées par le type. Étant donné que les types non annulables et in nullables sont tous deux stockés comme le même type, il y a plusieurs endroits où l’utilisation d’un type de référence nul n’est pas autorisée. En général, un type de référence nul ne peut pas être utilisé comme classe de base ou interface implémentée. Un type de référence in nullable ne peut pas être utilisé dans une création d’objet ou une expression de test de type. Un type de référence in nullable ne peut pas être le type d’expression d’accès d’un membre. Les exemples suivants montrent ces constructions :

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

## <a name="nullable-references-and-static-analysis"></a>Références et analyses statiques insédables

Les exemples de la section précédente illustrent la nature des types de références nuls. Les types de référence nuls ne sont pas de nouveaux types de classe, mais plutôt des annotations sur les types de référence existants. Le compilateur utilise ces annotations pour vous aider à trouver des erreurs de référence nulles potentielles dans votre code. Il n’y a pas de différence de temps d’exécution entre un type de référence non annulable et un type de référence nul. Le compilateur n’ajoute aucune vérification du temps d’exécution pour les types de référence non annulables. Les avantages sont dans l’analyse de temps de compilation. Le compilateur génère des avertissements qui vous aident à trouver et à corriger les erreurs nulles potentielles dans votre code. Vous déclarez votre intention, et le compilateur vous avertit lorsque votre code viole cette intention.

Dans un contexte in annulable, le compilateur effectue une analyse statique sur des variables de tout type de référence, à la fois in nullables et non annulables. Le compilateur suit l’état nul de chaque variable de référence comme *non nul* ou *peut-être nul*. L’état par défaut d’une référence non annulable *n’est pas nul*. L’état par défaut d’une référence annulée est *peut-être nul*.

Les types de référence non annulables devraient toujours être sûrs de la déreférence parce que leur état nul *n’est pas nul*. Pour faire respecter cette règle, le compilateur émet des avertissements si un type de référence non annulable n’est pas paradé à une valeur non nulle. Les variables locales doivent être assignées là où elles sont déclarées. Chaque constructeur doit attribuer chaque champ, soit dans son corps, un constructeur appelé, ou en utilisant un initialisateur de champ. Le compilateur émet des avertissements si une référence non annulable est attribuée à une référence dont l’état est *peut-être nul*. Toutefois, comme une référence non annulable *n’est pas nulle,* aucun avertissement n’est émis lorsque ces variables sont dé-référencées.

Les types de référence nuls `null`peuvent être parasités ou attribués à . Par conséquent, l’analyse statique doit déterminer qu’une variable *n’est pas nulle* avant qu’elle ne soit déreférée. Si une référence annulée est déterminée à *être peut-être nulle,* elle ne peut pas être attribuée à une variable de référence non-nullable. La classe suivante montre des exemples de ces avertissements :

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetClassWithNullable":::

L’extrait suivant montre où le compilateur émet des avertissements lors de l’utilisation de cette classe:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetLocalWarnings":::

Les exemples précédents démontrent l’analyse statique du compilateur pour déterminer l’état nul des variables de référence. Le compilateur applique des règles linguistiques pour les vérifications et les affectations nulles pour éclairer son analyse.  Le compilateur ne peut pas faire d’hypothèses sur la sémantique des méthodes ou des propriétés. Si vous appelez des méthodes qui effectuent des contrôles nuls, le compilateur ne peut pas savoir que ces méthodes affectent l’état nul d’une variable. Il existe un certain nombre d’attributs que vous pouvez ajouter à vos API pour informer le compilateur sur la sémantique des arguments et des valeurs de retour. Ces attributs ont été appliqués à de nombreuses API communes dans les bibliothèques de base .NET. Par exemple, <xref:System.String.IsNullOrEmpty%2A> a été mis à jour, et le compilateur interprète correctement cette méthode comme une vérification nulle. Pour plus d’informations sur les attributs qui s’appliquent à l’analyse statique de l’état nul, voir l’article sur [les attributs Nullable](../attributes/nullable-analysis.md).

## <a name="setting-the-nullable-context"></a>Définir le contexte in nullable

Il y a deux façons de contrôler le contexte nul. Au niveau du projet, `<Nullable>enable</Nullable>` vous pouvez ajouter le paramètre du projet. Dans un seul fichier source C, `#nullable enable` vous pouvez ajouter le pragma pour activer le contexte nul. Voir l’article sur [la mise en place d’une stratégie annulée](../../nullable-migration-strategies.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir les propositions suivantes pour la [spécification linguistique CMD](~/_csharplang/spec/introduction.md):

- [Types références Nullables](~/_csharplang/proposals/csharp-8.0/nullable-reference-types.md)
- [Spécifications de types de référence nuls](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Types valeur Nullable](nullable-value-types.md)
