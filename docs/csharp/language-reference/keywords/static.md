---
title: static, modificateur - Référence C#
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 771bcfdac4c4bf27c15da4bc374d804405317a78
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102058"
---
# <a name="static-c-reference"></a>static (référence C#)

Cette page `static` couvre le mot clé modificateur. Le `static` mot clé fait [`using static`](using-static.md) également partie de la directive.

Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique. Le `static` modificateur peut `static` être utilisé pour déclarer les cours. Dans les classes, les interfaces et les `static` structs, vous pouvez ajouter le modificateur aux champs, méthodes, propriétés, opérateurs, événements et constructeurs. Le `static` modificateur ne peut pas être utilisé avec des indexeurs ou des finalisateurs. Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example---static-class"></a>Exemple - classe statique

La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Une déclaration constante ou type `static` est implicitement un membre. Un `static` membre ne peut pas être référencé par une instance. Au lieu de cela, il est référencé à travers le nom de type. Par exemple, considérons la classe suivante :

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Pour se `static` référer `x`au membre, utilisez `MyBaseC.MyStruct.x`le nom entièrement qualifié, à moins que le membre ne soit accessible à partir de la même portée :

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Bien qu’une instance d’une classe contient une copie distincte de tous `static` les champs d’instance de la classe, il n’y a qu’une seule copie de chaque champ.

Il n’est pas [`this`](this.md) possible `static` d’utiliser pour référencer les méthodes ou les accesseurs de propriété.

Si `static` le mot clé est appliqué à une classe, tous les membres de la classe doivent être `static`.

Les classes, les `static` interfaces `static` et les classes peuvent avoir des constructeurs. Un `static` constructeur est appelé à un moment donné entre le moment où le programme commence et la classe est instantanée.

> [!NOTE]
> L’utilisation du mot clé `static` est plus restreinte que dans C++. Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).

Pour `static` démontrer aux membres, considérez une classe qui représente un employé de l’entreprise. Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés. La méthode et le terrain n’appartiennent à aucun cas d’employé. Au lieu de cela, ils appartiennent à la classe des employés dans son ensemble. Ils doivent être `static` déclarés membres de la classe.

## <a name="example---static-field-and-method"></a>Exemple - champ statique et méthode

Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés. Ce programme lit le nombre actuel d’employés à partir du clavier.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a>Exemple - initialisation statique

Cet exemple montre que vous `static` pouvez initialiser un champ en utilisant un autre `static` champ qui n’est pas encore déclaré. Les résultats ne seront pas définis jusqu’à `static` ce que vous affectiez explicitement une valeur sur le terrain.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation CMD](../../programming-guide/index.md)
- [Mots-clés C](index.md)
- [Modificateurs](index.md)
- [en utilisant une directive statique](using-static.md)
- [Classes statiques et membres de classe statique](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
