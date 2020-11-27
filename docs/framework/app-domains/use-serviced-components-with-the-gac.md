---
title: Utilisation de composants de service avec le Global Assembly Cache
description: Utilisez les composants de service (composants COM+ de code managé) avec le Global Assembly Cache dans .NET. Vérifiez si les services CLR et COM+ peuvent gérer des composants non-GAC.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
ms.openlocfilehash: 314f804dfcaee64ef364cc881ae76651961294d7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254582"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Utilisation de composants de service avec le Global Assembly Cache

Les composants pris en charge (composants COM+ de code managé) doivent être placés dans le Global Assembly Cache. Dans certains scénarios, le Common Language Runtime et les services COM+ peuvent gérer des composants pris en charge qui ne sont pas dans le Global Assembly Cache ; dans d’autres scénarios, cela est impossible. Les scénarios suivants illustrent ce principe :  
  
- Pour les composants pris en charge dans une application serveur COM+, l’assembly contenant les composants doit être dans le Global Assembly Cache, car Dllhost.exe ne s’exécute pas dans le même répertoire que celui qui contient les composants pris en charge.  
  
- Pour les composants pris en charge dans une application bibliothèque COM+, le runtime et les services COM+ peuvent résoudre la référence à l’assembly contenant les composants en effectuant une recherche dans le répertoire actif. Dans ce cas, l’assembly ne devra pas se trouver dans le Global Assembly Cache.  
  
- Pour les composants pris en charge dans une application ASP.NET, la situation est différente. Si vous placez l’assembly contenant les composants pris en charge dans le répertoire bin de la base de l’application, et que vous utilisez l’inscription à la demande, l’assembly sera mis en mémoire fantôme dans le cache de téléchargement, car ASP.NET tire parti des possibilités de mémoire fantôme du runtime.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d'assemblys et du Global Assembly Cache](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Outil Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
