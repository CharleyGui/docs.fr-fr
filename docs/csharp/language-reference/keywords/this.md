---
title: this, mot clé - Référence C#
description: this, mot clé (référence C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 2a2c487ad93e6fc75ecf95c541e859b8b60bb5b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715107"
---
# <a name="this-c-reference"></a>this (référence C#)

Le mot clé `this` fait référence à l’instance actuelle de la classe et est également utilisé comme modificateur du premier paramètre d’une méthode d’extension.

> [!NOTE]
> Cet article traite de l’utilisation de `this` avec des instances de classe. Pour plus d’informations sur son utilisation dans les méthodes d’extension, consultez [Méthodes d’extension](../../programming-guide/classes-and-structs/extension-methods.md).

Voici quelques utilisations courantes de `this` :

- Pour qualifier des membres masqués par des noms similaires, par exemple :

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Pour passer un objet comme paramètre à d’autres méthodes, par exemple :

  ```csharp
  CalcTax(this);
  ```

- Pour déclarer des indexeurs, par exemple :

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Les fonctions membres statiques, car ils existent au niveau de la classe et non comme faisant partie d’un objet, n’ont pas de pointeur `this`. Une erreur consiste à faire référence à `this` dans une méthode statique.

## <a name="example"></a> Exemple

Dans cet exemple, `this` est utilisé pour qualifier les membres de la classe `Employee`, `name` et `alias`, qui sont masqués par des noms similaires. Il est également utilisé pour passer un objet à la méthode `CalcTax`, qui appartient à une autre classe.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [base](base.md)
- [Méthodes](../../programming-guide/classes-and-structs/methods.md)
