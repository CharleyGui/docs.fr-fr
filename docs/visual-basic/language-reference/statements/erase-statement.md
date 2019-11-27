---
title: Erase, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 6d2052ceccbecd772c4e4bb18052aed74223a36e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343698"
---
# <a name="erase-statement-visual-basic"></a>Erase, instruction (Visual Basic)
Utilisé pour libérer des variables de tableau et libérer la mémoire utilisée pour leurs éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>Composants  
 `arraylist`  
 Requis. Liste des variables de tableau à effacer. Les variables multiples sont séparées par des virgules.  
  
## <a name="remarks"></a>Notes  
 L’instruction `Erase` peut apparaître uniquement au niveau de la procédure. Cela signifie que vous pouvez libérer des tableaux à l’intérieur d’une procédure, mais pas au niveau de la classe ou du module.  
  
 L’instruction `Erase` équivaut à assigner des `Nothing` à chaque variable de tableau.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’instruction `Erase` pour effacer deux tableaux et libérer leur mémoire (respectivement les éléments de stockage 1000 et 100). L’instruction `ReDim` affecte ensuite une nouvelle instance de tableau au tableau à trois dimensions.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Voir aussi

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim (instruction)](../../../visual-basic/language-reference/statements/redim-statement.md)
