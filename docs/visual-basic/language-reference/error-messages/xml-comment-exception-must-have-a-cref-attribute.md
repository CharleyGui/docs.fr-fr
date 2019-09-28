---
title: L'exception de commentaire XML doit avoir un attribut 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592037"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>L'exception de commentaire XML doit avoir un attribut 'cref'
La balise \<exception > fournit un moyen de documenter les exceptions qui peuvent être levées par une méthode. L’attribut requis `cref` désigne le nom d’un membre, qui est vérifié par le générateur de documentation. Si le membre existe, il est traduit en nom d’élément canonique dans le fichier de documentation.  
  
 **ID d’erreur :** BC42319  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez l’attribut `cref` à l’exception comme suit :  
  
    xml  
    <exception cref="member">Description</exception> de' ' '  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
