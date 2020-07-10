---
title: Nouveautés de C# 7.3
description: Vue d’ensemble des nouvelles fonctionnalités de C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: cd8f554516fb5078d9d2ed1eec787f36e8f4c7a7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174755"
---
# <a name="whats-new-in-c-73"></a>Nouveautés de C# 7.3

Il existe deux thèmes principaux pour la version C# 7.3. Un thème fournit des fonctionnalités permettant au code sécurisé d’être aussi performant que le code non sécurisé. Le second thème fournit des améliorations incrémentielles aux fonctionnalités existantes. En outre, de nouvelles options de compilateur ont été ajoutées à cette version.

Les nouvelles fonctionnalités suivantes prennent en charge le thème de meilleures performances pour le code sécurisé :

- Vous pouvez accéder à des champs fixes sans épinglage.
- Vous pouvez réaffecter des variables locales `ref`.
- Vous pouvez utiliser des initialiseurs sur les tableaux `stackalloc`.
- Vous pouvez utiliser des instructions `fixed` avec tout type prenant en charge un modèle.
- Vous pouvez utiliser des contraintes génériques supplémentaires.

Les améliorations suivantes ont été apportées aux fonctionnalités existantes :

- Vous pouvez tester `==` et `!=` avec des types de tuple.
- Vous pouvez utiliser des variables d’expression dans d’autres emplacements.
- Vous pouvez joindre des attributs à un champ de stockage de propriétés implémentées automatiquement.
- La résolution de la méthode lorsque des arguments diffèrent de `in` a été améliorée.
- La résolution de la surcharge comporte maintenant moins de cas ambigus.

Les nouvelles options du compilateur sont les suivantes :

- `-publicsign` pour activer la signature d’assemblys Open Source Software (OSS).
- `-pathmap` pour fournir un mappage des répertoires sources.

Le reste de cet article fournit des détails et des liens pour en savoir plus sur chacune de ces améliorations. Vous pouvez explorer ces fonctionnalités dans votre environnement à l’aide de l’outil global `dotnet try` :

1. Installez l’outil global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).
1. Clonez le référentiel [dotnet/try-samples](https://github.com/dotnet/try-samples).
1. Définissez le répertoire actuel sur le sous-répertoire *csharp7* pour le référentiel *try-samples*.
1. Exécutez `dotnet try`.

## <a name="enabling-more-efficient-safe-code"></a>Code sécurisé plus performant

Vous devez être en mesure d’écrire en toute sécurité un code C# ainsi performant qu’un code non sécurisé. Le code sécurisé évite les classes d’erreurs, par exemple les dépassements de mémoire tampon, les pointeurs perdus et d’autres erreurs d’accès à la mémoire. Ces nouvelles fonctionnalités étendent les fonctionnalités de code sécurisé vérifiables. Efforcez-vous d’utiliser plus de constructions sécurisées pour écrire votre code. Ces fonctionnalités facilitent cette écriture.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>L’indexation des champs `fixed` ne nécessite aucun épinglage

Prenons le struct suivant :

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

Dans les versions antérieures de C#, vous deviez épingler une variable pour accéder à un des entiers faisant partie de `myFixedField`. À présent, le code suivant se compile sans épingler la variable `p` à l’intérieur d’une instruction `fixed` distincte :

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

La variable `p` accède à un élément dans `myFixedField`. Vous n’avez pas besoin de déclarer une variable `int*` distincte. Notez que vous avez toujours besoin d’un contexte `unsafe`. Dans les versions antérieures de C#, vous devez déclarer un second pointeur fixe :

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

Pour plus d’informations, consultez l’article sur l' [ `fixed` instruction](../language-reference/keywords/fixed-statement.md).

### <a name="ref-local-variables-may-be-reassigned"></a>Les variables locales `ref` peuvent être réaffectées

Désormais, les variables locales `ref` peuvent être réassignées pour faire référence à d’autres instances, après avoir été initialisées. Le code suivant effectue maintenant une compilation :

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Pour plus d’informations, consultez l’article sur les [ `ref` retours et les `ref` variables locales](../programming-guide/classes-and-structs/ref-returns.md), ainsi que l’article sur [`foreach`](../language-reference/keywords/foreach-in.md) .

### <a name="stackalloc-arrays-support-initializers"></a>Les tableaux `stackalloc` prennent en charge les initialiseurs

Vous avez été en mesure de spécifier les valeurs des éléments dans un tableau lors de son initialisation :

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Maintenant, la même syntaxe peut être appliquée aux tableaux déclarés avec `stackalloc` :

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Pour plus d’informations, consultez l’article relatif à l' [ `stackalloc` opérateur](../language-reference/operators/stackalloc.md) .

### <a name="more-types-support-the-fixed-statement"></a>D’autres types prennent en charge l’instruction `fixed`

L’instruction `fixed` prenait en charge un ensemble limité de types. À partir de C# 7.3, tout type contenant une méthode `GetPinnableReference()` qui retourne `ref T` ou `ref readonly T` peut être `fixed`. L’ajout de cette fonctionnalité signifie que `fixed` peut être utilisé avec <xref:System.Span%601?displayProperty=nameWithType> et des types connexes.

Pour plus d’informations, consultez l’article sur les [ `fixed` instructions](../language-reference/keywords/fixed-statement.md) dans la référence du langage.

### <a name="enhanced-generic-constraints"></a>Contraintes génériques améliorées

Vous pouvez maintenant spécifier le type <xref:System.Enum?displayProperty=nameWithType> ou <xref:System.Delegate?displayProperty=nameWithType> en tant que contraintes de classe de base pour un paramètre de type.

Vous pouvez également utiliser la nouvelle `unmanaged` contrainte pour spécifier qu’un paramètre de type doit être un [type non managé](../language-reference/builtin-types/unmanaged-types.md)qui n’accepte pas les valeurs NULL.

Pour plus d’informations, consultez les articles sur les contraintes et contraintes [ `where` génériques](../language-reference/keywords/where-generic-type-constraint.md) [sur les paramètres de type](../programming-guide/generics/constraints-on-type-parameters.md).

L’ajout de ces contraintes aux types existants est une [modification incompatible](version-update-considerations.md#incompatible-changes). Les types génériques fermés peuvent ne plus respecter ces nouvelles contraintes.

## <a name="make-existing-features-better"></a>Améliorer les fonctionnalités existantes

Le second thème fournit des améliorations apportées aux fonctionnalités du langage. Ces fonctionnalités améliorent la productivité lors de l’écriture de code C#.

### <a name="tuples-support--and-"></a>Les tuples prennent en charge `==` et `!=`

Les types tuple C# prennent désormais en charge `==` et `!=`. Pour plus d’informations, consultez la section [égalité des tuples](../language-reference/builtin-types/value-tuples.md#tuple-equality) de l’article [types de tuple](../language-reference/builtin-types/value-tuples.md) .

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Joindre des attributs à des champs de stockage pour les propriétés implémentées automatiquement

Cette syntaxe est maintenant prise en charge :

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

L’attribut `SomeThingAboutFieldAttribute` est appliqué au champ de stockage généré par le compilateur pour `SomeProperty`. Pour plus d’informations, consultez les [attributs](../programming-guide/concepts/attributes/index.md) dans le guide de programmation C#.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in` critère de résolution de surcharge de méthode

Lorsque le modificateur de l’argument `in` a été ajouté, ces deux méthodes provoqueraient une ambiguïté :

```csharp
static void M(S arg);
static void M(in S arg);
```

À présent, la surcharge par valeur (la première dans l’exemple précédent) est meilleure que la version de référence en lecture seule. Pour appeler la version avec l’argument de référence en lecture seule, vous devez inclure le modificateur `in` lors de l’appel de la méthode.

> [!NOTE]
> Cette opération a été implémentée en tant que correctif de bogue. Il n’y a donc plus d’ambiguïté, même si la version du langage est définie sur « 7.2 ».

Pour plus d’informations, consultez l’article sur le [ `in` modificateur de paramètre](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Étendre des variables d’expression dans les initialiseurs

La syntaxe ajoutée dans C# 7.0 pour autoriser les déclarations variables `out` a été étendue pour inclure des initialiseurs de champ, des initialiseurs de propriété, des initialiseurs de constructeur et des clauses de requête. Il permet d’écrire un code tel que l’exemple suivant :

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a>Candidats de surcharge améliorés

Dans chaque version, les règles de résolution de surcharge ont été mises à jour pour résoudre les situations où des appels de méthode ambigus sont face à un choix « évident ». Cette version ajoute trois nouvelles règles pour aider le compilateur à opter pour le choix évident :

1. Lorsqu’un groupe de méthodes contient à la fois une instance et des membres statiques, le compilateur ignore les membres de l’instance si la méthode a été appelée sans récepteur d’instance ou contexte. Le compilateur ignore les membres statiques si la méthode a été appelée avec un récepteur d’instance. Lorsqu’il n’existe aucun récepteur, le compilateur inclut uniquement les membres statiques dans un contexte statique, sinon, à la fois les membres statiques et les membres de l’instance. Lorsque le récepteur représente de façon ambiguë une instance ou un type, le compilateur inclut les deux éléments. Un contexte statique, où un récepteur d’instance `this` implicite ne peut pas être utilisé, inclut le corps des membres où aucun `this` n’est défini, par exemple des membres statiques, ainsi que chaque endroit où `this` ne peut pas être utilisé, par exemple les initialiseurs de champ et les initialiseurs de constructeur.
1. Lorsqu’un groupe de méthodes contient certaines méthodes génériques dont les arguments de type ne répondent pas à leurs contraintes, ces membres sont supprimés de l’ensemble de candidats.
1. Pour une conversion de groupe de méthodes, les méthodes candidates dont le type de retour ne correspond pas à celui du délégué sont supprimées de l’ensemble.

Vous ne remarquerez que cette modification car vous trouverez moins d’erreurs de compilateur pour les surcharges de méthode ambiguës si vous savez quelle méthode est la meilleure.

## <a name="new-compiler-options"></a>Nouvelles options du compilateur

De nouvelles options du compilateur prennent en charge la nouvelle build et les scénarios DevOps pour les programmes C#.

### <a name="public-or-open-source-signing"></a>Signature publique ou Open Source

L’option du compilateur `-publicsign` indique au compilateur de signer l’assembly à l’aide d’une clé publique. L’assembly est marqué comme étant signé, mais la signature provient de la clé publique. Cette option vous permet de générer des assemblys signés à partir de projets open source à l’aide d’une clé publique.

Pour plus d’informations, consultez l’article [Option du compilateur -publicsign](../language-reference/compiler-options/publicsign-compiler-option.md).

### <a name="pathmap"></a>pathmap

L’option du compilateur `-pathmap` indique au compilateur de remplacer les chemins sources de l’environnement de build par des chemins sources mappés. L’option `-pathmap` contrôle le chemin source écrit par le compilateur vers les fichiers PDB ou pour <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.

Pour plus d’informations, consultez l’article [Option du compilateur -pathmap](../language-reference/compiler-options/pathmap-compiler-option.md).
