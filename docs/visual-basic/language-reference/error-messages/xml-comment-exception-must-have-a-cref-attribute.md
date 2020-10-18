---
title: L'exception de commentaire XML doit avoir un attribut 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 18e7aa5f6905eaa9c509aa21fe6f5bfcd54d46f0
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163296"
---
# <a name="bc42319-xml-comment-exception-must-have-a-cref-attribute"></a>BC42319 : l’exception de commentaire XML doit avoir un attribut’CREF'

La \<exception> balise permet de documenter les exceptions qui peuvent être levées par une méthode. L’attribut required `cref` désigne le nom d’un membre, qui est vérifié par le générateur de documentation. Si le membre existe, il est traduit en nom d’élément canonique dans le fichier de documentation.

**ID d’erreur :** BC42319

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

Ajoutez l' `cref` attribut à l’exception comme suit :

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>Voir aussi

- [\<exception>](../xmldoc/exception.md)
- [Guide pratique : créer une documentation XML](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Étiquettes XML pour les commentaires](../xmldoc/index.md)
