---
title: 'Comment : partager un assembly avec d’autres applications'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b4c183c3fc0b04121be8bbc2db4027887cbc3132
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644288"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>Comment : partager un assembly avec d’autres applications
Les assemblys peuvent être privés ou partagés. Par défaut, la plupart des programmes simples se composent d’un assembly privé, car ils ne sont pas destinés à être utilisés par d’autres applications.  

Pour partager un assembly avec d’autres applications, celui-ci doit être placé dans le [global assembly cache (GAC)](gac.md).  
  
Pour partager un assembly :
  
1. Créez votre assembly. Pour plus d’informations, consultez [créer des assemblys](../../standard/assembly/create.md).  
  
2. Attribuez un nom fort à votre assembly. Pour plus d’informations, consultez [Comment : signer un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).  
  
3. Assignez des informations de version à votre assembly. Pour plus d’informations, consultez contrôle de [version des assemblys](../../standard/assembly/versioning.md).  
  
4. Ajoutez votre assembly au Global Assembly Cache. Pour plus d’informations, consultez [Comment : installer un assembly dans le global assembly cache](install-assembly-into-gac.md).  
  
5. Accédez aux types contenus dans l’assembly à partir d’autres applications. Pour plus d’informations, consultez [Guide pratique pour référencer un assembly avec nom fort](../../standard/assembly/reference-strong-named.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../api/index.md)
- [Concepts de programmation (Visual Basic)](../../../api/index.md)
- [Programmer avec des assemblys](../../standard/assembly/index.md)
