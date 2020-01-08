---
title: Contenu d’assembly
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: bee9d5422ec3101b2486f233ae0816ae3643f4e7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345576"
---
# <a name="assembly-contents"></a>Contenu d’assembly

En général, un assembly statique peut comporter les quatre éléments suivants :

- Le [manifeste d’assembly](manifest.md), qui contient les métadonnées de l’assembly.

- les métadonnées des types ;  

- le code MSIL (Microsoft Intermediate Language) qui implémente les types ; Il est généré par le compilateur à partir d’un ou de plusieurs fichiers de code source.

- Ensemble de [ressources](../../framework/resources/index.md).  

Seul le manifeste d'assembly est requis, mais soit les types, soit les ressources sont nécessaires pour donner à l'assembly des fonctionnalités significatives.

L’illustration suivante montre ces éléments regroupés dans un seul fichier physique :

![Un assembly à fichier unique appelé MyAssembly. dll](./media/contents/single-file-assembly.gif)

Lorsque vous concevez votre code source, vous prenez des décisions explicites sur la façon de partitionner les fonctionnalités de votre application dans un ou plusieurs fichiers. Lorsque vous concevez du code .NET, vous prendrez des décisions similaires quant à la façon de partitionner les fonctionnalités dans un ou plusieurs assemblys.

## <a name="see-also"></a>Voir aussi

- [Assemblys dans .NET](index.md)
- [Manifeste d’assembly](manifest.md)
- [Considérations sur la sécurité des assemblys](security-considerations.md)
