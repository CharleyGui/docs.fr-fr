---
title: Longueur d'enregistrement incorrecte
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 7ec0a8c27f425ec717bca5d45d5dfd2b601c11d5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665733"
---
# <a name="bad-record-length"></a>Longueur d'enregistrement incorrecte
Cette erreur peut avoir plusieurs causes, dont les suivantes :  
  
- La longueur d’une variable de l’enregistrement spécifiée dans une `FileGet`, `FileGetObject`, `FilePut` ou `FilePutObject` instruction diffère de la longueur spécifiée dans le correspondantes `FileOpen` instruction.  
  
- La variable dans un `FilePut` ou `FilePutObject` instruction est ou inclut une chaîne de longueur variable.  
  
- La variable dans un `FilePut` ou `FilePutObject` est ou inclut un `Variant` type.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous que la somme des tailles des variables de longueur fixe dans le type défini par l’utilisateur définissant le type de la variable d’enregistrement est identique à la valeur indiquée dans le `FileOpen` l’instruction `Len` clause.  
  
2. Si la variable dans un `FilePut` ou `FilePutObject` instruction est ou inclut une chaîne de longueur variable, vérifiez que la chaîne de longueur variable est au moins 2 caractères plus courtes que la longueur d’enregistrement spécifiée dans le `Len` clause de le `FileOpen` instruction.  
  
3. Si la variable dans un `FilePut` ou `FilePutObject` est ou inclut un `Variant` Assurez-vous que la chaîne de longueur variable est plus court que la longueur d’enregistrement spécifiée dans au moins 4 octets le `Len` clause de la `FileOpen` instruction.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
