---
title: static, modificateur - Référence C#
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744662"
---
# <a name="static-c-reference"></a>static (référence C#)

Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique. Le modificateur `static` peut être utilisé pour déclarer des classes `static`. Dans les classes, les interfaces et les structs, vous pouvez ajouter le modificateur `static` à des champs, des méthodes, des propriétés, des opérateurs, des événements et des constructeurs. Le modificateur `static` ne peut pas être utilisé avec des indexeurs ou des finaliseurs. Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>Exemple

La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Une déclaration de constante ou de type est implicitement un membre `static`. Un membre `static` ne peut pas être référencé par le biais d’une instance. Au lieu de cela, elle est référencée par le nom de type. Par exemple, considérons la classe suivante :

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Pour faire référence au `x`membre `static`, utilisez le nom qualifié complet, `MyBaseC.MyStruct.x`, sauf si le membre est accessible à partir de la même portée :

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Alors qu’une instance d’une classe contient une copie distincte de tous les champs d’instance de la classe, il n’existe qu’une seule copie de chaque champ `static`.

Il n’est pas possible d’utiliser [`this`](this.md) pour référencer des méthodes ou des accesseurs de propriété `static`.

Si le mot clé `static` est appliqué à une classe, tous les membres de la classe doivent être `static`.

Les classes, les interfaces et les classes `static` peuvent avoir des constructeurs `static`. Un constructeur `static` est appelé à un moment donné entre le démarrage du programme et l’instanciation de la classe.

> [!NOTE]
> L’utilisation du mot clé `static` est plus restreinte que dans C++. Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).

Pour illustrer `static` membres, considérons une classe qui représente un employé de la société. Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés. La méthode et le champ n’appartiennent pas à une instance d’employé. Au lieu de cela, ils appartiennent à la classe des employés dans son ensemble. Ils doivent être déclarés comme `static` membres de la classe.

## <a name="example"></a>Exemple

Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés. Ce programme lit le nombre actuel d’employés à partir du clavier.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>Exemple

Cet exemple montre que vous pouvez initialiser un champ `static` à l’aide d’un autre champ `static` qui n’est pas encore déclaré. Les résultats ne sont pas définis tant que vous n’affectez pas explicitement une valeur au champ `static`.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Modificateurs](index.md)
- [Classes statiques et membres de classe statique](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
