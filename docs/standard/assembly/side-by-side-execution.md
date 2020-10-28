---
title: Assemblys et exécution côte à côte
description: En savoir plus sur l’exécution côte à côte, qui est la possibilité de stocker et d’exécuter plusieurs versions d’une application ou d’un composant sur le même ordinateur.
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET]
- assemblies [.NET], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 7bedd5a384ceace014412eb894adad5c92c00b05
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687984"
---
# <a name="assemblies-and-side-by-side-execution"></a>Assemblys et exécution côte à côte

L'exécution côte à côte consiste à stocker et exécuter plusieurs versions d'une application ou d'un composant sur un même ordinateur. Cela signifie que peuvent coexister simultanément sur un même ordinateur plusieurs versions du runtime ainsi que plusieurs versions d'applications et de composants utilisant une version du runtime. L'exécution côte à côte vous offre un meilleur contrôle des versions auxquelles peut être liée une application ainsi que de la version du runtime utilisée par une application.  
  
La prise en charge du stockage et de l'exécution côte à côte de différentes versions du même assembly fait partie intégrante de l'attribution des noms forts et se trouve intégrée à l'infrastructure du runtime. Comme le numéro de version de l'assembly avec nom fort fait partie de son identité, le runtime peut stocker plusieurs versions du même assembly dans le Global Assembly Cache et charger ces assemblys au moment de l'exécution.  
  
Bien que le runtime vous permette de créer des applications côte à côte, l'exécution côte à côte n'est pas automatique. Pour plus d’informations sur la création d’applications pour l’exécution côte à côte, consultez [instructions pour la création de composants pour l’exécution côte à côte](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Voir aussi

- [Comment le runtime localise les assemblys](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Assemblys dans .NET](index.md)
