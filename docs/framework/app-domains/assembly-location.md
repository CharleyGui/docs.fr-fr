---
title: Emplacement de l'assembly
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c736b4fe2a4bc38d4345413fa00d4cf7e5a80be7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607737"
---
# <a name="assembly-location"></a>Emplacement de l'assembly
L’emplacement d’un assembly détermine si le common language runtime peut le localiser quand il est référencé, et il peut aussi déterminer si l’assembly peut être partagé avec d’autres assemblys. Vous pouvez déployer un assembly dans les emplacements suivants :  
  
- Répertoire ou sous-répertoires de l’application.  
  
     Il s’agit de l’emplacement le plus courant pour déployer un assembly. Les sous-répertoires du répertoire racine d’une application peuvent être basés sur la langue ou la culture. Si un assembly a des informations de l’attribut de culture, il doit se trouver dans un sous-répertoire sous le répertoire de l’application avec le nom de cette culture.  
  
- Le Global Assembly Cache.  
  
     Il s’agit d’un cache de code au niveau de la machine, qui est installé partout où le common language runtime est installé. Dans la plupart des cas, si vous prévoyez de partager un assembly entre plusieurs applications, vous devez le déployer dans le Global Assembly Cache.  
  
- Sur un serveur HTTP.  
  
     Un assembly déployé sur un serveur HTTP doit avoir un nom fort ; vous pointez vers l’assembly dans la section codebase du fichier de configuration de l’application.  
  
## <a name="see-also"></a>Voir aussi

- [Création d’assemblys](../../../docs/framework/app-domains/create-assemblies.md)
- [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)
- [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)
