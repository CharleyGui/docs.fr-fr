---
title: Le nom <membername> n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 43fff3f12295f3837148b0a349887e8405126819
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160234"
---
# <a name="bc40031-name-membername-is-not-cls-compliant"></a>BC40031 : \<membername> le nom n’est pas conforme CLS

Un assembly est marqué comme, `<CLSCompliant(True)>` mais expose un membre avec un nom qui commence par un trait de soulignement ( `_` ).

 Un élément de programmation peut contenir un ou plusieurs traits de soulignement, mais pour être conforme à l' [indépendance du langage et aux composants de Language-Independent](../../../standard/language-independence-and-language-independent-components.md) (CLS), il ne doit pas commencer par un trait de soulignement. Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).

 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.

 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.

 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC40031

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si vous contrôlez le code source, modifiez le nom du membre afin qu’il ne commence pas par un trait de soulignement.

- Si vous avez besoin que le nom du membre reste inchangé, supprimez <xref:System.CLSCompliantAttribute> de sa définition ou marquez-le comme `<CLSCompliant(False)>` . Vous pouvez toujours marquer l’assembly comme `<CLSCompliant(True)>` .

## <a name="see-also"></a>Voir aussi

- [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Conventions d'affectation de noms Visual Basic](../../programming-guide/program-structure/naming-conventions.md)
