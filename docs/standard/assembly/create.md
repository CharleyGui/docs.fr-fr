---
title: Créer des assemblys
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 81fffb2b2e1d56d6068bf6f663a13fad6968a383
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740509"
---
# <a name="create-assemblies"></a>Créer des assemblys

Vous pouvez créer des assemblys monofichiers ou multifichiers à l’aide d’un IDE, comme Visual Studio, ou des compilateurs et des outils fournis par le SDK Windows. L’assembly le plus simple est un fichier unique qui a un nom simple et qui est chargé dans un seul domaine d’application. Cet assembly ne peut pas être référencé par d’autres assemblys en dehors du répertoire de l’application et n’est pas soumis à la vérification de la version. Pour désinstaller l’application constituée de l’assembly, vous supprimez simplement le répertoire où il se trouve. Pour de nombreux développeurs, un assembly avec ces fonctionnalités est tout ce qui est nécessaire pour déployer une application.

Vous pouvez créer un assembly multifichier à partir de plusieurs modules de code et fichiers de ressources. Vous pouvez également créer un assembly qui peut être partagé par plusieurs applications. Un assembly partagé doit avoir un nom fort et peut être déployé dans le Global Assembly Cache.

Vous disposez de plusieurs options quand vous regroupez des modules de code et des ressources dans des assemblys, en fonction des facteurs suivants :

- Contrôle de version

     Regroupez les modules qui doivent avoir les mêmes informations de version.

- Déploiement

     Regroupez les modules de code et les ressources qui prennent en charge votre modèle de déploiement.

- Réutilisation

     Regroupez les modules s’ils peuvent être logiquement utilisés ensemble dans le même but. Par exemple, un assembly constitué de types et de classes peu utilisés pour la maintenance du programme peut être placé dans le même assembly. En outre, les types que vous prévoyez de partager avec plusieurs applications doivent être regroupés dans un assembly, et celui-ci doit être signé avec un nom fort.

- Sécurité

     Regroupez les modules contenant des types qui nécessitent les mêmes autorisations de sécurité.

- Scoping

     Regroupez les modules contenant des types dont la visibilité doit être limitée au même assembly.

Il y a des considérations particulières lorsque l’on peut mettre des assemblages de temps d’exécution de langage commun à la disposition des applications COM non gérées. Pour plus d’informations sur le travail avec le code non-gestion, voir [Expose .NET Composants cadre à COM](../../framework/interop/exposing-dotnet-components-to-com.md).

## <a name="see-also"></a>Voir aussi

- [Contrôle de version des assemblys](versioning.md)
- [Comment : Construire un assemblage à un seul fichier](../../framework/app-domains/build-single-file-assembly.md)
- [Comment : Construire un assemblage multifils](../../framework/app-domains/build-multifile-assembly.md)
- [Comment le temps d’exécution localise les assemblages](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Assemblys multifichiers](../../framework/app-domains/multifile-assemblies.md)
