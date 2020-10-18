---
title: Le nom <namespacename> de l'espace de noms racine <fullnamespacename> n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 48e020cb74641279a4f402e47034514d78dfc4fc
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160208"
---
# <a name="bc40039-name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>BC40039 : \<namespacename> le nom dans l’espace de noms racine \<fullnamespacename> n’est pas conforme CLS

Un assembly est marqué comme `<CLSCompliant(True)>` , mais un élément du nom de l’espace de noms racine commence par un trait de soulignement ( `_` ).

 Un élément de programmation peut contenir un ou plusieurs traits de soulignement, mais pour être conforme à l' [indépendance du langage et aux composants de Language-Independent](../../../standard/language-independence-and-language-independent-components.md) (CLS), il ne doit pas commencer par un trait de soulignement. Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).

 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.

 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.

 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC40039

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si la conformité CLS est nécessaire, modifiez le nom de l’espace de noms racine afin qu’aucun de ses éléments ne commence par un trait de soulignement.

- Si vous avez besoin que le nom de l’espace de noms reste inchangé, supprimez <xref:System.CLSCompliantAttribute> de l’assembly ou marquez-le comme `<CLSCompliant(False)>` .

## <a name="see-also"></a>Voir aussi

- [Namespace, instruction](../statements/namespace-statement.md)
- [Espaces de noms dans Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [-rootnamespace](../../reference/command-line-compiler/rootnamespace.md)
- [Page Application, Concepteur de projet (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Conventions d'affectation de noms Visual Basic](../../programming-guide/program-structure/naming-conventions.md)
