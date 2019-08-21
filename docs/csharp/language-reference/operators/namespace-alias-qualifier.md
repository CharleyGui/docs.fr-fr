---
title: 'Opérateur :: - Référence C#'
ms.custom: seodec18
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 2aceb51747708b12fb3059b097b72206c78a9d5d
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971243"
---
# <a name="-operator-c-reference"></a>Opérateur :: (référence C#)

Utilisez le qualificateur d’alias d’espace de noms `::` pour accéder aux membres d’un espace de noms avec alias. Vous utilisez le qualificateur `::` entre deux identificateurs. L’identificateur de gauche peut être un des alias suivants :

- Un alias d’espace de noms créé avec la [directive using alias](../keywords/using-directive.md) :
  
  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- Un [alias externe](../keywords/extern-alias.md).
- L’alias `global`, qui est l’alias d’espace de noms global. L’espace de noms global est l’espace de noms qui contient des espaces de noms et des types qui ne sont pas déclarés dans un espace de noms nommé. Quand il est utilisé avec le qualificateur `::`, l’alias `global` référence toujours l’espace de noms global, même si l’alias d’espace de noms `global` défini par l’utilisateur est présent.
  
  L’exemple suivant utilise l’alias `global` pour accéder à l’espace de noms .NET <xref:System>, qui est un membre de l’espace de noms global. Sans l’alias `global`, l’accès se ferait à l’espace de noms `System` défini par l’utilisateur, qui est un membre de l’espace de noms `MyCompany.MyProduct` :

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }
  
      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```
  
  > [!NOTE]
  > Le mot clé `global` est l’alias d’espace de noms global seulement quand il s’agit de l’identificateur de gauche du qualificateur `::`.

Vous pouvez également utiliser l’[opérateur d’accès aux membres `.`](member-access-operators.md#member-access-operator-) pour accéder aux membres d’un espace de noms avec alias. Cependant, l’opérateur `.` est également utilisé pour accéder aux membres d’un type. Le qualificateur `::` garantit que son identificateur de gauche référence toujours un alias d’espace de noms, même s’il existe un type ou un espace de noms portant le même nom.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Qualificateurs d’alias d’espace de noms](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Utilisation des espaces de noms](../../programming-guide/namespaces/using-namespaces.md)
