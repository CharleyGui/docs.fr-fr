---
title: Différences entre le passage d'un argument par valeur et par référence
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: bd316ae2239ad85e4ef6dadbb8a634d5fe7ecf02
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403328"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Différences entre le passage d’un argument par valeur et par référence (Visual Basic)
Quand vous transmettez un ou plusieurs arguments à une procédure, chaque argument correspond à un élément de programmation sous-jacent dans le code appelant. Vous pouvez passer la valeur de cet élément sous-jacent ou une référence à celui-ci. C’est ce que l’on appelle le *mécanisme de passage*.  
  
## <a name="passing-by-value"></a>passer par valeur  
 Vous transmettez un argument *par valeur* en spécifiant le mot clé [ByVal](../../../language-reference/modifiers/byval.md) pour le paramètre correspondant dans la définition de la procédure. Lorsque vous utilisez ce mécanisme de passage, Visual Basic copie la valeur de l’élément de programmation sous-jacent dans une variable locale de la procédure. Le code de la procédure n’a pas accès à l’élément sous-jacent dans le code appelant.  
  
## <a name="passing-by-reference"></a>Passer par référence  
 Vous transmettez un argument *par référence* en spécifiant le mot clé [ByRef](../../../language-reference/modifiers/byref.md) pour le paramètre correspondant dans la définition de la procédure. Lorsque vous utilisez ce mécanisme de passage, Visual Basic donne à la procédure une référence directe à l’élément de programmation sous-jacent dans le code appelant.  
  
## <a name="passing-mechanism-and-element-type"></a>Transmission du mécanisme et du type d’élément  
 Le choix du mécanisme de passage n’est pas le même que la classification du type d’élément sous-jacent. Le passage par valeur ou par référence fait référence à ce que Visual Basic fournit au code de la procédure. Un type valeur ou un type référence fait référence à la façon dont un élément de programmation est stocké en mémoire.  
  
 Toutefois, le mécanisme de passage et le type d’élément sont interdépendants. La valeur d’un type référence est un pointeur vers les données situées ailleurs en mémoire. Cela signifie que lorsque vous transmettez un type référence par valeur, le code de la procédure a un pointeur vers les données de l’élément sous-jacent, même s’il ne peut pas accéder à l’élément sous-jacent lui-même. Par exemple, si l’élément est une variable tableau, le code de la procédure n’a pas accès à la variable elle-même, mais il peut accéder aux membres du tableau.  
  
## <a name="ability-to-modify"></a>Possibilité de modification  
 Quand vous transmettez un élément non modifiable en tant qu’argument, la procédure ne peut jamais la modifier dans le code appelant, qu’elle soit passée `ByVal` ou `ByRef` .  
  
 Pour un élément modifiable, le tableau suivant résume l’interaction entre le type d’élément et le mécanisme de passage.  
  
|Type d'élément|Passe`ByVal`|Passe`ByRef`|  
|------------------|--------------------|--------------------|  
|Type valeur (contient uniquement une valeur)|La procédure ne peut pas modifier la variable ou l’un de ses membres.|La procédure peut modifier la variable et ses membres.|  
|Type référence (contient un pointeur vers une instance de classe ou de structure)|La procédure ne peut pas modifier la variable, mais peut modifier les membres de l’instance vers laquelle elle pointe.|La procédure peut modifier la variable et les membres de l’instance vers laquelle elle pointe.|  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Comment : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage des arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Différences entre les arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Comment : modifier la valeur d’un argument de la procédure](./how-to-change-the-value-of-a-procedure-argument.md)
- [Comment : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Comment : forcer le passage d'un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)
- [Types valeur et types référence](../data-types/value-types-and-reference-types.md)
