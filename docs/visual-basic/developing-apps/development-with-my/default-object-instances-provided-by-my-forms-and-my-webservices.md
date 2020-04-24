---
title: Instances d’objets par défaut fournies par My.Forms et My.WebServices
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: d06df4bd023892429b2aaefdd624398a6546d06d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330207"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Instances d'objets par défaut fournies par My.Forms et My.WebServices (Visual Basic)

Les objets [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) et [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) fournissent un accès aux formulaires, aux sources de données et aux services Web XML utilisés par votre application. Pour ce faire, ils fournissent des collections d' *instances par défaut* de chacun de ces objets.  
  
## <a name="default-instances"></a>Instances par défaut  

 Une instance par défaut est une instance de la classe fournie par le runtime et n’a pas besoin d’être déclarée et instanciée à `Dim` l' `New` aide des instructions et. L’exemple suivant montre comment vous avez pu déclarer et instancier une instance d’une <xref:System.Windows.Forms.Form> classe appelée `Form1`, et comment vous pouvez désormais obtenir une instance par défaut de cette <xref:System.Windows.Forms.Form> classe via. `My.Forms`  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 L' `My.Forms` objet retourne une collection d’instances par défaut pour `Form` chaque classe qui existe dans votre projet. De même, `My.WebServices` fournit une instance par défaut de la classe proxy pour chaque service Web auquel vous avez créé une référence dans votre application.  
  
## <a name="see-also"></a>Voir aussi

- [My.Forms, objet](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.WebServices (objet)](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [Comment My dépend du type de projet](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
