---
description: using, directive - Référence C#
title: using, directive - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: f22a67348b19b8c97513ca685b2b10b34b1fd6fd
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89141944"
---
# <a name="using-directive-c-reference"></a>using, directive (référence C#)

La directive `using` a trois utilisations :

- Pour autoriser l'utilisation de types dans un espace de noms pour ne pas avoir à qualifier l'utilisation d'un type dans cet espace de noms :

    ```csharp
    using System.Text;
    ```

- Pour vous permettre d’accéder aux membres statiques et aux types imbriqués d’un type sans devoir qualifier l’accès avec le nom du type.

    ```csharp
    using static System.Math;
    ```

    Pour plus d’informations, consultez la [directive using static](using-static.md).

- Pour créer un alias pour un espace de noms ou un type. Cela s’appelle une *directive using alias*.

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

Le mot clé `using` est également utilisé pour créer des *instructions using<xref:System.IDisposable>, qui garantissent que les objets* tels que les fichiers et les polices sont gérés correctement. Pour plus d’informations, consultez [Instruction using](using-statement.md).

## <a name="using-static-type"></a>Utilisation du type statique

Vous pouvez accéder aux membres statiques d'un type sans devoir qualifier l'accès avec le nom du type :

```csharp
using static System.Console;
using static System.Math;
class Program
{
    static void Main()
    {
        WriteLine(Sqrt(3*3 + 4*4));
    }
}
```

## <a name="remarks"></a>Notes

La portée d'une directive `using` se limite au fichier dans lequel elle apparaît.

La directive `using` peut être placée :

- Au début d’un fichier de code source, avant les définitions de type ou d’espace de noms.
- Dans n’importe quel espace de noms, mais avant les espaces de noms ou types déclarés dans cet espace de noms.

Sinon, une erreur de compilateur [CS1529](../../misc/cs1529.md) est générée.

Créez une directive d’alias `using` afin de faciliter la qualification d’un identificateur pour un espace de noms ou un type. Dans une directive `using`, le type ou l’espace de noms complet doit toujours être utilisé, indépendamment des directives `using` placées avant. Aucun alias `using` ne peut être utilisé dans la déclaration d’une directive `using`. Par exemple, les lignes ci-dessous génèrent une erreur de compilation :

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

Créez une directive `using` pour utiliser les types dans un espace de noms sans avoir à spécifier l'espace de noms. Une directive `using` ne vous donne pas accès à des espaces de noms imbriqués dans l'espace de noms que vous spécifiez.

Les espaces de noms sont organisés en deux catégories : définis par l'utilisateur et définis par le système. Les espaces de noms définis par l'utilisateur sont des espaces de noms définis dans votre code. Pour obtenir la liste des espaces de noms définis par le système, consultez [Navigateur d’API .NET](../../../../api/index.md).

## <a name="example-1"></a>Exemple 1

L'exemple suivant montre comment définir et utiliser un alias `using` pour un espace de noms :

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

Une directive d'alias using ne peut pas avoir un type générique ouvert sur le côté droit. Par exemple, vous ne pouvez pas créer un alias using pour un `List<T>`, mais vous pouvez en créer un pour un `List<int>`.

## <a name="example-2"></a>Exemple 2

L'exemple suivant montre comment définir une directive `using` et un alias `using` pour une classe :

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez [Directives using](~/_csharplang/spec/namespaces.md#using-directives) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Utilisation d’espaces de noms](../../programming-guide/namespaces/using-namespaces.md)
- [Mots clés C#](index.md)
- [Espaces de noms](../../programming-guide/namespaces/index.md)
- [using, instruction](using-statement.md)
