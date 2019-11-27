---
title: Nothing et chaînes
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: dfc43748d0754f0a6a29763c42ab82d9937f89f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344294"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Nothing et les chaînes en Visual Basic
Le runtime Visual Basic et le .NET Framework évaluent `Nothing` différemment lorsqu’il s’agit de chaînes.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic Runtime et le .NET Framework  
 Prenons l'exemple suivant :  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Le runtime Visual Basic évalue généralement `Nothing` comme une chaîne vide (""). Toutefois, le .NET Framework ne lève pas d’exception et lève une exception chaque fois qu’une tentative est effectuée pour effectuer une opération de chaîne sur `Nothing`.  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
