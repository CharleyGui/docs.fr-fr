---
title: Erase (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 31aeaf822bc9c1de59a5c5f68406c6521216ae0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404717"
---
# <a name="erase-statement-visual-basic"></a>Erase, instruction (Visual Basic)
Utilisé pour libérer des variables de tableau et libérer la mémoire utilisée pour leurs éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>Éléments  
 `arraylist`  
 Obligatoire. Liste des variables de tableau à effacer. Les variables multiples sont séparées par des virgules.  
  
## <a name="remarks"></a>Notes  
 L' `Erase` instruction peut apparaître uniquement au niveau de la procédure. Cela signifie que vous pouvez libérer des tableaux à l’intérieur d’une procédure, mais pas au niveau de la classe ou du module.  
  
 L' `Erase` instruction équivaut à assigner `Nothing` à chaque variable de tableau.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `Erase` instruction pour effacer deux tableaux et libérer leur mémoire (respectivement les éléments de stockage 1000 et 100). L' `ReDim` instruction assigne ensuite une nouvelle instance de tableau au tableau à trois dimensions.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Voir aussi

- [Résultat](../nothing.md)
- [ReDim (instruction)](redim-statement.md)
