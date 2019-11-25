---
title: Vue d'ensemble des constantes
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 9ccddfe44757c76992d641094e21ec8c2110ef83
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338342"
---
# <a name="constants-overview-visual-basic"></a>Vue d'ensemble des constantes (Visual Basic)
A constant is a meaningful name that takes the place of a number or string that does not change. Constants store values that, as the name implies, remain the same throughout the execution of an application. You can greatly improve the readability of your code and make it easier to maintain by using constants. Use them in code that contains values that reappear or that depends on certain numbers that are difficult to remember or have no obvious meaning.  
  
## <a name="how-to-create-and-use-constants"></a>How to Create and Use Constants  
 Visual Basic contains a number of predefined constants, mainly using for printing and displaying. You can also create your own constants with the `Const` statement, using the same guidelines you would for creating a variable name. If `Option Strict` is `On`, you must explicitly declare the constant type.  
  
 A constant's scope, which is the set of all code that can refer to it without qualifying its name, is the same as that of a variable declared in the same location. To create a constant that exists within the scope of a particular procedure, declare it inside that procedure. To create a constant that is available throughout an application, declare it using the `Public` keyword in the declarations section of the class.  
  
> [!NOTE]
> Although constants somewhat resemble variables, you cannot modify them or assign new values to them as you can to variables.  
  
 The constants you use in your code can be defined by the object model for controls or components you work with, or they can be user-defined (that is, those you create yourself).  
  
## <a name="compile-time-and-run-time-constants"></a>Compile-time and Run-time Constants  
 A compile-time constant is computed at the time the code is compiled, while a run-time constant can only be computed while the application is running. A compile-time constant will have the same value each time an application runs, while a run-time constant may change each time. Compile-time constants are required for cases such as array bounds, case expressions, or enumerator initializers.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Définition|Terme|  
|---|---|  
|[Guide pratique : déclarer une constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Explains how to use the `Const` statement to declare a constant and set its value; by declaring a constant, you assign a meaningful name to the value.|  
|[Constantes définies par l’utilisateur](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Describes how to create your own constants, including information on scoping and how to avoid circular references.|  
|[Constantes et types de données littérales](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Provides information on how the Visual Basic compiler initializes constants when `Option Explicit` is turned off.|  
|[Guide pratique : regrouper les valeurs de constante connexes](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Demonstrates how to group constant values that are related.|  
  
## <a name="reference"></a>Reference  
  
|Définition|Terme|  
|---|---|  
|[Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Lists the constants predefined by Visual Basic.|  
|[Const (instruction)](../../../../visual-basic/language-reference/statements/const-statement.md)|Describes the `Const` statement and its use.|  
|[Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Describes the `Option Strict` statement and its use.|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Comment : initialiser une variable tableau en Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
