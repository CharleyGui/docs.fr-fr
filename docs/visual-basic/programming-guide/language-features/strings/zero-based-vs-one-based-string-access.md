---
title: Accès à une chaîne de base zéro et à un
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 97e60038bc7ec0f030939d0980b786bffebcfb9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354301"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Accès à une chaîne de base zéro et accès à une chaîne de base un en Visual Basic
Cette rubrique compare comment Visual Basic et les .NET Framework fournissent l’accès aux caractères d’une chaîne. Le .NET Framework fournit toujours un accès de base zéro aux caractères d’une chaîne, tandis que Visual Basic fournit un accès de base zéro et un accès de base zéro, selon la fonction.  
  
## <a name="one-based"></a>Basé sur un  
 Pour obtenir un exemple d’une fonction de Visual Basic basée sur un, prenez en compte la fonction `Mid`. Il accepte un argument qui indique la position de caractère à laquelle la sous-chaîne commencera, en commençant par la position 1. La méthode .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> prend un index du caractère dans la chaîne à laquelle la sous-chaîne doit commencer, en commençant par la position 0. Ainsi, si vous avez une chaîne « ABCDe », les caractères individuels sont numérotés 1, 2, 3, 4, 5 pour une utilisation avec la fonction `Mid`, mais 0, 1, 2, 3, 4 pour une utilisation avec la méthode <xref:System.String.Substring%2A?displayProperty=nameWithType>.  
  
## <a name="zero-based"></a>De base zéro  
 Pour obtenir un exemple de fonction Visual Basic de base zéro, prenez en compte la fonction `Split`. Il fractionne une chaîne et retourne un tableau contenant les sous-chaînes. La méthode .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> fractionne également une chaîne et retourne un tableau contenant les sous-chaînes. Étant donné que la fonction `Split` et <xref:System.String.Split%2A> méthode retournent des tableaux .NET Framework, ils doivent être de base zéro.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
