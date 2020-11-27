---
title: Utilisation d'assemblys et du Global Assembly Cache
description: Travaillez avec les assemblys et le Global Assembly Cache (GAC) dans .NET. Examinez les raisons pour lesquelles vous pouvez souhaiter installer un assembly dans le GAC.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
ms.openlocfilehash: e27fdd7def2d234e1e8eb7557e869bf478d68210
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279309"
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

[Comment : installer un assembly dans le global assembly cache](install-assembly-into-gac.md)  
Décrit les façons d’installer un assembly dans le Global Assembly Cache.  
  
[Procédure : Visualiser le contenu du Global Assembly Cache](how-to-view-the-contents-of-the-gac.md)  
Explique comment utiliser [Gacutil.exe (outil Global Assembly Cache](../tools/gacutil-exe-gac-tool.md) pour visualiser le contenu du Global Assembly Cache.  
  
[Procédure : supprimer un assembly du Global Assembly Cache](how-to-remove-an-assembly-from-the-gac.md)  
Explique comment utiliser [Gacutil.exe (outil Global Assembly Cache](../tools/gacutil-exe-gac-tool.md) pour supprimer un assembly du Global Assembly Cache.  
  
[Utilisation de composants de service avec le Global Assembly Cache](use-serviced-components-with-the-gac.md)  
Explique pourquoi les composants traités (composants COM+ managés) doivent être placés dans le Global Assembly Cache.  
  
## <a name="related-sections"></a>Sections connexes  

[Création d’assemblys](../../standard/assembly/create.md)  
Fournit une vue d’ensemble de la création d’assemblys.  
  
[Global Assembly Cache](gac.md)  
Décrit le Global Assembly Cache.  
  
[Guide pratique pour afficher le contenu d’un assembly](../../standard/assembly/view-contents.md)  
Explique comment utiliser [Ildasm.exe (Désassembleur IL)](../tools/ildasm-exe-il-disassembler.md) pour visualiser les informations du langage MSIL (Microsoft Intermediate Language) dans un assembly.  
  
[Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)  
Décrit comment le common language runtime localise et charge les assemblys qui composent votre application.  
  
[Programmation à l’aide d’assemblys](../../standard/assembly/index.md)  
Décrit les assemblys, les blocs de construction des applications managées.
