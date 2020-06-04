---
title: <message> Cette erreur peut résulter de la combinaison d’une référence de fichier et d’une référence de projet pour l’assembly <assemblyname>
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 263e30f992ef58b0053acb2fd749d0d9186ef6b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397257"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>\<message> Cette erreur peut résulter de la combinaison d’une référence de fichier et d’une référence de projet pour l’assembly \<assemblyname>
\<message>Cette erreur peut également être due à la combinaison d’une référence de fichier et d’une référence de projet à l’assembly' \<assemblyname> . Dans ce cas, essayez de remplacer la référence de fichier à' \<assemblyfilename> 'dans le projet' \<projectname1> 'par une référence de projet à' \<projectname2> '.  
  
 Le code de votre projet accède à un membre d’un autre projet, mais la configuration de votre solution n’autorise pas le compilateur Visual Basic à résoudre la référence.  
  
 Pour accéder à un type défini dans un autre assembly, le compilateur Visual Basic doit avoir une référence à cet assembly. Cette référence doit être unique et non équivoque et elle ne doit pas provoquer de références circulaires entre les projets.  
  
 **ID d’erreur :** BC30971  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer. Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.  
  
2. Dans les propriétés de votre projet, ajoutez une référence au projet contenant l’assembly qui définit le type que vous utilisez.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)
- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
- [Dépannage de références rompues](/visualstudio/ide/troubleshooting-broken-references)
