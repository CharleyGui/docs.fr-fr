---
title: Une référence à l'assembly '<assemblyidentity>' contenant le type '<typename>' est requise, mais une référence adéquate n'a pas été trouvée en raison de l'ambiguïté entre les projets '<projectname1>' et '<projectname2>'
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: ca574bfe926b7b9df272e296190b36f8635263db
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162308"
---
# <a name="bc30969-reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a>BC30969 : une référence à l’assembly' \<assemblyidentity> 'contenant le type' 'est requise \<typename> , mais une référence appropriée n’a pas pu être trouvée en raison de l’ambiguïté entre les projets' \<projectname1> 'et' \<projectname2> '

Une expression utilise un type, comme une classe, une structure, une interface, une énumération ou un délégué, qui est défini en dehors de votre projet. Cependant, des références de projet désignent plusieurs assemblys définissant ce type.

 Les projets cités produisent des assemblys de même nom. Par conséquent, le compilateur ne peut pas déterminer quel assembly utiliser pour le type auquel vous accédez.

 Pour accéder à un type défini dans un autre assembly, le compilateur Visual Basic doit avoir une référence à cet assembly. Cette référence doit être unique et non équivoque et elle ne doit pas provoquer de références circulaires entre les projets.

 **ID d’erreur :** BC30969

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer. Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.

2. Dans vos propriétés de projet, ajoutez une référence au fichier qui contient l’assembly qui définit le type que vous utilisez.

## <a name="see-also"></a>Voir aussi

- [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)
- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
- [Dépannage de références rompues](/visualstudio/ide/troubleshooting-broken-references)
