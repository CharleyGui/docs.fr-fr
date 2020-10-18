---
title: Une référence à l'assembly '<assemblyname>' contenant la classe de base '<classname>' est requise
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: d2fb3498219dfe3318ec418ede250de818874ba9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162334"
---
# <a name="bc30007-reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a>BC30007 : une référence à l’assembly' \<assemblyname> 'contenant la classe de base' 'est requise \<classname>

Une référence à l’assembly' \<assemblyname> 'contenant la classe de base' 'est requise \<classname> . Ajoutez-en une à votre projet.

 La classe est définie dans une bibliothèque de liens dynamiques (DLL) ou un assembly qui n’est pas directement référencé dans votre projet. Le compilateur Visual Basic requiert une référence pour éviter toute ambiguïté au cas où la classe serait définie dans plusieurs DLL ou assemblys.

 **ID d’erreur :** BC30007

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Incluez le nom de la DLL ou de l’assembly non référencé dans vos références de projet.

## <a name="see-also"></a>Voir aussi

- [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)
- [Dépannage de références rompues](/visualstudio/ide/troubleshooting-broken-references)
