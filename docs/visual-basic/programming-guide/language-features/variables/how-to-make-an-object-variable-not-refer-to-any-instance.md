---
title: "Comment : faire en sorte qu'une variable objet ne fasse pas référence à une instance"
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 320dadb61c12f3339c5328dcef31c41503892c56
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352892"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Comment : faire en sorte qu'une variable objet ne fasse pas référence à une instance (Visual Basic)
Vous pouvez dissocier une variable objet d’une instance d’objet en lui affectant la valeur [Nothing](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Pour dissocier une variable objet d’une instance d’objet  
  
- Affectez à la variable la valeur `Nothing` dans une instruction d’assignation.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Programmation fiable  
 Si votre code tente d’accéder à un membre d’une variable objet qui a été définie sur `Nothing`, un <xref:System.NullReferenceException> se produit. Si vous définissez une variable objet sur `Nothing` fréquemment, ou s’il est possible que la variable ne soit pas initialisée, il est judicieux de délimiter les accès aux membres dans un bloc `Try...Catch...Finally`.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Si vous utilisez une variable objet pour des objets qui contiennent des données confidentielles ou sensibles, vous pouvez définir la variable sur `Nothing` lorsque vous ne traitez pas activement l’un de ces objets. Cela réduit le risque que du code malveillant ait accès aux données.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.NullReferenceException>
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Assignation des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Try...Catch...Finally (instruction)](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
