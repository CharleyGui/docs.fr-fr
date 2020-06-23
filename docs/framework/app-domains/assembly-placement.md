---
title: Emplacement des assemblys
description: Passez en revue les instructions relatives à l’emplacement des assemblys .NET dans les répertoires (par exemple, dans le Global Assembly Cache ou dans le répertoire ou sous-répertoire de l’application).
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 3106f6f01229057725cbc2e8e689a4e2247f95e6
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104957"
---
# <a name="assembly-placement"></a>Emplacement des assemblys
Pour la plupart des applications .NET Framework, vous localisez les assemblys qui composent une application dans le répertoire de l'application, dans un sous-répertoire de l'application ou dans le Global Assembly Cache (si l'assembly est partagé). Vous pouvez substituer l’emplacement où le common language runtime recherche un assembly à l’aide de l' [ \<codeBase> élément](../configure-apps/file-schema/runtime/codebase-element.md) dans un fichier de configuration. Si l’assembly n’a pas de nom fort, l’emplacement spécifié à l’aide de l' [ \<codeBase> élément](../configure-apps/file-schema/runtime/codebase-element.md) est limité au répertoire ou à un sous-répertoire de l’application. Si l’assembly a un nom fort, l' [ \<codeBase> élément](../configure-apps/file-schema/runtime/codebase-element.md) peut spécifier n’importe quel emplacement sur l’ordinateur ou sur un réseau.  
  
 Des règles similaires sont appliquées pour localiser des assemblys lors de l'utilisation d'applications de code non managé ou de COM Interop : si l'assembly est partagé par plusieurs applications, il doit alors être installé dans le Global Assembly Cache. Les assemblys utilisés avec du code non managé doivent être exportés en tant que bibliothèque de types et être inscrits. Les assemblys utilisés par COM Interop doivent être inscrits dans le catalogue, même si cette inscription s'effectue dans certains cas automatiquement.  
  
## <a name="see-also"></a>Voir aussi

- [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)
- [Configuration d’applications](../configure-apps/index.md)
- [Interopérabilité avec du code non managé](../interop/index.md)
- [Assemblys dans .NET](index.md)
