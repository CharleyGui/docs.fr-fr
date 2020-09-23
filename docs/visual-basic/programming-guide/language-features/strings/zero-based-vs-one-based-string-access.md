---
title: Accès à une chaîne de base zéro et à un
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 91d3fb9d7bfdf3d5af27fc6499583640946a802f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072286"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Accès à une chaîne de base zéro et accès à une chaîne de base un en Visual Basic

Cette rubrique compare comment Visual Basic et les .NET Framework fournissent l’accès aux caractères d’une chaîne. Le .NET Framework fournit toujours un accès de base zéro aux caractères d’une chaîne, tandis que Visual Basic fournit un accès de base zéro et un accès de base zéro, selon la fonction.  
  
## <a name="one-based"></a>Basé sur un  

 Pour obtenir un exemple d’une fonction de Visual Basic basée sur un, considérez la `Mid` fonction. Il accepte un argument qui indique la position de caractère à laquelle la sous-chaîne commencera, en commençant par la position 1. La <xref:System.String.Substring%2A?displayProperty=nameWithType> méthode .NET Framework prend un index du caractère dans la chaîne à laquelle la sous-chaîne doit commencer, en commençant par la position 0. Ainsi, si vous avez une chaîne « ABCDe », les caractères individuels sont numérotés 1, 2, 3, 4, 5 pour une utilisation avec la `Mid` fonction, mais 0, 1, 2, 3, 4 pour une utilisation avec la <xref:System.String.Substring%2A?displayProperty=nameWithType> méthode.  
  
## <a name="zero-based"></a>De base zéro  

 Pour obtenir un exemple de fonction Visual Basic de base zéro, considérez la `Split` fonction. Il fractionne une chaîne et retourne un tableau contenant les sous-chaînes. La <xref:System.String.Split%2A?displayProperty=nameWithType> méthode .NET Framework fractionne également une chaîne et retourne un tableau contenant les sous-chaînes. Étant donné que la `Split` fonction et la <xref:System.String.Split%2A> méthode retournent des tableaux .NET Framework, ils doivent être de base zéro.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Introduction aux chaînes en Visual Basic](introduction-to-strings.md)
