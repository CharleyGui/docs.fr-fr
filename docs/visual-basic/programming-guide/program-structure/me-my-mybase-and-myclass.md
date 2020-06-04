---
title: Me, My, MyBase et MyClass
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: b4470e5c178c0f66dc33956ea0131d4eabc51d46
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397465"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase et MyClass dans Visual Basic
`Me`, `My` , `MyBase` et `MyClass` dans Visual Basic ont des noms similaires, mais à des fins différentes. Cette rubrique décrit chacune de ces entités afin de les distinguer.  
  
## <a name="me"></a>Moi  
 Le `Me` mot clé permet de faire référence à l’instance spécifique d’une classe ou d’une structure dans laquelle le code est en cours d’exécution. `Me`se comporte comme une variable objet ou une variable de structure faisant référence à l’instance actuelle. L’utilisation de `Me` est particulièrement utile pour transmettre des informations sur l’instance en cours d’exécution d’une classe ou d’une structure à une procédure d’une autre classe, structure ou module.  
  
 Par exemple, supposons que vous ayez la procédure suivante dans un module.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Vous pouvez appeler cette procédure et passer l’instance actuelle de la <xref:System.Windows.Forms.Form> classe en tant qu’argument à l’aide de l’instruction suivante.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 Cette `My` fonctionnalité offre un accès facile et intuitif à plusieurs classes de .NET Framework, ce qui permet à l’utilisateur Visual Basic d’interagir avec l’ordinateur, l’application, les paramètres, les ressources, etc.  
  
## <a name="mybase"></a>MyBase  
 Le `MyBase` mot clé se comporte comme une variable objet qui fait référence à la classe de base de l’instance actuelle d’une classe. `MyBase`est couramment utilisé pour accéder aux membres de la classe de base qui sont substitués ou occultés dans une classe dérivée. `MyBase.New`est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivée.  
  
## <a name="myclass"></a>MyClass  
 Le `MyClass` mot clé se comporte comme une variable objet qui fait référence à l’instance actuelle d’une classe telle qu’elle a été implémentée à l’origine. `MyClass`est semblable à `Me` , mais tous les appels de méthode sur celui-ci sont traités comme si la méthode avait la valeur `NotOverridable` .  
  
## <a name="see-also"></a>Voir aussi

- [Éléments fondamentaux de l’héritage](../language-features/objects-and-classes/inheritance-basics.md)
