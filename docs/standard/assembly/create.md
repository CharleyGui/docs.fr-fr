---
title: Créer des assemblys
description: Découvrez comment créer des assemblys à fichier unique ou multifichiers à l’aide d’un IDE, tel que Visual Studio, ou les compilateurs et les outils fournis par le SDK Windows.
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET], multifile
- single-file assemblies
- assemblies [.NET], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: e1b08e40ae3b4c377cec52cb1ebf6db643af6429
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160579"
---
# <a name="create-assemblies"></a>Créer des assemblys

Vous pouvez créer des assemblys monofichiers ou multifichiers à l’aide d’un IDE, comme Visual Studio, ou des compilateurs et des outils fournis par le SDK Windows. L’assembly le plus simple est un fichier unique qui a un nom simple et qui est chargé dans un seul domaine d’application. Cet assembly ne peut pas être référencé par d’autres assemblys en dehors du répertoire de l’application et n’est pas soumis à la vérification de la version. Pour désinstaller l’application constituée de l’assembly, vous supprimez simplement le répertoire où il se trouve. Pour de nombreux développeurs, un assembly avec ces fonctionnalités est tout ce qui est nécessaire pour déployer une application.

Vous pouvez créer un assembly multifichier à partir de plusieurs modules de code et fichiers de ressources. Vous pouvez également créer un assembly qui peut être partagé par plusieurs applications. Un assembly partagé doit avoir un nom fort et peut être déployé dans le Global Assembly Cache.

Vous disposez de plusieurs options quand vous regroupez des modules de code et des ressources dans des assemblys, en fonction des facteurs suivants :

- Gestion de version

     Regroupez les modules qui doivent avoir les mêmes informations de version.

- Déploiement

     Regroupez les modules de code et les ressources qui prennent en charge votre modèle de déploiement.

- Réutiliser

     Regroupez les modules s’ils peuvent être logiquement utilisés ensemble dans le même but. Par exemple, un assembly constitué de types et de classes peu utilisés pour la maintenance du programme peut être placé dans le même assembly. En outre, les types que vous prévoyez de partager avec plusieurs applications doivent être regroupés dans un assembly, et celui-ci doit être signé avec un nom fort.

- Sécurité

     Regroupez les modules contenant des types qui nécessitent les mêmes autorisations de sécurité.

- Scoping

     Regroupez les modules contenant des types dont la visibilité doit être limitée au même assembly.

Des considérations particulières sont à prendre en compte lors de la mise à disposition des assemblys de common language runtime pour les applications COM non managées. Pour plus d’informations sur l’utilisation de code non managé, consultez [exposer des .NET Framework Components à com](../../framework/interop/exposing-dotnet-components-to-com.md).

## <a name="see-also"></a>Voir aussi

- [Contrôle de version des assemblys](versioning.md)
- [Procédure : Générer un assembly monofichier](../../framework/app-domains/build-single-file-assembly.md)
- [Procédure : Générer un assembly multifichier](../../framework/app-domains/build-multifile-assembly.md)
- [Comment le runtime localise les assemblys](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Assemblys multifichiers](../../framework/app-domains/multifile-assemblies.md)
