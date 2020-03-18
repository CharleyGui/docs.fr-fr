---
title: Classes et méthodes partielles - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 50b192d5a7416a982f41d0c3ac13e9c1bfe3397c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399818"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Classes et méthodes partielles (Guide de programmation C#)

Il est possible de fractionner la définition d’une [classe](../../language-reference/keywords/class.md), d’un [struct](../../language-reference/builtin-types/struct.md), d’une [interface](../../language-reference/keywords/interface.md) ou d’une méthode entre plusieurs fichiers sources. Chaque fichier source contient une section de la définition de méthode ou de type, et toutes les parties sont combinées au moment où l’application est compilée.

## <a name="partial-classes"></a>Classes partielles

Il peut être utile de fractionner une définition de classe dans les situations suivantes :

- Dans des projets volumineux, le fractionnement d’une classe entre plusieurs fichiers distincts permet à plusieurs programmeurs d’y travailler simultanément.

- Quand vous utilisez une source générée automatiquement, vous pouvez ajouter du code à la classe sans avoir à recréer le fichier source. Visual Studio suit cette approche pour créer des formulaires Windows Forms, du code wrapper de service web, etc. Vous pouvez écrire du code qui utilise ces classes sans avoir à modifier le fichier créé par Visual Studio.

- Pour fractionner une définition de classe, utilisez le modificateur de mot clé [partial](../../language-reference/keywords/partial-type.md), comme ci-dessous :

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

Le mot clé `partial` indique que d’autres parties de la classe, du struct ou de l’interface peuvent être définies dans l’espace de noms. Toutes les parties doivent utiliser le mot clé `partial`. Toutes les parties doivent être disponibles à la compilation pour former le type final. Toutes les parties doivent avoir la même accessibilité : `public`, `private`, etc.

Si une partie est déclarée comme abstract, l’ensemble du type est considéré comme abstract. Si une partie est déclarée comme sealed, l’ensemble du type est considéré comme sealed. Si une partie déclare un type de base, l’ensemble du type hérite de cette classe.

Toutes les parties qui spécifient une classe de base doivent être en accord, mais les parties qui omettent une classe de base héritent tout de même du type de base. Les parties peuvent spécifier des interfaces de base différentes. Le type final implémente alors toutes les interfaces indiquées dans toutes les déclarations partielles. Tous les membres de classe, de struct ou d’interface déclarés dans une définition partielle sont disponibles pour toutes les autres parties. Le type final est la combinaison de toutes les parties au moment de la compilation.

> [!NOTE]
> Le modificateur `partial` n’est pas disponible sur les déclarations de délégué ou d’énumération.

L’exemple suivant montre que les types imbriqués peuvent être partiels, même si le type dans lequel ils sont imbriqués n’est pas partiel lui-même.

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

Au moment de la compilation, les attributs de définitions de type partiel sont fusionnés. Observez, par exemple, les déclarations suivantes :

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

Elles sont équivalentes aux déclarations suivantes :

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

Les éléments suivants sont fusionnés à partir de toutes les définitions de type partiel :

- commentaires XML

- interfaces

- attributs de paramètre de type générique

- attributs de classe

- membres

Observez, par exemple, les déclarations suivantes :

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

Elles sont équivalentes aux déclarations suivantes :

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a>Restrictions

Il y a plusieurs règles à respecter quand vous utilisez des définitions de classe partielle :

- Toutes les définitions de type partiel conçues comme des parties du même type doivent être modifiées avec `partial`. Par exemple, les déclarations de classe suivantes génèrent une erreur :

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- Le modificateur `partial` peut uniquement être placé juste avant les mots clés `class`, `struct` ou `interface`.

- Les types partiels imbriqués sont autorisés dans les définitions de type partiel, comme illustré dans l’exemple suivant :

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- Toutes les définitions de type partiel conçues comme des parties du même type doivent être définies dans le même assembly et dans le même module (fichier .exe ou .dll). Les définitions partielles ne peuvent pas être fractionnées entre plusieurs modules.

- Le nom de classe et les paramètres de type générique doivent correspondre dans toutes les définitions de type partiel. Les types génériques peuvent être partiels. Chaque déclaration partielle doit utiliser les mêmes noms de paramètres, dans le même ordre.

- Les mots clés suivants sont facultatifs dans une définition de type partiel. S’ils sont utilisés dans une définition de type partiel, ils ne doivent pas être en conflit avec les mots clés spécifiés dans une autre définition partielle pour le même type :

  - [public](../../language-reference/keywords/public.md)

  - [Privé](../../language-reference/keywords/private.md)

  - [Protégé](../../language-reference/keywords/protected.md)

  - [Interne](../../language-reference/keywords/internal.md)

  - [Abstrait](../../language-reference/keywords/abstract.md)

  - [sealed](../../language-reference/keywords/sealed.md)

  - classe de base

  - modificateur [new](../../language-reference/keywords/new-modifier.md) (parties imbriquées)

  - contraintes génériques

Pour plus d’informations, consultez [Contraintes sur les paramètres de type](../generics/constraints-on-type-parameters.md).

## <a name="example-1"></a>Exemple 1

### <a name="description"></a>Description

Dans l’exemple suivant, les champs et le constructeur de la classe `Coords` sont déclarés dans une définition de classe partielle, et le membre `PrintCoords` est déclaré dans une autre définition de classe partielle.

### <a name="code"></a>Code

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a>Exemple 2

### <a name="description"></a>Description

L’exemple suivant montre que vous pouvez également développer des interfaces et des structs partiels.

### <a name="code"></a>Code

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a>Méthodes partielles

Une classe partielle ou un struct partiel peut contenir une méthode partielle. Une partie de la classe contient la signature de la méthode. Une implémentation facultative peut être définie dans la même partie ou dans une autre partie. Si l’implémentation n’est pas fournie, la méthode et tous les appels à cette méthode sont supprimés au moment de la compilation.

Les méthodes partielles permettent à l’implémenteur d’une partie d’une classe de définir une méthode, comme pour un événement. L’implémenteur de l’autre partie de la classe peut décider s’il faut implémenter la méthode ou non. Si la méthode n’est pas implémentée, le compilateur supprime la signature de méthode et tous les appels à la méthode. Les appels à la méthode, y compris tous les résultats retournés par l’évaluation des arguments dans les appels, n’ont aucun effet au moment de l’exécution. C’est pourquoi le code dans la classe partielle peut utiliser librement une méthode partielle, même si l’implémentation n’est pas fournie. Aucune erreur de compilation ou d’exécution n’est générée si la méthode est appelée, mais qu’elle n’est pas finalement implémentée.

Les méthodes partielles sont particulièrement utiles pour personnaliser le code généré. Elles permettent de réserver un nom et une signature de méthode. Ainsi, le code généré peut appeler la méthode, mais le développeur peut décider d’implémenter ou non la méthode. En grande partie comme les classes partielles, les méthodes partielles permettent d’utiliser conjointement du code créé par un générateur de code et du code créé manuellement par un développeur sans impact sur le temps d’exécution.

Une déclaration de méthode partielle se compose de deux parties : la définition et l’implémentation. Celles-ci peuvent être situées dans des parties distinctes ou dans la même partie d’une classe partielle. En l’absence de déclaration d’implémentation, le compilateur optimise à la fois la déclaration de définition et tous les appels à la méthode.

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- Une déclaration de méthode partielle doit commencer par le mot clé contextuel [partial](../../language-reference/keywords/partial-type.md), et la méthode doit retourner [void](../../language-reference/builtin-types/void.md).

- Les méthodes partielles peuvent avoir des paramètres [in](../../language-reference/keywords/in-parameter-modifier.md) ou [ref](../../language-reference/keywords/ref.md), mais pas [out](../../language-reference/keywords/out-parameter-modifier.md).

- Les méthodes partielles sont implicitement [private](../../language-reference/keywords/private.md) et, par conséquent, elles ne peuvent pas être [virtual](../../language-reference/keywords/virtual.md).

- Les méthodes partielles ne peuvent pas être [extern](../../language-reference/keywords/extern.md), car la présence du corps détermine si elles sont utilisées pour la définition ou pour l’implémentation.

- Les méthodes partielles peuvent avoir des modificateurs [static](../../language-reference/keywords/static.md) et [unsafe](../../language-reference/keywords/unsafe.md).

- Les méthodes partielles peuvent être génériques. Les contraintes sont placées sur la déclaration de méthode partielle de définition et peuvent être répétées facultativement sur la déclaration d’implémentation. Les noms de paramètre et de paramètre de type ne doivent pas obligatoirement être identiques dans la déclaration d’implémentation et la déclaration de définition.

- Vous pouvez créer un [délégué](../../language-reference/builtin-types/reference-types.md) pour une méthode partielle qui a été définie et implémentée, mais pas pour une méthode partielle qui a uniquement été définie.

## <a name="c-language-specification"></a>Spécification du langage C#

Pour plus d’informations, consultez [Types partiels](~/_csharplang/spec/classes.md#partial-types) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes](./classes.md)
- [Types de structure](../../language-reference/builtin-types/struct.md)
- [Interfaces](../interfaces/index.md)
- [partielle (Type)](../../language-reference/keywords/partial-type.md)
