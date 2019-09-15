---
title: Emplacement des assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 829aa80169319b67a8cc5ee39fee9214cd4fcbce
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971639"
---
# <a name="assembly-placement"></a>Emplacement des assemblys
Pour la plupart des applications .NET Framework, vous localisez les assemblys qui composent une application dans le répertoire de l'application, dans un sous-répertoire de l'application ou dans le Global Assembly Cache (si l'assembly est partagé). Vous pouvez effectuer des remplacements là où le common language runtime recherche un assembly à l’aide de l’élément [\<codeBase>](../../framework/configure-apps/file-schema/runtime/codebase-element.md) dans un fichier de configuration. Si l’assembly n’a pas un nom fort, l’emplacement spécifié à l’aide de l’élément [\<codeBase>](../../framework/configure-apps/file-schema/runtime/codebase-element.md) est limité au répertoire ou à un sous-répertoire de l’application. Si l’assembly a un nom fort, l’élément [\<codeBase>](../../framework/configure-apps/file-schema/runtime/codebase-element.md) peut spécifier n’importe quel emplacement sur l’ordinateur ou sur un réseau.  
  
 Des règles similaires sont appliquées pour localiser des assemblys lors de l'utilisation d'applications de code non managé ou de COM Interop : si l'assembly est partagé par plusieurs applications, il doit alors être installé dans le Global Assembly Cache. Les assemblys utilisés avec du code non managé doivent être exportés en tant que bibliothèque de types et être inscrits. Les assemblys utilisés par COM Interop doivent être inscrits dans le catalogue, même si cette inscription s'effectue dans certains cas automatiquement.  
  
## <a name="see-also"></a>Voir aussi

- [Méthode de localisation des assemblys par le runtime](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Configuration d'applications](../../../docs/framework/configure-apps/index.md)
- [Interopération avec du code non managé](../../../docs/framework/interop/index.md)
- [Assemblys dans .NET](index.md)
