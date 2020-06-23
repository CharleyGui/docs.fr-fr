---
title: Global Assembly Cache
description: Comprendre le Global Assembly Cache, qui est un cache de code à l’ensemble de l’ordinateur où le common language runtime pour .NET est installé.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
ms.openlocfilehash: 7f08bb4cf279924b12432f259dae8ce5a8474285
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104914"
---
# <a name="global-assembly-cache"></a>Global Assembly Cache
Sur chaque ordinateur où le Common Language Runtime est installé, il y a un cache de code machine appelé Global Assembly Cache. Le Global Assembly Cache stocke des assemblys spécialement destinés à être partagés entre plusieurs applications sur l’ordinateur.  
  
 Partagez des assemblys en les installant dans le Global Assembly Cache uniquement si cela est nécessaire. En règle générale, vous devez maintenir les dépendances d’assembly privées et rechercher les assemblys dans le répertoire de l’application, sauf si le partage d’un assembly est explicitement requis. De plus, il n’est pas nécessaire d’installer des assemblys dans le Global Assembly Cache pour les rendre accessibles à COM Interop ou au code non managé.  
  
> [!NOTE]
> Dans certains scénarios, vous ne devez pas installer d’assembly dans le Global Assembly Cache. Si vous placez l’un des assemblys composant une application dans le Global Assembly Cache, vous ne pouvez plus répliquer ni installer l’application en utilisant la commande **xcopy** pour copier le répertoire de l’application. Vous devez également déplacer l’assembly dans le Global Assembly Cache.  
  
 Il existe deux manières de déployer un assembly dans le Global Assembly Cache :  
  
- Utiliser un programme d’installation conçu pour fonctionner avec le Global Assembly Cache. Il s’agit de l’option par défaut d’installation des assemblys dans le Global Assembly Cache.  
  
- Utiliser un outil de développement appelé [Outil Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) fourni par le SDK Windows.  
  
    > [!NOTE]
    > Dans les scénarios de déploiement, utilisez Windows Installer pour installer des assemblys dans le Global Assembly Cache. Utilisez l’outil Global Assembly Cache uniquement dans les scénarios de développement, car il ne propose pas de fonctionnalités de décompte des références d’assembly et d’autres fonctionnalités disponibles lors de l’utilisation de Windows Installer.  
  
 À compter du .NET Framework 4, l’emplacement par défaut du Global Assembly Cache est **%windir%\Microsoft.NET\assembly**. Dans les versions antérieures du .NET Framework, l’emplacement par défaut est **%windir%\assembly**.  
  
 Les administrateurs protègent souvent le répertoire systemroot en utilisant une liste de contrôle d’accès pour contrôler l’accès en écriture et en exécution. Le Global Assembly Cache étant installé dans un sous-répertoire du répertoire systemroot, il hérite de la liste ACL de ce répertoire. Il est recommandé que seuls les utilisateurs ayant des privilèges d’administrateur soient autorisés à supprimer des fichiers du Global Assembly Cache.  
  
 Les assemblys déployés dans le Global Assembly Cache doivent avoir un nom fort. Quand un assembly est ajouté au Global Assembly Cache, des contrôles d’intégrité sont effectués sur tous les fichiers qui composent l’assembly. Le cache effectue ces contrôles d’intégrité pour vérifier qu’aucun assembly n’a été falsifié, par exemple quand un fichier a changé mais que le manifeste ne reflète pas ce changement.  
  
## <a name="see-also"></a>Voir aussi

- [Assemblys dans .NET](../../standard/assembly/index.md)
- [Utilisation d'assemblys et du Global Assembly Cache](working-with-assemblies-and-the-gac.md)
- [Assemblys avec nom fort](../../standard/assembly/strong-named.md)
