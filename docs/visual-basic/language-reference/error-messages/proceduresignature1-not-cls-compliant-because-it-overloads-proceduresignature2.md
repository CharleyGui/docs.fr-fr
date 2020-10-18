---
title: <proceduresignature1> n’est pas conforme au CLS, car il surcharge <proceduresignature2> dont il diffère uniquement par un tableau de types de paramètres tableau ou par la dimension des types de paramètres tableau
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 5376f0513b1180da511a508cf8e0e754e8938384
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159792"
---
# <a name="bc40035-proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>BC40035 : \<proceduresignature1> n’est pas conforme CLS, car il surcharge \<proceduresignature2> qui diffère de celui-ci uniquement par un tableau de types de paramètres tableau ou par le rang des types de paramètres tableau

Une procédure ou une propriété est marquée comme `<CLSCompliant(True)>` quand elle substitue une autre procédure ou propriété, et la seule différence entre leurs listes de paramètres est le niveau d’imbrication d’un tableau en escalier ou le rang d’un tableau.

 Dans les déclarations suivantes, les deuxième et troisième déclarations génèrent cette erreur :

 `Overloads Sub ProcessArray(arrayParam() As Integer)`

 `Overloads Sub ProcessArray(arrayParam()() As Integer)`

 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`

 La deuxième déclaration remplace le paramètre unidimensionnel d’origine `arrayParam` par un tableau de tableaux. La troisième déclaration est remplacée `arrayParam` par un tableau à deux dimensions (rang 2). Bien que Visual Basic permette aux surcharges de différer uniquement par l’une de ces modifications, cette surcharge n’est pas conforme à l' [indépendance du langage et aux composants de Language-Independent](../../../standard/language-independence-and-language-independent-components.md) (CLS).

 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.

 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.

 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC40035

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si vous avez besoin de la conformité CLS, définissez vos surcharges pour qu’elles diffèrent les unes des autres de manière plus que seules les modifications mentionnées dans cette page d’aide.
- Si vous avez besoin que les surcharges diffèrent uniquement par les modifications mentionnées dans cette page d’aide, supprimez <xref:System.CLSCompliantAttribute> de leurs définitions ou marquez-les comme `<CLSCompliant(False)>` .

## <a name="see-also"></a>Voir aussi

- [Surcharge de procédure](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Surcharges](../modifiers/overloads.md)
