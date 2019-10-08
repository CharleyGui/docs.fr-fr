---
title: 'Procédure : Faire en sorte qu’une variable objet ne fasse pas référence à une instance (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: e647f2f891b06aa1767faac49b01df98ea31ec1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004917"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Procédure : Faire en sorte qu’une variable objet ne fasse pas référence à une instance (Visual Basic)
Vous pouvez dissocier une variable objet d’une instance d’objet en lui affectant la valeur [Nothing](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Pour dissocier une variable objet d’une instance d’objet  
  
- Affectez à la variable la valeur `Nothing` dans une instruction d’assignation.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Programmation fiable  
 Si votre code tente d’accéder à un membre d’une variable objet qui a été définie sur `Nothing`, une <xref:System.NullReferenceException> se produit. Si vous affectez à une variable objet la valeur `Nothing` fréquemment, ou si la variable n’est pas initialisée, il est judicieux de placer les accès aux membres dans un bloc `Try...Catch...Finally`.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Si vous utilisez une variable objet pour des objets qui contiennent des données confidentielles ou sensibles, vous pouvez définir la variable sur `Nothing` lorsque vous n’êtes pas activement confronté à l’un de ces objets. Cela réduit le risque que du code malveillant ait accès aux données.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.NullReferenceException>
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Assignation des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Try...Catch...Finally (instruction)](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
