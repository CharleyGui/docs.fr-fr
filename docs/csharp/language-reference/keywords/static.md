---
description: static, modificateur - Référence C#
title: static, modificateur - Référence C#
ms.date: 09/25/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 239163fc2f91ccbfe8b1c111a358db87d36a8308
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654637"
---
# <a name="static-c-reference"></a>static (référence C#)

Cette page couvre le `static` mot clé de modificateur. Le `static` mot clé fait également partie de la [`using static`](using-static.md) directive.

Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique. Le `static` modificateur peut être utilisé pour déclarer des `static` classes. Dans les classes, les interfaces et les structs, vous pouvez ajouter le `static` modificateur à des champs, des méthodes, des propriétés, des opérateurs, des événements et des constructeurs. Le `static` modificateur ne peut pas être utilisé avec des indexeurs ou des finaliseurs. Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

À compter de C# 8,0, vous pouvez ajouter le `static` modificateur à une [fonction locale](../../programming-guide/classes-and-structs/local-functions.md). Une fonction locale statique ne peut pas capturer les variables locales ou l’état de l’instance.

À compter de C# 9,0, vous pouvez ajouter le `static` modificateur à une [expression lambda](../operators/lambda-expressions.md) ou une [méthode anonyme](../operators/delegate-operator.md). Une méthode lambda statique ou anonyme ne peut pas capturer les variables locales ou l’état de l’instance.

## <a name="example---static-class"></a>Exemple : classe statique

La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Une déclaration de constante ou de type est implicitement un `static` membre. Un `static` membre ne peut pas être référencé par le biais d’une instance. Au lieu de cela, elle est référencée par le nom de type. Par exemple, considérons la classe suivante :

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Pour faire référence au `static` membre `x` , utilisez le nom qualifié complet, `MyBaseC.MyStruct.x` , sauf si le membre est accessible à partir de la même portée :

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Alors qu’une instance d’une classe contient une copie distincte de tous les champs d’instance de la classe, il n’existe qu’une seule copie de chaque `static` champ.

Il n’est pas possible d’utiliser [`this`](this.md) pour référencer des `static` méthodes ou des accesseurs de propriété.

Si le `static` mot clé est appliqué à une classe, tous les membres de la classe doivent avoir la valeur `static` .

Les classes, les interfaces et les `static` classes peuvent avoir des `static` constructeurs. Un `static` constructeur est appelé à un moment donné entre le démarrage du programme et l’instanciation de la classe.

> [!NOTE]
> L’utilisation du mot clé `static` est plus restreinte que dans C++. Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).

Pour illustrer `static` les membres, considérez une classe qui représente un employé de la société. Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés. La méthode et le champ n’appartiennent pas à une instance d’employé. Au lieu de cela, ils appartiennent à la classe des employés dans son ensemble. Ils doivent être déclarés en tant que `static` membres de la classe.

## <a name="example---static-field-and-method"></a>Exemple : champ et méthode statiques

Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés. Ce programme lit le nombre actuel d’employés à partir du clavier.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a>Exemple : initialisation statique

Cet exemple montre que vous pouvez initialiser un `static` champ à l’aide d’un autre `static` champ qui n’est pas encore déclaré. Les résultats ne sont pas définis tant que vous n’affectez pas explicitement une valeur au `static` champ.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Modificateurs](index.md)
- [using static, directive](using-static.md)
- [Classes statiques et membres de classe statique](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
