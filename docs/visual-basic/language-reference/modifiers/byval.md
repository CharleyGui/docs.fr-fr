---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: c4cdafafa6bae3246c0512e28f94fde7e88d230b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373022"
---
# <a name="byval-visual-basic"></a>Byval (Visual Basic)
Spécifie qu’un argument est passé [par valeur](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), de sorte que la procédure ou propriété appelée ne peut pas modifier la valeur d’une variable sous-jacente à l’argument dans le code appelant. Si aucun modificateur n’est spécifié, ByVal est la valeur par défaut.

> [!NOTE]
> Étant donné qu’il s’agit de la valeur par défaut, il n’est pas nécessaire de spécifier explicitement le `ByVal` mot clé dans les signatures de méthode. Il a tendance à produire du code bruyant et entraîne souvent un surexamen du mot clé non défini par défaut `ByRef` .

## <a name="remarks"></a>Notes
 Le modificateur `ByVal` peut être utilisé dans les contextes suivants :

 [Declare Statement](../statements/declare-statement.md)

 [Function (instruction)](../statements/function-statement.md)
  
 [Operator Statement](../statements/operator-statement.md)
  
 [Property Statement](../statements/property-statement.md)
  
 [Sub (instruction)](../statements/sub-statement.md)

## <a name="example"></a>Exemple
 L’exemple suivant illustre l’utilisation du `ByVal` mécanisme de passage de paramètre avec un argument de type référence. Dans l’exemple, l’argument est `c1` , une instance de la classe `Class1` . `ByVal`empêche le code des procédures de modifier la valeur sous-jacente de l’argument de référence, `c1` , mais ne protège pas les champs et les propriétés accessibles de `c1` .

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Voir aussi

- [Mots clés](../keywords/index.md)
- [Passage des arguments par valeur et par référence](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
