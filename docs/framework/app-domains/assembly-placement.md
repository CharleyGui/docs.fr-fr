---
title: Emplacement des assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 5eb7b5c35bb40d5a58390ccbd4619cbed4e06c52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119957"
---
# <a name="assembly-placement"></a>Emplacement des assemblys
Pour la plupart des applications .NET Framework, vous localisez les assemblys qui composent une application dans le répertoire de l'application, dans un sous-répertoire de l'application ou dans le Global Assembly Cache (si l'assembly est partagé). Vous pouvez substituer l’emplacement où le Common Language Runtime recherche un assembly à l’aide de l' [ \<élément CodeBase>](../configure-apps/file-schema/runtime/codebase-element.md) dans un fichier de configuration. Si l’assembly n’a pas de nom fort, l’emplacement spécifié à l’aide de l' [ \<élément CodeBase>](../configure-apps/file-schema/runtime/codebase-element.md) est limité au répertoire ou à un sous-répertoire de l’application. Si l’assembly a un nom fort, l' [ \<élément CodeBase>](../configure-apps/file-schema/runtime/codebase-element.md) peut spécifier n’importe quel emplacement sur l’ordinateur ou sur un réseau.  
  
 Des règles similaires sont appliquées pour localiser des assemblys lors de l'utilisation d'applications de code non managé ou de COM Interop : si l'assembly est partagé par plusieurs applications, il doit alors être installé dans le Global Assembly Cache. Les assemblys utilisés avec du code non managé doivent être exportés en tant que bibliothèque de types et être inscrits. Les assemblys utilisés par COM Interop doivent être inscrits dans le catalogue, même si cette inscription s'effectue dans certains cas automatiquement.  
  
## <a name="see-also"></a>Voir aussi

- [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)
- [Configuration d'applications](../configure-apps/index.md)
- [Interopération avec du code non managé](../interop/index.md)
- [Assemblys dans .NET](index.md)
