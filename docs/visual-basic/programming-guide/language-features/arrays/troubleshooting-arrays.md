---
title: Dépannage des tableaux
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 3c50c68c2a39aa04cff2dd43b5dfde709aec290f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349063"
---
# <a name="troubleshooting-arrays-visual-basic"></a>Dépannage des tableaux (Visual Basic)
Cette page répertorie certains problèmes courants qui peuvent se produire lors de l’utilisation de tableaux.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Erreurs de compilation lors de la déclaration et de l’initialisation d’un tableau  
 Les erreurs de compilation peuvent provenir d’une mauvaise compréhension des règles de déclaration, de création et d’initialisation de tableaux. Les causes les plus courantes des erreurs sont les suivantes :  
  
- En fournissant une [nouvelle](../../../../visual-basic/language-reference/operators/new-operator.md) clause d’opérateur après avoir spécifié des longueurs de dimensions dans la déclaration de variable de tableau. Les lignes de code suivantes affichent des déclarations non valides de ce type.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- Spécification des longueurs de dimensions pour plus que le tableau de niveau supérieur d’un tableau en escalier. La ligne de code suivante montre une déclaration non valide de ce type.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- Omission du mot clé `New` lors de la spécification des valeurs de l’élément. La ligne de code suivante montre une déclaration non valide de ce type.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- Spécification d’une clause `New` sans accolades (`{}`). Les lignes de code suivantes affichent des déclarations non valides de ce type.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Accès à un tableau hors limites  
 Le processus d’initialisation d’un tableau assigne une limite supérieure et une limite inférieure à chaque dimension. Chaque accès à un élément du tableau doit spécifier un index valide, ou indice, pour chaque dimension. Si un index est inférieur à sa limite inférieure ou au-dessus de sa limite supérieure, une <xref:System.IndexOutOfRangeException> exception se produit. Le compilateur ne peut pas détecter une telle erreur, de sorte qu’une erreur se produit au moment de l’exécution.  
  
### <a name="determining-bounds"></a>Détermination des limites  
 Si un autre composant passe un tableau à votre code, par exemple en tant qu’argument de procédure, vous ne connaissez pas la taille de ce tableau ni les longueurs de ses dimensions. Vous devez toujours déterminer la limite supérieure pour chaque dimension d’un tableau avant de tenter d’accéder à tous les éléments. Si le tableau a été créé par d’autres moyens que la clause Visual Basic `New`, la limite inférieure peut être différente de 0, et il est plus sûr de déterminer également la limite inférieure.  
  
### <a name="specifying-the-dimension"></a>Spécification de la dimension  
 Lorsque vous déterminez les limites d’un tableau multidimensionnel, prenez soin de la façon dont vous spécifiez la dimension. Les paramètres `dimension` des méthodes <xref:System.Array.GetLowerBound%2A> et <xref:System.Array.GetUpperBound%2A> sont basés sur 0, tandis que les paramètres `Rank` des fonctions Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> et <xref:Microsoft.VisualBasic.Information.UBound%2A> sont basés sur 1.  
  
## <a name="see-also"></a>Voir aussi

- [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Comment : initialiser une variable tableau en Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
