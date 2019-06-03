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
ms.openlocfilehash: df921ecc670bf12411dc8b0d828d6c19bb0a1aec
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422746"
---
# <a name="namespace-c-reference"></a>namespace (référence C#)

Le mot clé `namespace` est utilisé pour déclarer une portée qui contient un ensemble d’objets connexes. Vous pouvez utiliser un espace de noms pour organiser les éléments de code et créer des types globaux uniques.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Remarques

Dans un espace de noms, vous pouvez déclarer zéro ou plusieurs des types suivants :

- autre espace de noms

- [class](class.md)

- [interface](interface.md)

- [struct](struct.md)

- [enum](enum.md)

- [delegate](delegate.md)

Le compilateur ajoute un espace de noms par défaut, que vous déclariez ou non explicitement un espace de noms dans un fichier source C#. Cet espace de noms sans nom, parfois appelé espace de noms global, est présent dans chaque fichier. Tout identificateur dans l’espace de noms global peut être utilisé dans un espace de noms nommé.

Les espaces de noms ont implicitement un accès public, et cela n’est pas modifiable. Consultez [Modificateurs d’accès](access-modifiers.md) pour connaître les modificateurs d’accès que vous pouvez assigner à des éléments dans un espace de noms.

Il est possible de définir un espace de noms dans deux déclarations ou plus. Par exemple, l’exemple suivant définit deux classes comme appartenant à l’espace de noms `MyCompany` :

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Exemple

L’exemple suivant montre comment appeler une méthode statique dans un espace de noms imbriqué.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a>Ressources connexes

Pour plus d’informations sur l’utilisation des espaces de noms, consultez les rubriques suivantes :

- [Espaces de noms](../../programming-guide/namespaces/index.md)

- [Utilisation d’espaces de noms](../../programming-guide/namespaces/using-namespaces.md)

- [Guide pratique pour utiliser l’alias d’espace de noms global](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../../language-reference/index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [using](using-directive.md)
- [using static](using-static.md)
