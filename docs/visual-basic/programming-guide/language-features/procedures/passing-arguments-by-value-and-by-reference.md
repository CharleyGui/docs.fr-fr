---
title: Passage des arguments par valeur et par référence
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: b7430b209f53a0a924ec587a0097178baf0075e3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059215"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Passage d’un argument par valeur et par référence (Visual Basic)

Dans Visual Basic, vous pouvez passer un argument à une procédure *par valeur* ou *par référence*. C’est ce que l’on appelle le *mécanisme de passage*et détermine si la procédure peut modifier l’élément de programmation sous-jacent à l’argument dans le code appelant. La déclaration de procédure détermine le mécanisme de passage pour chaque paramètre en spécifiant le mot clé [ByVal](../../../language-reference/modifiers/byval.md) ou [ByRef](../../../language-reference/modifiers/byref.md) .  
  
## <a name="distinctions"></a>Distinctions  

 Lors du passage d’un argument à une procédure, tenez compte de plusieurs différences différentes qui interagissent entre elles :  
  
- Si l’élément de programmation sous-jacent est modifiable ou non modifiable  
  
- Si l’argument lui-même est modifiable ou non modifiable  
  
- Si l’argument est passé par valeur ou par référence  
  
- Si le type de données de l’argument est un type valeur ou un type référence  
  
 Pour plus d’informations, consultez [différences entre les arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md) et les [différences entre le passage d’un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Choix du mécanisme de passage  

 Vous devez choisir le mécanisme de passage avec précaution pour chaque argument.  
  
- **Protection**. Dans le choix entre les deux mécanismes de passage, le critère le plus important est l’exposition des variables appelées à changer. L’avantage de passer un argument `ByRef` est que la procédure peut retourner une valeur au code appelant par le biais de cet argument. L’avantage de passer un argument `ByVal` est qu’il empêche la modification d’une variable par la procédure.  
  
- **Performances**. Bien que le mécanisme de passage puisse affecter les performances de votre code, la différence est généralement insignifiante. Une exception est un type valeur passé `ByVal` . Dans ce cas, Visual Basic copie l’intégralité du contenu des données de l’argument. Par conséquent, pour un type de valeur élevée tel qu’une structure, il peut être plus efficace de la passer `ByRef` .  
  
     Pour les types référence, seul le pointeur vers les données est copié (quatre octets sur les plateformes 32 bits, huit octets sur les plateformes 64 bits). Par conséquent, vous pouvez passer des arguments de type `String` ou `Object` par valeur sans nuire aux performances.  
  
## <a name="determination-of-the-passing-mechanism"></a>Détermination du mécanisme de passage  

 La déclaration de procédure spécifie le mécanisme de passage pour chaque paramètre. Le code appelant ne peut pas substituer un `ByVal` mécanisme.  
  
 Si un paramètre est déclaré avec `ByRef` , le code appelant peut forcer le mécanisme à `ByVal` en plaçant le nom de l’argument entre parenthèses dans l’appel. Pour plus d’informations, consultez [Comment : forcer le passage d’un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 La valeur par défaut de Visual Basic consiste à passer des arguments par valeur.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Quand passer un argument par valeur  
  
- Si l’élément de code appelant sous-jacent à l’argument est un élément non modifiable, déclarez le paramètre correspondant [ByVal](../../../language-reference/modifiers/byval.md). Aucun code ne peut modifier la valeur d’un élément non modifiable.  
  
- Si l’élément sous-jacent est modifiable, mais que vous ne souhaitez pas que la procédure puisse modifier sa valeur, déclarez le paramètre `ByVal` . Seul le code appelant peut modifier la valeur d’un élément modifiable passé par valeur.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Quand passer un argument par référence  
  
- Si la procédure a un besoin réel de modifier l’élément sous-jacent dans le code appelant, déclarez le paramètre correspondant [ByRef](../../../language-reference/modifiers/byref.md).  
  
- Si l’exécution correcte du code dépend de la procédure modifiant l’élément sous-jacent dans le code appelant, déclarez le paramètre `ByRef` . Si vous le passez par valeur, ou si le code appelant substitue le `ByRef` mécanisme de passage en mettant l’argument entre parenthèses, l’appel de procédure peut produire des résultats inattendus.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  

 L’exemple suivant montre comment passer des arguments par valeur et quand les passer par référence. `Calculate`La procédure a à la fois un `ByVal` et un `ByRef` paramètre. Étant donné un taux d’intérêt, `rate` , et une somme d’argent, `debt` la tâche de la procédure consiste à calculer une nouvelle valeur pour, `debt` qui est le résultat de l’application du taux d’intérêt à la valeur d’origine de `debt` . Étant donné que `debt` est un `ByRef` paramètre, le nouveau total est reflété dans la valeur de l’argument dans le code appelant qui correspond à `debt` . Le paramètre `rate` est un `ByVal` paramètre, car ne `Calculate` doit pas modifier sa valeur.  
  
### <a name="code"></a>Code  

 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Comment : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Comment : modifier la valeur d’un argument de la procédure](./how-to-change-the-value-of-a-procedure-argument.md)
- [Comment : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Comment : forcer le passage d'un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)
- [Types valeur et types référence](../data-types/value-types-and-reference-types.md)
