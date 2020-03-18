---
title: Contenu d’assembly
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: bee9d5422ec3101b2486f233ae0816ae3643f4e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75345576"
---
# <a name="assembly-contents"></a>Contenu d’assembly

En général, un assembly statique peut comporter les quatre éléments suivants :

- Le [manifeste d’assembly](manifest.md), qui contient les métadonnées de l’assembly.

- les métadonnées des types ;  

- le code MSIL (Microsoft Intermediate Language) qui implémente les types ; Il est généré par le compilateur à partir d’un ou plusieurs fichiers de code source.

- Un ensemble de [ressources](../../framework/resources/index.md).  

Seul le manifeste d'assembly est requis, mais soit les types, soit les ressources sont nécessaires pour donner à l'assembly des fonctionnalités significatives.

L’illustration suivante montre ces éléments regroupés en un seul fichier physique :

![Une assemblée à un seul fichier appelée MyAssembly.dll](./media/contents/single-file-assembly.gif)

Lorsque vous concevez votre code source, vous prenez des décisions explicites sur la façon de diviser la fonctionnalité de votre application dans un ou plusieurs fichiers. Lors de la conception de code .NET, vous prendrez des décisions similaires sur la façon de diviser la fonctionnalité en un ou plusieurs assemblages.

## <a name="see-also"></a>Voir aussi

- [Assemblys dans .NET](index.md)
- [Manifeste de l’Assemblée](manifest.md)
- [Aspects de la sécurité des assemblys](security-considerations.md)
