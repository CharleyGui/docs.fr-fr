---
title: "Comment : faire en sorte qu'une variable objet ne fasse pas référence à une instance"
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 61bb06401ebd1e479c9256a80a12d87240831063
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080252"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Comment : faire en sorte qu'une variable objet ne fasse pas référence à une instance (Visual Basic)

Vous pouvez dissocier une variable objet d’une instance d’objet en lui affectant la valeur [Nothing](../../../language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Pour dissocier une variable objet d’une instance d’objet  
  
- Affectez à la variable la valeur `Nothing` dans une instruction d’assignation.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Programmation fiable  

 Si votre code tente d’accéder à un membre d’une variable objet qui a été définie sur `Nothing` , une <xref:System.NullReferenceException> se produit. Si vous définissez une variable objet sur `Nothing` fréquemment, ou s’il est possible que la variable ne soit pas initialisée, il est judicieux de délimiter les accès aux membres dans un `Try...Catch...Finally` bloc.  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  

 Si vous utilisez une variable objet pour des objets qui contiennent des données confidentielles ou sensibles, vous pouvez affecter à la variable la valeur `Nothing` lorsque vous ne traitez pas activement l’un de ces objets. Cela réduit le risque que du code malveillant ait accès aux données.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.NullReferenceException>
- [Variables objets](object-variables.md)
- [Affectation des variables objets](object-variable-assignment.md)
- [Nothing](../../../language-reference/nothing.md)
- [Try...Catch...Finally (instruction)](../../../language-reference/statements/try-catch-finally-statement.md)
