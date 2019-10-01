---
title: Opérateur IsNot (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 32e8f9532244679d2994b0e3d98279d75f7e77b4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701040"
---
# <a name="isnot-operator-visual-basic"></a>Opérateur IsNot (Visual Basic)

Compare deux variables de référence d’objet.

## <a name="syntax"></a>Syntaxe

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Composants
 `result` Obligatoire. Valeur `Boolean`.

 `object1` Obligatoire. Toute variable ou expression `Object`.

 `object2` Obligatoire. Toute variable ou expression `Object`.

## <a name="remarks"></a>Notes
 L’opérateur `IsNot` détermine si deux références d’objet font référence à des objets différents. Toutefois, il n’effectue pas de comparaisons de valeurs. Si `object1` et `object2` font tous deux référence à la même instance d’objet, `result` est `False` ; Si ce n’est pas le cas, `result` est `True`.

 `IsNot` est l’opposé de l’opérateur `Is`. L’avantage de `IsNot` est que vous pouvez éviter la syntaxe maladroite avec `Not` et `Is`, ce qui peut être difficile à lire.

 Vous pouvez utiliser les opérateurs `Is` et `IsNot` pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.

## <a name="example"></a>Exemple
 L’exemple de code suivant utilise à la fois l’opérateur `Is` et l’opérateur `IsNot` pour effectuer la même comparaison.

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>Voir aussi

- [Is (opérateur)](is-operator.md)
- [TypeOf (opérateur)](typeof-operator.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Guide pratique pour Teste si deux objets sont identiques à @ no__t-0
