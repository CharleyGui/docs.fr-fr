---
title: Contenu d’assembly
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- assemblies [.NET Core]
- single-file assemblies
- multifile assemblies [.NET Framework]
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: 9ca12ee4bd993db3dd200a3b340c220ce5188796
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122534"
---
# <a name="assembly-contents"></a>Contenu d’assembly
En général, un assembly statique peut comporter les quatre éléments suivants :

- Le [manifeste d’assembly](manifest.md), qui contient les métadonnées de l’assembly.

- les métadonnées des types ;  

- le code MSIL (Microsoft Intermediate Language) qui implémente les types ; Il est généré par le compilateur à partir d’un ou de plusieurs fichiers de code source.

- un ensemble de ressources.  

Seul le manifeste d'assembly est requis, mais soit les types, soit les ressources sont nécessaires pour donner à l'assembly des fonctionnalités significatives.

L’illustration suivante montre ces éléments regroupés dans un seul fichier physique.

![Diagramme qui montre un assembly à fichier unique appelé MyAssembly.dll.](./media/contents/single-file-assembly.gif)

Dans cette illustration, les trois fichiers appartiennent à un assembly, comme décrit dans le manifeste de l'assembly contenu dans MyAssembly.dll. Pour le système de fichiers, il s'agit de trois fichiers distincts. Notez que le fichier Util.netmodule a été compilé comme un module car il ne contient pas d'information sur l'assembly. Lorsque l'assembly a été créé, le manifeste de l'assembly a été ajouté à MyAssembly.dll, en indiquant sa relation avec Util.netmodule et Graphic.bmp.

Actuellement, à mesure que vous concevez votre code source, vous prenez des décisions explicites concernant le mode de partition des fonctionnalités de votre application dans un ou plusieurs fichiers. Lors du design de code .NET Framework, vous prendrez des décisions similaires sur le mode de partition des fonctionnalités dans un ou plusieurs assemblys.

## <a name="see-also"></a>Voir aussi

- [Assemblys dans .NET](index.md)
- [Manifeste d’assembly](manifest.md)
- [Considérations sur la sécurité des assemblys](security-considerations.md)
