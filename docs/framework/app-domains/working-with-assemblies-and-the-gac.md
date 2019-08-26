---
title: Utilisation d'assemblys et du Global Assembly Cache
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62760cb9fe5832ee018ebdebf6275ea61691c738
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927799"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a>Utilisation d'assemblys et du Global Assembly Cache
Si vous prévoyez de partager un assembly entre plusieurs applications, vous pouvez l’installer dans le Global Assembly Cache. Chaque ordinateur où le common language runtime est installé a ce cache de code à l’échelle de l’ordinateur. Le Global Assembly Cache stocke des assemblys spécialement destinés à être partagés entre plusieurs applications sur l’ordinateur. Un assembly doit avoir un nom fort pour être installé dans le Global Assembly Cache.  
  
> [!NOTE]
> Les assemblys placés dans le Global Assembly Cache doivent avoir le même nom d’assembly et le même nom de fichier (sans l’extension du nom de fichier). Par exemple, un assembly avec le nom d’assembly monAssembly doit avoir le nom de fichier monAssembly.exe ou monAssembly.dll.  
  
 Il est recommandé de partager des assemblys en les installant dans le Global Assembly Cache seulement quand c’est nécessaire. Une règle générale est de conserver les dépendances d’assembly privées et de placer les assemblys dans le répertoire de l’application, sauf si le partage d’un assembly est explicitement nécessaire. En outre, il n’est pas nécessaire d’installer des assemblys dans le Global Assembly Cache pour les rendre accessibles à COM Interop ou à du code non managé.  
  
 Vous pouvez souhaiter installer un assembly dans le Global Assembly Cache pour plusieurs raisons :  
  
- Emplacement partagé.  
  
     Les assemblys qui doivent être utilisés par des applications peuvent être placés dans le Global Assembly Cache. Par exemple, si toutes les applications doivent utiliser un assembly qui se trouve dans le Global Assembly Cache, vous pouvez ajouter une instruction de stratégie de version au fichier Machine.config pour rediriger les références à l’assembly.  
  
- Sécurité des fichiers.  
  
     Les administrateurs protègent souvent le répertoire systemroot en utilisant une liste de contrôle d’accès pour contrôler l’accès en écriture et en exécution. Le Global Assembly Cache étant installé dans le répertoire systemroot, il hérite de la liste de contrôle d’accès de ce répertoire. Il est recommandé que seuls les utilisateurs disposant de privilèges d’administrateur soient autorisés à supprimer des fichiers du Global Assembly Cache.  
  
- Contrôle de version côte à côte.  
  
     Plusieurs copies des assemblys avec le même nom mais avec des informations de version différentes peuvent être conservées dans le Global Assembly Cache.  
  
- Emplacements de recherche supplémentaires.  
  
     Le common language runtime recherche dans le Global Assembly Cache un assembly qui correspond à l’assembly demandé avant de chercher ailleurs ou d’utiliser les informations du code base dans un fichier de configuration.  
  
 Notez que dans certains scénarios, vous ne voulez explicitement pas installer un assembly dans le Global Assembly Cache. Si vous placez un des assemblys composant une application dans le Global Assembly Cache, vous ne pouvez plus répliquer ni installer l’application en utilisant XCOPY pour copier le répertoire de l’application. Dans ce cas, vous devez également déplacer l’assembly dans le Global Assembly Cache.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour installer un assembly dans le Global Assembly Cache](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 Décrit les façons d’installer un assembly dans le Global Assembly Cache.  
  
 [Guide pratique pour visualiser le contenu du Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).  
 Explique comment utiliser [Gacutil.exe (outil Global Assembly Cache](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pour visualiser le contenu du Global Assembly Cache.  
  
 [Guide pratique pour supprimer un assembly du Global Assembly Cache](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 Explique comment utiliser [Gacutil.exe (outil Global Assembly Cache](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pour supprimer un assembly du Global Assembly Cache.  
  
 [Utilisation de composants de service avec le Global Assembly Cache](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 Explique pourquoi les composants traités (composants COM+ managés) doivent être placés dans le Global Assembly Cache.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’assemblys](../../../docs/framework/app-domains/create-assemblies.md)  
 Fournit une vue d’ensemble de la création d’assemblys.  
  
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)  
 Décrit le Global Assembly Cache.  
  
 [Guide pratique pour afficher le contenu d’un assembly](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Explique comment utiliser [Ildasm.exe (Désassembleur IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour visualiser les informations du langage MSIL (Microsoft Intermediate Language) dans un assembly.  
  
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Décrit comment le common language runtime localise et charge les assemblys qui composent votre application.  
  
 [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Décrit les assemblys, les blocs de construction des applications managées.
