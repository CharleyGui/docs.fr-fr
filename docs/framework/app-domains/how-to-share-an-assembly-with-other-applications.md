---
title: 'Procédure : Partager un assembly avec d’autres applications'
description: Découvrez comment partager un assembly avec d’autres applications dans .NET. Les assemblys peuvent être privés (valeur par défaut) ou partagés. Pour partager un assembly, placez-le dans le GAC.
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 1056f8b555713d5d67488537e6c06cc457c4d312
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242537"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>Procédure : Partager un assembly avec d’autres applications

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
