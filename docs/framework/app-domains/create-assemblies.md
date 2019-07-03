---
title: Création d'assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e544976b0b801b08af238b2aeb36b5611154379
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832900"
---
# <a name="creating-assemblies"></a>Création d'assemblys

Vous pouvez créer des assemblys monofichiers ou multifichiers à l’aide d’un IDE, comme Visual Studio, ou des compilateurs et des outils fournis par le kit de développement logiciel (SDK) Windows. L’assembly le plus simple est un fichier unique qui a un nom simple et qui est chargé dans un seul domaine d’application. Cet assembly ne peut pas être référencé par d’autres assemblys en dehors du répertoire de l’application et n’est pas soumis à la vérification de la version. Pour désinstaller l’application constituée de l’assembly, vous supprimez simplement le répertoire où il se trouve. Pour de nombreux développeurs, un assembly avec ces fonctionnalités est tout ce qui est nécessaire pour déployer une application.

Vous pouvez créer un assembly multifichier à partir de plusieurs modules de code et fichiers de ressources. Vous pouvez également créer un assembly qui peut être partagé par plusieurs applications. Un assembly partagé doit avoir un nom fort et peut être déployé dans le Global Assembly Cache.

Vous disposez de plusieurs options quand vous regroupez des modules de code et des ressources dans des assemblys, en fonction des facteurs suivants :

- Gestion de version

     Regroupez les modules qui doivent avoir les mêmes informations de version.

- Déploiement

     Regroupez les modules de code et les ressources qui prennent en charge votre modèle de déploiement.

- Réutilisation

     Regroupez les modules s’ils peuvent être logiquement utilisés ensemble dans le même but. Par exemple, un assembly constitué de types et de classes peu utilisés pour la maintenance du programme peut être placé dans le même assembly. En outre, les types que vous prévoyez de partager avec plusieurs applications doivent être regroupés dans un assembly, et celui-ci doit être signé avec un nom fort.

- Sécurité

     Regroupez les modules contenant des types qui nécessitent les mêmes autorisations de sécurité.

- Portée

     Regroupez les modules contenant des types dont la visibilité doit être limitée au même assembly.

Des considérations particulières sont à prendre en compte quand des assemblys du common language runtime sont rendus disponibles pour des applications COM non managées. Pour plus d’informations sur l’utilisation de code non managé, consultez [Exposition de composants .NET Framework à COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).

## <a name="see-also"></a>Voir aussi

- [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Contrôle de version des assemblys](../../../docs/framework/app-domains/assembly-versioning.md)
- [Guide pratique pour générer un assembly à fichier unique](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [Guide pratique pour générer un assembly multifichier](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Assemblys multifichiers](../../../docs/framework/app-domains/multifile-assemblies.md)
