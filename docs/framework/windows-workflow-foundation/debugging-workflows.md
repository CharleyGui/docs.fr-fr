---
title: Débogage de workflows
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: 12b85260f8eab87fc9b98a99ca1192fd307313d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915410"
---
# <a name="debugging-workflows"></a>Débogage de workflows
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] offre plusieurs options permettant de déboguer des workflows en cours d'exécution à partir de l'environnement de développement. Les workflows peuvent être débogués dans le concepteur, dans XAML et dans le code.  
  
## <a name="debugging-in-the-workflow-designer"></a>Débogage dans le concepteur de workflow  
 Les points d’arrêt peuvent être définis sur des activités dans le concepteur de flux de travail en mettant en surbrillance l’activité et en appuyant sur **F9** ou en utilisant le menu contextuel de l’activité. Ainsi, l'exécution du workflow s'arrête lorsque l'hôte de workflow est exécuté en mode débogage. Dans la capture d'écran suivante, l'exécution du workflow est suspendue à un point d'arrêt. Pour plus d’informations, consultez Débogage de [flux de travail avec l’Concepteur de flux de travail](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).  
  
## <a name="debugging-in-xaml"></a>Débogage dans XAML  
 Si un workflow a suspendu son exécution à un point d'arrêt dans le concepteur, le workflow peut également être débogué dans XAML. Pour afficher le point d’exécution en XAML, sélectionnez **vue XAML** dans le concepteur de workflow lorsque l’exécution du workflow est suspendue. Il est possible de revenir au mode de débogage dans le concepteur de workflow en rouvrant le workflow dans le concepteur à partir de l'Explorateur de solutions. Pour plus d'informations, voir [Procédure : Déboguez le code](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer)XAML avec l’Concepteur de flux de travail.  
  
## <a name="debugging-in-code"></a>Débogage dans le code  
 Des points d'arrêt de code peuvent être utilisés dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] de la même façon que dans d'autres applications impératives. Cliquez sur la marge de gauche du volet de code pour créer un point d’arrêt de code ou appuyez sur **F9** pour placer un point d’arrêt à l’emplacement du curseur.  
  
## <a name="attaching-to-a-workflow-process"></a>Attachement à un processus de workflow  
 Le débogage de workflow permet également d'utiliser l'infrastructure de Visual Studio pour attacher un processus. Cela permet à l'auteur de workflow de déboguer un workflow qui est exécuté dans un environnement hôte différent, tel qu'Internet Information Services 7.0 (IIS).  
  
## <a name="remote-debugging"></a>Remote Debugging  
 Les fonctions de débogage à distance Windows Workflow Foundation (WF) sont identiques au débogage à distance pour d’autres composants de Visual Studio. Pour plus d’informations sur l’utilisation du débogage [à distance, consultez Procédure: Activez le débogage](https://go.microsoft.com/fwlink/?LinkId=196257)distant.  
  
> [!NOTE]
> Si l’application de workflow cible l’architecture x86 et est hébergée sur un ordinateur exécutant un système d’exploitation 64 bits, le débogage à distance ne fonctionnera pas si Visual Studio n’est pas installé sur l’ordinateur distant ou si la cible de l’application de workflow est remplacée par **Any CPU**.  
  
## <a name="extending-the-workflow-debugging-service"></a>Extension du service de débogage de workflow  
 Le service de débogage de workflow est maintenant public et peut être utilisé pour créer des applications personnalisées, notamment pour la surveillance, la simulation et le débogage dans un concepteur réhébergé. Pour plus d'informations, voir la rubrique <xref:System.Activities.Presentation.Debug.DebuggerService>.
