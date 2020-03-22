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
ms.openlocfilehash: a21dfeb12e8d99f5f8b8afede084846711c299ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400847"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase et MyClass dans Visual Basic
`Me`, `My` `MyBase`, `MyClass` et dans Visual Basic ont des noms similaires, mais des buts différents. Ce sujet décrit chacune de ces entités afin de les distinguer.  
  
## <a name="me"></a>Moi  
 Le `Me` mot clé fournit un moyen de se référer à l’instance spécifique d’une classe ou d’une structure dans laquelle le code est actuellement en cours d’exécution. `Me`se comporte comme une variable d’objet ou une variable de structure se référant à l’instance actuelle. L’utilisation `Me` est particulièrement utile pour transmettre des informations sur l’instance actuellement exécutante d’une classe ou d’une structure à une procédure dans une autre classe, structure ou module.  
  
 Supposons, par exemple, que vous ayez la procédure suivante dans un module.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Vous pouvez appeler cette procédure et passer <xref:System.Windows.Forms.Form> l’instance actuelle de la classe comme un argument en utilisant la déclaration suivante.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 La `My` fonctionnalité offre un accès facile et intuitif à un certain nombre de classes cadre .NET, permettant à l’utilisateur visual basic d’interagir avec l’ordinateur, l’application, les paramètres, les ressources, et ainsi de suite.  
  
## <a name="mybase"></a>MyBase  
 Le `MyBase` mot clé se comporte comme une variable d’objet se référant à la classe de base de l’instance actuelle d’une classe. `MyBase`est couramment utilisé pour accéder aux membres de la classe de base qui sont remplacés ou ombragés dans une classe dérivée. `MyBase.New`est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivé.  
  
## <a name="myclass"></a>MyClass  
 Le `MyClass` mot clé se comporte comme une variable d’objet se référant à l’instance actuelle d’une classe telle qu’elle a été mise en œuvre à l’origine. `MyClass`est similaire `Me`à , mais tous les appels méthode `NotOverridable`sur elle sont traitées comme si la méthode étaient .  
  
## <a name="see-also"></a>Voir aussi

- [Éléments fondamentaux de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
