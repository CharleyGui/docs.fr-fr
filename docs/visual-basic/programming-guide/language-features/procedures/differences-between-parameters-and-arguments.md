---
title: Différences entre les paramètres et les arguments
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: c4249dbf86bd1bfa7ef08e94059d2880333e9a92
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341374"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Différences entre les paramètres et les arguments (Visual Basic)
Dans la plupart des cas, une procédure doit avoir des informations sur les circonstances dans lesquelles elle a été appelée. Une procédure qui exécute des tâches répétitives ou partagées utilise des informations différentes pour chaque appel. Ces informations se composent de variables, de constantes et d’expressions que vous transmettez à la procédure lorsque vous l’appelez.  
  
 Pour communiquer ces informations à la procédure, la procédure définit un *paramètre*et le code appelant passe un *argument* à ce paramètre. Vous pouvez considérer le paramètre comme un espace de parking et l’argument comme une automobile. Tout comme les autres automobiles peuvent se garer dans un espace de parking à différents moments, le code appelant peut passer un argument différent au même paramètre chaque fois qu’il appelle la procédure.  
  
## <a name="parameters"></a>Paramètres  
 Un *paramètre* représente une valeur que la procédure vous attend à passer lorsque vous l’appelez. La déclaration de la procédure définit ses paramètres.  
  
 Lorsque vous définissez une `Function` ou `Sub` procédure, vous spécifiez une *liste de paramètres* entre parenthèses immédiatement après le nom de la procédure. Pour chaque paramètre, vous spécifiez un nom, un type de données et un mécanisme de passage ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)). Vous pouvez également indiquer qu’un paramètre est facultatif. Cela signifie que le code appelant n’a pas besoin de passer une valeur pour celui-ci.  
  
 Le nom de chaque paramètre fait office de *variable locale* dans la procédure. Vous utilisez le nom de paramètre de la même façon que vous utilisez une autre variable.  
  
## <a name="arguments"></a>Arguments  
 Un *argument* représente la valeur que vous transmettez à un paramètre de procédure lorsque vous appelez la procédure. Le code appelant fournit les arguments lorsqu’il appelle la procédure.  
  
 Quand vous appelez une procédure `Function` ou `Sub`, vous incluez une *liste d’arguments* entre parenthèses immédiatement après le nom de la procédure. Chaque argument correspond au paramètre à la même position dans la liste.  
  
 Contrairement à la définition des paramètres, les arguments n’ont pas de noms. Chaque argument est une expression, qui peut contenir zéro, une ou plusieurs variables, constantes et littéraux. Le type de données de l’expression évaluée doit généralement correspondre au type de données défini pour le paramètre correspondant, et dans tous les cas, il doit être converti en type de paramètre.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures Sub](./sub-procedures.md)
- [Procédures Function](./function-procedures.md)
- [Procédures de propriété](./property-procedures.md)
- [Procédures d’opérateur](./operator-procedures.md)
- [Guide pratique : définir un paramètre pour une procédure](./how-to-define-a-parameter-for-a-procedure.md)
- [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Procédures récursives](./recursive-procedures.md)
- [Surcharge de procédure](./procedure-overloading.md)
