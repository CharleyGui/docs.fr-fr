---
title: namespace, mot clé - Référence C#
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 04595e96f6f14b8806a2d89625151910cac9e0d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345424"
---
# <a name="namespace-c-reference"></a>namespace (référence C#)

Le mot clé `namespace` est utilisé pour déclarer une portée qui contient un ensemble d’objets connexes. Vous pouvez utiliser un espace de noms pour organiser les éléments de code et créer des types globaux uniques.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Notes

Dans un espace de noms, vous pouvez déclarer zéro ou plusieurs des types suivants :

- autre espace de noms

- [classe](class.md)

- [interface](interface.md)

- [struct](struct.md)

- [enum](../builtin-types/enum.md)

- [delegate](../builtin-types/reference-types.md#the-delegate-type)

Le compilateur ajoute un espace de noms par défaut, que vous déclariez ou non explicitement un espace de noms dans un fichier source C#. Cet espace de noms sans nom, parfois appelé espace de noms global, est présent dans chaque fichier. Tout identificateur dans l’espace de noms global peut être utilisé dans un espace de noms nommé.

Les espaces de noms ont implicitement un accès public, et cela n’est pas modifiable. Consultez [Modificateurs d’accès](access-modifiers.md) pour connaître les modificateurs d’accès que vous pouvez assigner à des éléments dans un espace de noms.

Il est possible de définir un espace de noms dans deux déclarations ou plus. Par exemple, l’exemple suivant définit deux classes comme appartenant à l’espace de noms `MyCompany` :

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Exemple

L’exemple suivant montre comment appeler une méthode statique dans un espace de noms imbriqué.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Espace de noms](~/_csharplang/spec/namespaces.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Mots clés C#](index.md)
- [using](using-directive.md)
- [using static](using-static.md)
- [Qualificateur d’alias d’espace de noms`::`](../operators/namespace-alias-qualifier.md)
- [Espaces de noms](../../programming-guide/namespaces/index.md)
