---
title: 'Procédure : Partager un assembly avec d’autres applications'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b1ef195458dd2de95eeb5e25089339e55d9e3fbb
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972948"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>Procédure : Partager un assembly avec d’autres applications
Les assemblys peuvent être privés ou partagés. Par défaut, la plupart des programmes simples se composent d’un assembly privé, car ils ne sont pas destinés à être utilisés par d’autres applications.  

Pour partager un assembly avec d’autres applications, celui-ci doit être placé dans le [global assembly cache (GAC)](gac.md).  
  
Pour partager un assembly :
  
1. Créez votre assembly. Pour plus d’informations, consultez [créer des assemblys](../../standard/assembly/create.md).  
  
2. Attribuez un nom fort à votre assembly. Pour plus d’informations, consultez [Guide pratique pour signer un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).  
  
3. Assignez des informations de version à votre assembly. Pour plus d’informations, consultez contrôle de [version des assemblys](../../standard/assembly/versioning.md).  
  
4. Ajoutez votre assembly au Global Assembly Cache. Pour plus d'informations, voir [Procédure : Installez un assembly dans le](install-assembly-into-gac.md)global assembly cache.  
  
5. Accédez aux types contenus dans l’assembly à partir d’autres applications. Pour plus d’informations, consultez [Guide pratique pour Référencez un assembly](../../standard/assembly/reference-strong-named.md)avec nom fort.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../api/index.md)
- [Concepts de programmation (Visual Basic)](../../../api/index.md)
- [Programmer avec des assemblys](../../standard/assembly/program.md)
