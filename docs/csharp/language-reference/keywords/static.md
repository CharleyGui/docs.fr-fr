---
title: static, modificateur - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: b288e57d9241e294a0fa18edafe72eec675327a7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633186"
---
# <a name="static-c-reference"></a>static (référence C#)

Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique. Le modificateur `static` peut être utilisé avec des classes, des champs, des méthodes, des propriétés, des opérateurs, des événements et des constructeurs. En revanche, il ne peut pas être utilisé avec des indexeurs, des finaliseurs ni des types autres que des classes. Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>Exemple

La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Une déclaration de constante ou de type est implicitement un membre statique.

Un membre statique ne peut pas être référencé via une instance. Au lieu de cela, il est référencé via le nom de type. Par exemple, considérons la classe suivante :

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Pour faire référence au membre statique `x`, utilisez le nom complet `MyBaseC.MyStruct.x`, à moins que le membre soit accessible à partir de la même portée :

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Alors qu’une instance d’une classe contient une copie distincte de tous les champs d’instance de la classe, il existe une seule copie de chaque champ statique.

Il n’est pas possible d’utiliser [this](this.md) pour référencer des méthodes statiques ou des accesseurs de propriété.

Si le mot clé `static` est appliqué à une classe, tous les membres de la classe doivent être statiques.

Les classes et les classes statiques peuvent avoir des constructeurs statiques. Les constructeurs statiques sont appelés à un moment donné entre le démarrage du programme et l’instanciation de la classe.

> [!NOTE]
> L’utilisation du mot clé `static` est plus restreinte que dans C++. Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).

Pour illustrer les membres statiques, considérons une classe qui représente un employé d’une entreprise. Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés. La méthode et le champ n’appartiennent à aucune instance d’employé. Au lieu de cela, ils appartiennent à la classe entreprise. Par conséquent, ils doivent être déclarés comme membres statiques de cette classe.

## <a name="example"></a>Exemple

Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés. Pour plus de simplicité, ce programme lit le nombre actuel d’employés à partir du clavier. Dans une application réelle, ces informations doivent être lues à partir d’un fichier.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>Exemple

Cet exemple montre que bien que vous puissiez initialiser un champ statique à l’aide d’un autre champ statique encore non déclaré, les résultats sont indéfinis tant que vous n’assignez pas explicitement une valeur au champ statique.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Modificateurs](modifiers.md)
- [Classes statiques et membres de classe statique](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
