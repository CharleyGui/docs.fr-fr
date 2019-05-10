---
title: <proceduresignature1> n’est pas conforme CLS, car il surcharge <proceduresignature2> dont il diffère uniquement par un tableau de types de paramètres tableau ou par la dimension des types de paramètres tableau
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 9006e12838581a98c7e7945278c7d767a3074259
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661782"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>\<proceduresignature1 > n’est pas conforme CLS, car il surcharge \<proceduresignature2 > dont il diffère uniquement par un tableau de types de paramètres tableau ou par la dimension des types de paramètres tableau
Une procédure ou la propriété est marquée comme `<CLSCompliant(True)>` quand il substitue à une autre procédure ou propriété et la seule différence entre leurs listes de paramètres est le niveau d’imbrication d’un tableau en escalier ou le rang d’un tableau.  
  
 Dans les déclarations suivantes, les deuxième et troisième déclarations génèrent cette erreur.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 La deuxième déclaration remplace le paramètre unidimensionnel d’origine `arrayParam` à un tableau de tableaux. La troisième déclaration remplace `arrayParam` un tableau à deux dimensions (rang 2). Bien que Visual Basic autorise les surcharges à différer uniquement par l’une de ces modifications, une telle surcharge n’est pas conforme à la [indépendance du langage et composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40035  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si vous avez besoin de la conformité CLS, définissez vos surcharges pour diffèrent entre eux dans plus de manières que seules les modifications mentionnées dans cette page d’aide.  
  
- Si vous avez besoin que les surcharges diffèrent uniquement par les modifications mentionnées dans cette aide page, supprimez le <xref:System.CLSCompliantAttribute> à partir de leurs définitions ou marquez-les comme `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Voir aussi

- [Surcharge de procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
