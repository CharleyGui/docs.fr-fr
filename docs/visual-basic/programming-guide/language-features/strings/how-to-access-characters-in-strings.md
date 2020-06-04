---
title: 'Comment : accéder aux caractères dans les chaînes'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: fa5920cfd25f61f6e6c7d5438ef7c0e38a48fa1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401951"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Comment : accéder aux caractères dans les chaînes en Visual Basic
Cet exemple montre comment utiliser la <xref:System.String.Chars%2A> propriété pour accéder au caractère à l’emplacement spécifié dans une chaîne.  
  
## <a name="example"></a>Exemple  
 Il est parfois utile d’avoir des données sur les caractères de votre chaîne et les positions de ces caractères dans la chaîne. Vous pouvez considérer une chaîne comme un tableau de caractères ( `Char` instances); vous pouvez récupérer un caractère particulier en référençant l’index de ce caractère par le biais de la <xref:System.String.Chars%2A> propriété.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 Le `index` paramètre de la <xref:System.String.Chars%2A> propriété est de base zéro.  
  
## <a name="robust-programming"></a>Programmation fiable  
 La <xref:System.String.Chars%2A> propriété retourne le caractère à la position spécifiée. Toutefois, certains caractères Unicode peuvent être représentés par plusieurs caractères. Pour plus d’informations sur l’utilisation des caractères Unicode, consultez [Comment : convertir une chaîne en tableau de caractères](how-to-convert-a-string-to-an-array-of-characters.md).  
  
 La <xref:System.String.Chars%2A> propriété lève une <xref:System.IndexOutOfRangeException> exception si le `index` paramètre est supérieur ou égal à la longueur de la chaîne, ou s’il est inférieur à zéro  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.String.Chars%2A>
- [Guide pratique : convertir une chaîne en tableau de caractères](how-to-convert-a-string-to-an-array-of-characters.md)
- [Conversion entre chaînes et d'autres types de données en Visual Basic](converting-between-strings-and-other-data-types.md)
- [Chaînes](index.md)
