---
title: Déploiement d'une application d'interopérabilité
description: Déployez une application d’interopérabilité, qui a généralement un assembly client .NET, des assemblys d’interopérabilité de bibliothèques de types COM distinctes et des composants COM inscrits.
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
ms.openlocfilehash: 190b10ede4bc0037836d44332408d7752108346c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555066"
---
# <a name="deploying-an-interop-application"></a>Déploiement d'une application d'interopérabilité
Une application d’interopérabilité comporte généralement un assembly client .NET, un ou plusieurs assemblys d’interopérabilité représentant des bibliothèques de types COM distinctes, et un ou plusieurs composants COM inscrits. Visual Studio et le SDK Windows fournissent des outils pour importer et convertir une bibliothèque de types vers un assembly d’interopérabilité, comme décrit dans [Importation d’une bibliothèque de types sous la forme d’un assembly](importing-a-type-library-as-an-assembly.md). Il existe deux façons de déployer une application d’interopérabilité :  
  
- En utilisant les types Interop incorporés : à partir de l' .NET Framework 4, vous pouvez indiquer au compilateur d’incorporer les informations de type d’un assembly d’interopérabilité dans votre fichier exécutable. Le compilateur incorpore uniquement les informations de type que votre application utilise. Vous n’avez pas à déployer l’assembly d’interopérabilité avec votre application. Il s’agit de la technique recommandée.  
  
- En déployant des assemblys d’interopérabilité : vous pouvez créer une référence standard à un assembly d’interopérabilité. Dans ce cas, l’assembly d’interopérabilité doit être déployé avec votre application. Si vous utilisez cette technique et que vous n’utilisez pas un composant COM privé, référencez toujours l’assembly PIA (Primary Interop Assembly) publié par l’auteur du composant COM que vous prévoyez d’incorporer dans votre code managé. Pour plus d’informations sur la production et l’utilisation d’assemblys PIA (Primary Interop Assembly), consultez [Assemblys PIA (Primary Interop Assembly)](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
 Si vous utilisez des types interop incorporés, le déploiement est simple et direct. Vous n’avez rien de spécial à faire. Le reste de cet article décrit les scénarios de déploiement des assemblys d’interopérabilité avec votre application.  
  
## <a name="deploying-interop-assemblies"></a>Déploiement des assemblys d’interopérabilité  
 Les assemblys peuvent avoir des noms forts. Un assembly avec nom fort inclut la clé publique de l’éditeur, qui fournit une identité unique. Les assemblys qui sont produits par l’[importateur de bibliothèques de types (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) peuvent être signés par l’éditeur à l’aide de l’option **/keyfile**. Vous pouvez installer des assemblys signés dans le Global Assembly Cache. Les assemblys non signés doivent être installés sur la machine de l’utilisateur en tant qu’assemblys privés.  
  
### <a name="private-assemblies"></a>Assemblys privés  
 Pour installer un assembly destiné à une utilisation privée, vous devez installer l’exécutable de l’application et l’assembly d’interopérabilité qui contient les types COM importés dans la même structure de répertoires. L’illustration suivante montre un assembly d’interopérabilité non signé destiné à une utilisation privée par Client1.exe et Client2.exe, qui se trouvent dans des répertoires distincts de l’application. L’assembly d’interopérabilité, appelé LOANLib.dll dans cet exemple, est installé deux fois.  
  
 ![Structure de répertoire et Registre Windows](./media/deploying-an-interop-application/com-private-deployment.gif "Structure de répertoires et entrées du Registre pour un déploiement privé")  
  
 Tous les composants COM associés à l’application doivent être installés dans le Registre Windows. Si les fichiers Client1.exe et Client2.exe de l’illustration sont installés sur des ordinateurs différents, vous devez inscrire les composants COM sur les deux ordinateurs.  
  
### <a name="shared-assemblies"></a>Assemblys partagés  
 Les assemblys qui sont partagés par plusieurs applications doivent être installés dans un référentiel centralisé appelé le Global Assembly Cache. Les clients .NET peuvent accéder à la même copie de l’assembly d’interopérabilité, qui est signé et installé dans le Global Assembly Cache. Pour plus d’informations sur la production et l’utilisation d’assemblys PIA (Primary Interop Assembly), consultez [Assemblys PIA (Primary Interop Assembly)](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
## <a name="see-also"></a>Voir aussi

- [Exposition de composants COM au .NET Framework](exposing-com-components.md)
- [Importation d'une bibliothèque de types sous la forme d'un assembly](importing-a-type-library-as-an-assembly.md)
- [Utiliser des types COM dans du code managé](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Compilation d'un projet d'interopérabilité](compiling-an-interop-project.md)
