---
title: Différences entre les propriétés et les variables
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: 95bafcaca98e1a0fbdd62a550291c8ece932c1ba
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075029"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Différences entre les propriétés et les variables en Visual Basic

Les variables et les propriétés représentent toutes deux des valeurs auxquelles vous pouvez accéder. Toutefois, il existe des différences en matière de stockage et d’implémentation.  
  
## <a name="variables"></a>Variables  

 Une *variable* correspond directement à un emplacement de mémoire. Vous définissez une variable avec une instruction de déclaration unique. Une variable peut être une *variable locale*, définie à l’intérieur d’une procédure et disponible uniquement dans cette procédure, ou elle peut être une *variable membre*, définie dans un module, une classe ou une structure, mais pas à l’intérieur d’une procédure. Une variable membre est également appelée un *champ*.  
  
## <a name="properties"></a>Propriétés  

 Une *propriété* est un élément de données défini sur un module, une classe ou une structure. Vous définissez une propriété avec un bloc de code entre `Property` les `End Property` instructions et. Le bloc de code contient une `Get` procédure, une `Set` procédure ou les deux. Ces procédures sont appelées *procédures de propriété* ou *accesseurs de propriété*. En plus de récupérer ou de stocker la valeur de la propriété, ils peuvent également effectuer des actions personnalisées, telles que la mise à jour d’un compteur d’accès.  
  
## <a name="differences"></a>Différences  

 Le tableau suivant présente quelques différences importantes entre les variables et les propriétés.  
  
|Point de différence|Variable|Propriété|  
|-------------------------|--------------|--------------|  
|Déclaration|Instruction de déclaration unique|Série d’instructions dans un bloc de code|  
|Implémentation|Emplacement de stockage unique|Code exécutable (procédures de propriété)|  
|Stockage|Directement associée à la valeur de la variable|Possède généralement un stockage interne qui n’est pas disponible en dehors de la classe ou du module conteneur de la propriété<br /><br /> La valeur de la propriété peut ou non exister en tant qu’élément stocké <sup>1</sup>|  
|Code exécutable|None|Doit avoir au moins une procédure|  
|Accès en lecture et en écriture|Lecture/écriture ou lecture seule|Lecture/écriture, lecture seule ou écriture seule|  
|Actions personnalisées (en plus d’accepter ou de retourner une valeur)|Impossible|Peut être effectué dans le cadre de la définition ou de la récupération de la valeur de propriété|  
  
 <sup>1</sup> contrairement à une variable, la valeur d’une propriété peut ne pas correspondre directement à un seul élément de stockage. Le stockage peut être fractionné en plusieurs parties pour des raisons de commodité ou de sécurité, ou la valeur peut être stockée sous une forme chiffrée. Dans ce cas `Get` , la procédure assemblerait les éléments ou déchiffrerait la valeur stockée, et la `Set` procédure chiffrerait la nouvelle valeur ou la fractionnera dans le stockage constitutif. Une valeur de propriété peut être éphémère, comme l’heure de la journée, auquel cas la `Get` procédure le calcule à la volée chaque fois que vous accédez à la propriété.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures Property](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Dim (instruction)](../../../language-reference/statements/dim-statement.md)
- [Comment : créer une propriété](./how-to-create-a-property.md)
- [Comment : déclarer une propriété avec des niveaux d'accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Comment : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)
- [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Comment : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)
- [Comment : obtenir une valeur d'une propriété](./how-to-get-a-value-from-a-property.md)
