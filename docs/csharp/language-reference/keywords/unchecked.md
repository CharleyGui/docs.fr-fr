---
description: unchecked, mot clé - Référence C#
title: unchecked, mot clé - Référence C#
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: bb66639e3657b247b9ebcad1594daf1f57a5c76b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141983"
---
# <a name="unchecked-c-reference"></a>unchecked (référence C#)

Le mot clé `unchecked` permet de supprimer le contrôle de dépassement de capacité pour les conversions et les opérations arithmétiques de type intégral.

Dans un contexte non vérifié (unchecked), si une expression produit une valeur située hors de la plage du type de destination, le dépassement de capacité n’est pas signalé. Par exemple, comme le calcul dans l’exemple suivant s’effectue dans un bloc ou une expression `unchecked`, le fait que le résultat est trop grand pour un entier est ignoré et `int1` se voit assigner la valeur -2,147,483,639.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

Si l’environnement `unchecked` est supprimé, une erreur de compilation se produit. Le dépassement de capacité peut être détecté au moment de la compilation, car tous les termes de l’expression sont des constantes.

Les expressions qui contiennent des termes non constants sont non vérifiées par défaut au moment de la compilation et de l’exécution. Consultez [checked](checked.md) pour plus d’informations sur l’activation d’un environnement vérifié (checked).

Étant donné que la vérification de dépassement de capacité prend du temps, l’utilisation de code non vérifié dans les situations où il n’existe aucun danger de dépassement de capacité peut améliorer les performances. Toutefois, si un dépassement de capacité est possible, il convient d’utiliser un environnement vérifié (checked).

## <a name="example"></a>Exemple

L’exemple de code suivant montre comment utiliser le mot clé `unchecked`.

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Checked et unchecked](checked-and-unchecked.md)
- [désactivé](checked.md)
