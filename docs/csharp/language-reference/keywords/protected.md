---
title: protected, mot clé - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: f54c3f36e5aeb428815d1c49cd797e559d156ea7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422564"
---
# <a name="protected-c-reference"></a>protected (référence C#)

Le mot clé `protected` est un modificateur d’accès de membre.

 > Cette page traite de l’accès `protected`. Le mot clé `protected` fait également partie des modificateurs d’accès [`protected internal`](protected-internal.md) et [`private protected`](private-protected.md).

Un membre protégé est accessible dans sa classe et par les instances de la classe dérivée.

Pour obtenir une comparaison de `protected` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](accessibility-levels.md).

## <a name="example"></a>Exemple

Un membre protégé d’une classe de base est accessible dans une classe dérivée uniquement si l’accès s’effectue par le biais du type de la classe dérivée. Prenons l’exemple de l’extrait de code suivant :

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

L’instruction `a.x = 10` génère une erreur, car elle est appelée dans la méthode statique Main, et pas dans une instance de la classe B.

Les membres de struct ne peuvent pas être protégés, car le struct ne peut pas être hérité.

## <a name="example"></a>Exemple

Dans cet exemple, la classe `DerivedPoint` est dérivée de `Point`. Vous pouvez donc accéder aux membres protégés de la classe de base directement à partir de la classe dérivée.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

Si vous changez les niveaux d’accès de `x` et `y` à [private](private.md), le compilateur affiche les messages d’erreur suivants :

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>spécification du langage C#  

Pour plus d’informations, consultez [Accessibilité déclarée](~/_csharplang/spec/basic-concepts.md#declared-accessibility) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Modificateurs d’accès](access-modifiers.md)
- [Niveaux d’accessibilité](accessibility-levels.md)
- [Modificateurs](index.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Problèmes de sécurité pour les mots clés virtuels internes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
