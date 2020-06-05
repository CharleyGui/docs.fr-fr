---
title: L'espace de noms ou le type spécifié dans les Imports '<qualifiedelementname>' au niveau du projet ne contient aucun membre public ou est introuvable
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 0ee235252d69e6f77ce53b048f45e73d0969e864
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409450"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>L'espace de noms ou le type spécifié dans les Imports '\<qualifiedelementname>' au niveau du projet ne contient aucun membre public ou est introuvable
L’espace de noms ou le type spécifié dans les importations au niveau du projet' \<qualifiedelementname> 'ne contient aucun membre public ou est introuvable. Assurez-vous que l’espace de noms ou le type est défini et contient au moins un membre public. Assurez-vous que le nom d’alias ne contient pas d’autres alias.  
  
 Une propriété d’importation d’un projet spécifie un élément conteneur qui est introuvable ou ne définit aucun `Public` membre.  
  
 Un *élément conteneur* peut être un espace de noms, une classe, une structure, un module, une interface ou une énumération. L’élément conteneur contient des membres, tels que des variables, des procédures ou d’autres éléments conteneurs.  
  
 L’objectif de l’importation est de permettre à votre code d’accéder à des membres de type ou d’espace de noms sans avoir à les qualifier. Votre projet peut également avoir besoin d’ajouter une référence à l’espace de noms ou au type. Pour plus d’informations, consultez « importation d’éléments contenants » dans les [références aux éléments déclarés](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Si le compilateur ne peut pas trouver l’élément conteneur spécifié, il ne peut pas résoudre les références qui l’utilisent. S’il trouve l’élément mais que l’élément n’expose aucun `Public` membre, aucune référence ne peut être effectuée. Dans les deux cas, il est inutile d’importer l’élément.  
  
 Vous utilisez le **Concepteur de projet** pour spécifier les éléments à importer. Utilisez la section **espaces de noms importés** de la page **références** . Vous pouvez accéder au **Concepteur de projets** en double-cliquant sur l’icône **mon projet** dans **Explorateur de solutions**.  
  
 **ID d’erreur :** BC40057  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Ouvrez le **Concepteur de projets** et basculez vers la page de **référence** .  
  
2. Dans la section **espaces de noms importés** , vérifiez que l’élément conteneur est accessible à partir de votre projet.  
  
3. Vérifiez que l’élément conteneur expose au moins un `Public` membre.  
  
## <a name="see-also"></a>Voir aussi

- [Page Références, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
- [Public](../modifiers/public.md)
- [Espaces de noms dans Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
