---
title: Génération de profils d'exécution
description: Explorez le profilage du runtime dans .NET, qui est une méthode de collecte des données de performances dans tout scénario de développement ou de déploiement.
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters
- common language runtime, profiling
- Perfmon.exe
- System Monitor
- profiling
- runtime, profiling
- profiling applications
- Performance Console
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
ms.openlocfilehash: 5d1542c7f6afa2d683240d6d5cca837b961eb3be
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267102"
---
# <a name="runtime-profiling"></a>Génération de profils d'exécution

Le profilage est une méthode de collecte de données de performance dans le cadre d’un scénario de développement ou de déploiement. Cette section s’adresse aux développeurs et administrateurs système qui souhaitent recueillir des informations sur les performances d’une application.  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>Suivi des performances à l’aide de l’analyseur de performances (Perfmon.exe)  

 L’analyseur de performances est l’outil le plus simple à utiliser pour profiler votre application .NET Framework. L’analyseur de performances représente graphiquement les données trouvées dans les compteurs de performance .NET Framework installés avec le common language runtime et le SDK Windows. Ces compteurs permettent de tout surveiller, de la gestion de la mémoire jusqu’aux performances du compilateur juste-à-temps (JIT). Ils vous renseignent sur les ressources que votre application utilise, ce qui est une mesure indirecte des performances de votre application. Ces compteurs s’avèrent utiles pour comprendre le fonctionnement interne de votre application.  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>Pour exécuter Perfmon.exe sur Windows Vista et les versions ultérieures  
  
1. À l'invite de commandes, entrez **perfmon**. La console **Analyseur de performances** apparaît.  
  
2. Dans le dossier **Outils d’analyse** , cliquez sur **Analyseur de performances**.  
  
3. Dans la barre d’outils de l’analyseur de performances, cliquez sur l’icône **Ajouter** (signe plus), si elle est présente. À défaut, cliquez avec le bouton droit dans la fenêtre de l’analyseur et sélectionnez l’option **Ajouter des compteurs** .  
  
     La boîte de dialogue **Ajouter des compteurs** s’ouvre. La zone de liste **Compteurs disponibles** présente les objets de performance disponibles. Il existe plusieurs objets prédéfinis pour les applications .NET Framework, notamment ceux qui touchent à la gestion de la mémoire (**.NET CLR Memory**), à l’interopérabilité (**.NET CLR Interop**), à la gestion des exceptions (**.NET CLR Exceptions**) et au multithreading (**.NET CLR LocksAndThreads**). Chaque objet de performance comprend un certain nombre de compteurs de performances individuels. Pour obtenir la liste des compteurs de performances disponibles dans l’analyseur de performances, consultez [Performance Counters](performance-counters.md).  
  
4. Cochez la case en regard du nom d’un objet de performance pour afficher la liste des compteurs de performances individuels qu’il prend en charge.  
  
5. Cliquez sur le compteur de performances que vous voulez afficher.  
  
6. Dans la zone **de liste instances de l’objet sélectionné** , cliquez sur **\<All instances>** cette option pour spécifier que vous souhaitez analyser le compteur de performance pour la Common Language Runtime globalement (c’est-à-dire à l’échelle du système).  
  
     -ou-  
  
     Dans la zone de liste **Instances de l’objet sélectionné** , cliquez sur le nom d’une application pour analyser le compteur de performances de cette application.  
  
     Pour différencier plusieurs versions du runtime ou pour lever toute ambiguïté quant aux applications qui ont le même nom, vous devez aussi modifier une clé de Registre. Pour plus d'informations, consultez [Performance Counters and In-Process Side-By-Side Applications](performance-counters-and-in-process-side-by-side-applications.md).  
  
> [!NOTE]
> Si des compteurs de performances nouveaux sont installés pendant l’exécution de la console de performances, arrêtez et redémarrez la console de performances pour les rendre visibles.  
  
 Si vous voulez profiler un assembly qui existe dans une zone ou sur un partage distant, assurez-vous que l’assembly distant bénéficie d’une confiance totale sur l’ordinateur qui exécute les compteurs de performances. Si l’assembly n’a pas un niveau de confiance suffisant, les compteurs de performances ne fonctionnent pas. Pour plus d’informations sur l’octroi de confiance à différentes zones, consultez [Caspol.exe (outil Stratégie de sécurité d’accès du code)](../tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
> Sur les systèmes sur lesquels le .NET Framework 4 est installé, l’analyseur de performances peut ne pas afficher les données des compteurs de performances dans certaines catégories, telles que les **données CLR .net** et la **mise en réseau CLR .net**, pour les applications développées à l’aide de la .NET Framework 1,1. Si c’est le cas, vous pouvez configurer l’analyseur de performances pour afficher ces données en ajoutant l' [\<forcePerformanceCounterUniqueSharedMemoryReads>](../configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) élément au fichier de configuration de l’application.  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>Lecture et création de compteurs de performances par programmation  

 Le .NET Framework fournit des classes que vous pouvez utiliser pour accéder par programmation aux mêmes informations de performances que celles disponibles dans la console de performances. Vous pouvez aussi utiliser ces classes pour créer des compteurs de performances personnalisés. Le tableau suivant décrit quelques-unes des classes d’analyse des performances fournies dans le .NET Framework.  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|Représente un composant de compteur de performances Windows NT. Cette classe permet de lire les compteurs prédéfinis ou personnalisés existants et de publier (écrire) des données de performance dans des compteurs personnalisés.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|Propose plusieurs méthodes permettant d’interagir avec les compteurs et les catégories de compteurs de l’ordinateur.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|Spécifie un programme d’installation pour le composant `PerformanceCounter` .|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|Spécifie la formule de calcul de la méthode `NextValue` pour un `PerformanceCounter`.|  
  
## <a name="see-also"></a>Voir aussi

- [Compteurs de performance](performance-counters.md)
