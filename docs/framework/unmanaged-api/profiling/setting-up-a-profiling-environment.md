---
title: Configuration d'un environnement de profilage
ms.date: 03/30/2017
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
ms.openlocfilehash: 32ebb868ea64a24fba80133b1a0eb539f51cb411
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176966"
---
# <a name="setting-up-a-profiling-environment"></a>Configuration d'un environnement de profilage
> [!NOTE]
> Il y a eu des changements substantiels au profilage dans le cadre .NET 4.  
  
 Quand un processus managé (application ou service) démarre, il charge le Common Language Runtime (CLR). Quand le CLR est initialisé, il évalue les deux variables environnementales suivantes afin de déterminer si le processus doit se connecter à un profileur :  
  
- COR_ENABLE_PROFILING : le CLR se connecte à un profileur uniquement si cette variable d'environnement existe et que sa valeur est 1.  
  
- COR_PROFILER : si la vérification COR_ENABLE_PROFILING réussit, le CLR se connecte au profileur qui a ce CLSID ou ProgID, lequel doit avoir été stocké précédemment dans le Registre. La variable d'environnement COR_PROFILER est définie en tant que chaîne, comme indiqué dans les deux exemples suivants.  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Pour profiler une application CLR, vous devez définir les variables d'environnement COR_ENABLE_PROFILING et COR_PROFILER avant d'exécuter l'application. Vous devez également vous assurer que la DLL du profileur est enregistrée.  
  
> [!NOTE]
> À partir du cadre .NET 4, les profileurs n’ont pas besoin d’être enregistrés.  
  
> [!NOTE]
> Pour utiliser les versions cadre .NET 2.0, 3.0 et 3.5 profileurs dans le cadre .NET 4 et les versions ultérieures, vous devez définir la variable COMPLUS_ProfAPI_ProfilerCompatibilitySetting environnement.  
  
## <a name="environment-variable-scope"></a>Étendue de la variable d'environnement  
 La manière dont vous définissez les variables d'environnement COR_ENABLE_PROFILING et COR_PROFILER déterminent leur champ d'influence. Vous pouvez définir ces variables de l'une des manières suivantes :  
  
- Si vous définissez les variables dans un [ICorDebug : : Appelez CreateProcess,](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) elles ne s’appliqueront qu’à l’application que vous exécutez à l’époque. (Elles s'appliquent également aux autres applications démarrées par l'application qui héritent de l'environnement.)  
  
- Si vous définissez les variables dans une fenêtre d'invite de commandes, elles s'appliquent à toutes les applications démarrées à partir de cette fenêtre.  
  
- Si vous définissez les variables au niveau de l'utilisateur, elles s'appliquent à toutes les applications que vous démarrez avec l'Explorateur de fichiers. Une fenêtre d'invite de commandes que vous ouvrez après avoir défini les variables présente ces paramètres d'environnement à l'instar de toute application que vous démarrez à partir de cette fenêtre. Pour définir les variables de l’environnement au niveau de l’utilisateur, cliquez à droite **sur Mon ordinateur,** cliquez sur **Propriétés,** cliquez sur l’onglet **Advanced,** cliquez sur **Environment Variables**et ajoutez les variables à la liste des **variables utilisateur.**  
  
- Si vous définissez les variables au niveau de l'ordinateur, elles s'appliquent à toutes les applications démarrées sur cet ordinateur. Une fenêtre d'invite de commandes que vous ouvrez sur cet ordinateur présente ces paramètres d'environnement à l'instar de toute application que vous démarrez à partir de cette fenêtre. Cela signifie que chaque processus managé sur cet ordinateur démarre avec votre profileur. Pour définir les variables de l’environnement au niveau de l’ordinateur, cliquez à droite **sur Mon ordinateur,** cliquez sur **Propriétés,** cliquez sur **l’onglet Advanced,** cliquez sur **Environment Variables**, ajoutez les variables à la liste des variables **du système,** puis redémarrez votre ordinateur. Après le redémarrage, les variables sont disponibles à l'échelle du système.  
  
 Si vous profilez un service Windows, vous devez redémarrer votre ordinateur après avoir défini les variables d'environnement et inscrit la DLL du profileur. Pour plus d’informations sur ces considérations, voir la section [Profiling a Windows Service](#windows_service).  
  
## <a name="additional-considerations"></a>Considérations supplémentaires  
  
- La classe profiler met en œuvre les interfaces [ICorProfilerCallback](icorprofilercallback-interface.md) et [ICorProfilerCallback2.](icorprofilercallback2-interface.md) Dans le .NET Framework version 2.0, un profileur doit implémenter `ICorProfilerCallback2`. Dans ce cas, `ICorProfilerCallback2` ne sera pas chargé.  
  
- Un seul profileur peut profiler un processus à la fois dans un environnement donné. Vous pouvez inscrire deux profileurs différents dans des environnements différents, mais chacun doit profiler des processus distincts. Le profileur doit être implémenté en tant que DLL de serveur COM in-process, mappée dans le même espace d'adressage que le processus en cours de profilage. Cela signifie que le profileur s'exécute in-process. Le .NET Framework ne prend pas en charge un autre type de serveur COM. Par exemple, si un profileur souhaite surveiller des applications à partir d'un ordinateur distant, il doit implémenter des agents collecteurs sur chaque ordinateur. Ces agents traitent les résultats par lots et les communiquent à l’ordinateur de collection de données central.  
  
- Étant donné que le profileur est un objet COM instancié in-process, chaque application profilée possède sa propre copie du profileur. Par conséquent, une instance de profileur particulière n'a pas à gérer les données de plusieurs applications. Toutefois, vous devrez ajouter une logique au code de journalisation du profileur pour éviter le remplacement du fichier journal d'autres applications profilées.  
  
## <a name="initializing-the-profiler"></a>Initialisation du profileur  
 Quand les deux vérifications de variables d'environnement réussissent, le CLR crée une instance du profileur d'une manière similaire à la fonction `CoCreateInstance` COM. Le profileur n'est pas chargé via un appel direct à `CoCreateInstance`. Par conséquent, un appel à `CoInitialize`, qui requiert la définition du modèle de thread, est évité. Le CLR appelle alors [l’ICorProfilerCallback: ::Méthode initialise](icorprofilercallback-initialize-method.md) dans le profileur. La signature de cette méthode est la suivante.  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Le profileur doit `pICorProfilerInfoUnk` demander un pointeur d’interface [ICorProfilerInfo](icorprofilerinfo-interface.md) ou [ICorProfilerInfo2](icorprofilerinfo2-interface.md) et l’enregistrer afin qu’il puisse demander plus d’informations plus tard pendant le profilage.  
  
## <a name="setting-event-notifications"></a>Définition de notifications d'événements  
 Le profileur appelle ensuite la méthode [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) pour spécifier les catégories de notifications qui l’intéressent. Par exemple, si le profileur s’intéresse uniquement aux notifications d’entrée et de sortie de fonction, ainsi qu’aux notifications de garbage collection, il spécifie ce qui suit.  
  
```cpp  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 En définissant le masque des notifications de cette manière, le profileur peut limiter les notifications qu'il reçoit. Cette approche permet à l'utilisateur de générer un profileur simple ou à but spécifique. Elle réduit également le temps processeur qui serait gaspillé en envoyant des notifications qui ne seraient qu'ignorées par le profileur.  
  
 Certains événements de profileur sont immuables. Cela signifie que, dès que ces événements sont définis dans le rappel `ICorProfilerCallback::Initialize`, ils ne peuvent pas être désactivés et aucun nouvel événement ne peut être activé. Toute tentative de modification d'un événement immuable entraîne le retour d'un HRESULT d'échec par `ICorProfilerInfo::SetEventMask`.  
  
<a name="windows_service"></a>
## <a name="profiling-a-windows-service"></a>Profilage d'un service Windows  
 Le profilage d'un service Windows s'apparente au profilage d'une application du Common Language Runtime. Les deux opérations de profilage sont activées via des variables d'environnement. Étant donné qu'un service Windows démarre au démarrage du système d'exploitation, les variables d'environnement décrites précédemment dans cette rubrique doivent déjà être présentes et définies sur les valeurs requises avant le démarrage du système. En outre, la DLL de profilage doit déjà être enregistrée sur le système.  
  
 Après avoir défini les variables d'environnement COR_ENABLE_PROFILING et COR_PROFILER, puis inscrit la DLL du profileur, vous devez redémarrer l'ordinateur cible pour que le service Windows puisse détecter ces modifications.  
  
 Notez que ces modifications activent le profilage à l'échelle du système. Pour empêcher le profilage de chaque application managée qui s'exécute par la suite, vous devez supprimer les variables d'environnement système après le redémarrage de l'ordinateur cible.  
  
 Cette technique entraîne également le profilage de chaque processus CLR. Le profileur devrait ajouter de la logique à son [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback pour détecter si le processus actuel est d’intérêt. Si ce n'est pas le cas, le profileur peut faire échouer le rappel sans exécuter l'initialisation.  
  
## <a name="see-also"></a>Voir aussi

- [Aperçu de profilage](profiling-overview.md)
