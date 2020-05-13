---
title: Contenu d’assembly
description: Cet article décrit le contenu d’un assembly .NET, qui peut inclure des métadonnées d’assembly, des métadonnées de type, du code MSIL et des ressources.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: 94df452162ed7290fab7fa267d2624e6d844a587
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378565"
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
- [Aspects de la sécurité des assemblys](security-considerations.md)
