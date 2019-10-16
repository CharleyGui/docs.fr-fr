---
title: L'exception de commentaire XML doit avoir un attribut 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 54965f3796b6c5ef0e387cd354abcb5740476257
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321175"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>L'exception de commentaire XML doit avoir un attribut 'cref'

La balise \<exception > fournit un moyen de documenter les exceptions qui peuvent être levées par une méthode. L’attribut requis `cref` désigne le nom d’un membre, qui est vérifié par le générateur de documentation. Si le membre existe, il est traduit en nom d’élément canonique dans le fichier de documentation.

**ID d’erreur :** BC42319

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

Ajoutez l’attribut `cref` à l’exception comme suit :

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>Voir aussi

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [Guide pratique : créer une documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)
