---
title: Le <membername> non conforme CLS n'est pas autorisé dans une interface conforme CLS
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: aa7944e90857436553435ce783c0820770496a49
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159987"
---
# <a name="bc40033-non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a>BC40033 : non conforme CLS \<membername> n’est pas autorisé dans une interface conforme CLS

Une propriété, une procédure ou un événement dans une interface est marqué comme `<CLSCompliant(True)>` lorsque l’interface elle-même est marquée comme `<CLSCompliant(False)>` ou n’est pas marquée.

 Pour qu’une interface soit conforme à l' [indépendance du langage et aux composants de Language-Independent](../../../standard/language-independence-and-language-independent-components.md) (CLS), tous ses membres doivent être conformes.

 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.

 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.

 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC40033

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si la conformité CLS est requise et si vous contrôlez le code source de l’interface, marquez l’interface comme `<CLSCompliant(True)>` si tous ses membres étaient conformes.

- Si vous avez besoin de la conformité CLS et que vous n’avez pas le contrôle du code source de l’interface, ou s’il n’est pas qualifié pour être conforme, définissez ce membre dans une autre interface.

- Si vous avez besoin que ce membre reste dans son interface actuelle, supprimez <xref:System.CLSCompliantAttribute> de sa définition ou marquez-le comme `<CLSCompliant(False)>` .

## <a name="see-also"></a>Voir aussi

- [Interface (instruction)](../statements/interface-statement.md)
