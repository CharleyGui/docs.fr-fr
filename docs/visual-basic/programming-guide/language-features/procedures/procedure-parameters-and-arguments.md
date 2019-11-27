---
title: Paramètres et arguments d’une procédure
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 7dfbbcb39cf7bb05c8a62a7a252e425f287c9a09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352579"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Paramètres et arguments d’une procédure (Visual Basic)
Dans la plupart des cas, une procédure a besoin d’informations sur les circonstances dans lesquelles elle a été appelée. Une procédure qui exécute des tâches répétitives ou partagées utilise des informations différentes pour chaque appel. Ces informations se composent de variables, de constantes et d’expressions que vous transmettez à la procédure lorsque vous l’appelez.  
  
 Un *paramètre* représente une valeur que la procédure vous attend à fournir lorsque vous l’appelez. La déclaration de la procédure définit ses paramètres.  
  
 Vous pouvez définir une procédure sans paramètres, un paramètre ou plusieurs. La partie de la définition de procédure qui spécifie les paramètres est appelée *liste de paramètres*.  
  
 Un *argument* représente la valeur que vous fournissez à un paramètre de procédure lorsque vous appelez la procédure. Le code appelant fournit les arguments lorsqu’il appelle la procédure. La partie de l’appel de procédure qui spécifie les arguments est appelée *liste d’arguments*.  
  
 L’illustration suivante montre le code appelant la procédure `safeSquareRoot` à partir de deux emplacements différents. Le premier appel passe la valeur de la variable `x` (4,0) au paramètre `number`, et la valeur de retour dans `root` (2,0) est assignée à la variable `y`. Le deuxième appel passe la valeur littérale 9,0 à `number`et affecte la valeur de retour (3,0) à la variable `z`.  
  
 ![Diagramme qui illustre le passage d’un argument à un paramètre](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 Pour plus d’informations, consultez [différences entre les paramètres et les arguments](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Type de données du paramètre  
 Vous définissez un type de données pour un paramètre à l’aide de la clause `As` dans sa déclaration. Par exemple, la fonction suivante accepte une chaîne et un entier.  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 Si le commutateur de vérification de type ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `Off,` la clause `As` est facultative, mais si un paramètre l’utilise, tous les paramètres doivent l’utiliser. Si la vérification de type est `On`, la clause `As` est requise pour tous les paramètres de procédure.  
  
 Si le code appelant s’attend à fournir un argument avec un type de données différent de celui de son paramètre correspondant, par exemple `Byte` à un paramètre `String`, il doit effectuer l’une des opérations suivantes :  
  
- Fournissez uniquement des arguments avec des types de données qui s’étendent au type de données du paramètre ;  
  
- Définissez `Option Strict Off` pour autoriser les conversions restrictives implicites ; ni  
  
- Utilisez un mot clé de conversion pour convertir explicitement le type de données.  
  
### <a name="type-parameters"></a>Paramètres de type  
 Une *procédure générique* définit également un ou plusieurs *paramètres de type* en plus de ses paramètres normaux. Une procédure générique permet au code appelant de passer différents types de données chaque fois qu’il appelle la procédure. il peut donc adapter les types de données aux exigences de chaque appel individuel. Consultez [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures Sub](./sub-procedures.md)
- [Procédures Function](./function-procedures.md)
- [Procédures de propriété](./property-procedures.md)
- [Procédures d’opérateur](./operator-procedures.md)
- [Guide pratique : définir un paramètre pour une procédure](./how-to-define-a-parameter-for-a-procedure.md)
- [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
