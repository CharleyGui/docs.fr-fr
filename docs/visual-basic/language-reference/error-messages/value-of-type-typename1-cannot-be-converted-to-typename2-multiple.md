---
title: La valeur du type '<typename1>' ne peut pas être convertie en '<typename2>' (plusieurs références de fichier)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 25008f05979638e050b74fc659fdc0a6d13b3c31
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406584"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>La valeur du type '\<typename1>' ne peut pas être convertie en '\<typename2>' (plusieurs références de fichier)
Impossible de convertir la valeur de type' ' \<typename1> en' \<typename2> '. Une incompatibilité de type peut être due à la combinaison d’une référence de fichier à' \<filepath1> 'dans le projet' \<projectname1> 'avec une référence de fichier à' \<filepath2> 'dans le projet' \<projectname2> '. Si les deux assemblys sont identiques, essayez de remplacer ces deux références pour qu’elles se situent au même emplacement.  
  
 Dans le cas où un projet crée plusieurs références de fichier à un assembly, le compilateur ne peut pas garantir qu’un type peut être converti en un autre.  
  
 Chaque référence de fichier spécifie un chemin d’accès et un nom de fichier pour le fichier de sortie d’un projet (en général, un fichier DLL). Le compilateur ne peut pas garantir que les fichiers de sortie proviennent de la même source, ou qu’ils représentent la même version du même assembly. Par conséquent, il ne peut pas garantir que les types des différentes références sont du même type, ou qu’il peut être converti en l’un l’autre.  
  
 Vous pouvez utiliser une référence de fichier unique si vous savez que les assemblys référencés ont la même identité d’assembly. L' *identité de l’assembly* comprend le nom de l’assembly, sa version, sa clé publique, le cas échéant, et la culture. Ces informations identifient de manière unique l’assembly.  
  
 **ID d’erreur :** BC30961  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si les assemblys référencés ont la même identité d’assembly, supprimez ou remplacez l’une des références de fichier pour qu’il n’y ait qu’une seule référence de fichier.  
  
- Si les assemblys référencés n’ont pas la même identité d’assembly, modifiez votre code afin qu’il n’essaie pas de convertir un type en un type dans l’autre.  
  
## <a name="see-also"></a>Voir aussi

- [Conversions de type en Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
- [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)
