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
ms.openlocfilehash: bbed3248840803d36607a67c8373fed15c07445f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341220"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Différences entre les propriétés et les variables en Visual Basic
Les variables et les propriétés représentent toutes deux des valeurs auxquelles vous pouvez accéder. Toutefois, il existe des différences en matière de stockage et d’implémentation.  
  
## <a name="variables"></a>Variables  
 Une *variable* correspond directement à un emplacement de mémoire. Vous définissez une variable avec une instruction de déclaration unique. Une variable peut être une *variable locale*, définie à l’intérieur d’une procédure et disponible uniquement dans cette procédure, ou elle peut être une *variable membre*, définie dans un module, une classe ou une structure, mais pas à l’intérieur d’une procédure. Une variable membre est également appelée un *champ*.  
  
## <a name="properties"></a>Propriétés  
 Une *propriété* est un élément de données défini sur un module, une classe ou une structure. Vous définissez une propriété avec un bloc de code entre les instructions `Property` et `End Property`. Le bloc de code contient une procédure `Get`, une procédure `Set` ou les deux. Ces procédures sont appelées *procédures de propriété* ou *accesseurs de propriété*. En plus de récupérer ou de stocker la valeur de la propriété, ils peuvent également effectuer des actions personnalisées, telles que la mise à jour d’un compteur d’accès.  
  
## <a name="differences"></a>Différences  
 Le tableau suivant présente quelques différences importantes entre les variables et les propriétés.  
  
|Point de différence|Variable|Propriété|  
|-------------------------|--------------|--------------|  
|Déclaration|Instruction de déclaration unique|Série d’instructions dans un bloc de code|  
|Implémentation|Emplacement de stockage unique|Code exécutable (procédures de propriété)|  
|Stockage|Directement associée à la valeur de la variable|Possède généralement un stockage interne qui n’est pas disponible en dehors de la classe ou du module conteneur de la propriété<br /><br /> La valeur de la propriété peut ou non exister en tant qu’élément stocké <sup>1</sup>|  
|Code exécutable|Aucune|Doit avoir au moins une procédure|  
|Accès en lecture et en écriture|Lecture/écriture ou lecture seule|Lecture/écriture, lecture seule ou écriture seule|  
|Actions personnalisées (en plus d’accepter ou de retourner une valeur)|Non possible|Peut être effectué dans le cadre de la définition ou de la récupération de la valeur de propriété|  
  
 <sup>1</sup> contrairement à une variable, la valeur d’une propriété peut ne pas correspondre directement à un seul élément de stockage. Le stockage peut être fractionné en plusieurs parties pour des raisons de commodité ou de sécurité, ou la valeur peut être stockée sous une forme chiffrée. Dans ce cas, la procédure `Get` assembler les éléments ou déchiffrer la valeur stockée, et la procédure `Set` chiffre la nouvelle valeur ou la fractionne dans le stockage constitutif. Une valeur de propriété peut être éphémère, comme l’heure de la journée, auquel cas la procédure `Get` le calcul à la volée chaque fois que vous accédez à la propriété.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures de propriété](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Property (instruction)](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Guide pratique : créer une propriété](./how-to-create-a-property.md)
- [Guide pratique : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Guide pratique : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)
- [Comment : déclarer et appeler une propriété par défaut dans Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Guide pratique : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)
- [Guide pratique : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)
