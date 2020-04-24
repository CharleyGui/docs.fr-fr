---
title: Vue d'ensemble du modèle d'application Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: aa47304cf2bded93bdb95ffe7dfa35bb37d9a643
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976460"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Vue d'ensemble du modèle d'application Visual Basic

Visual Basic fournit un modèle bien défini pour contrôler le comportement des applications Windows Forms : le modèle d’application Visual Basic. Ce modèle comprend des événements pour la gestion du démarrage et de l’arrêt de l’application, ainsi que des événements pour intercepter les exceptions non gérées. Il prend également en charge le développement d’applications à instance unique. Le modèle d’application est extensible, de sorte que les développeurs qui ont besoin de davantage de contrôle peuvent personnaliser ses méthodes substituables.  
  
## <a name="uses-for-the-application-model"></a>Utilisations du modèle d’application  

 Une application classique doit effectuer des tâches au démarrage et à l’arrêt. Par exemple, lorsqu’il démarre, l’application peut afficher un écran de démarrage, créer des connexions de base de données, charger un état enregistré, et ainsi de suite. Lorsque l’application s’arrête, elle peut fermer les connexions à la base de données, enregistrer l’état actuel, et ainsi de suite. En outre, l’application peut exécuter du code spécifique lorsque l’application s’arrête de manière inattendue, par exemple pendant une exception non gérée.  
  
 Le modèle d’application Visual Basic permet de créer facilement une application à *instance unique* . Une application à instance unique diffère d’une application normale dans la mesure où une seule instance de l’application peut être exécutée à la fois. Une tentative de lancement d’une autre instance d’une application à instance unique entraîne la notification de l’instance d’origine, au `StartupNextInstance` moyen de l’événement, qu’une autre tentative de lancement a été effectuée. La notification comprend les arguments de ligne de commande de l’instance suivante. L’instance suivante de l’application est ensuite fermée avant qu’une initialisation puisse se produire.  
  
 Une application à instance unique démarre et vérifie s’il s’agit de la première instance ou d’une instance suivante de l’application :  
  
- S’il s’agit de la première instance, elle démarre comme d’habitude.  
  
- Chaque nouvelle tentative de démarrage de l’application, pendant l’exécution de la première instance, produit un comportement très différent. La tentative suivante notifie la première instance des arguments de ligne de commande, puis se ferme immédiatement. La première instance de gère `StartupNextInstance` l’événement pour déterminer les arguments de ligne de commande de l’instance suivante, et continue à s’exécuter.  
  
     Ce diagramme montre comment une instance suivante signale la première instance :  
  
     ![Diagramme illustrant une image d’application d’instance unique.](./media/overview-of-the-visual-basic-application-model/single-instance-application.gif)  
  
 En gérant l' `StartupNextInstance` événement, vous pouvez contrôler le comportement de votre application à instance unique. Par exemple, Microsoft Outlook s’exécute généralement comme une application à instance unique ; Quand Outlook est en cours d’exécution et que vous tentez de redémarrer Outlook, le focus se déplace vers l’instance d’origine, mais une autre instance ne s’ouvre pas.  
  
## <a name="events-in-the-application-model"></a>Événements dans le modèle d’application  

 Les événements suivants se trouvent dans le modèle d’application :  
  
- **Démarrage**de l’application. L’application déclenche l' <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> événement lorsqu’elle démarre. En gérant cet événement, vous pouvez ajouter du code qui initialise l’application avant le chargement du formulaire principal. L' `Startup` événement permet également d’annuler l’exécution de l’application au cours de cette phase du processus de démarrage, si vous le souhaitez.  
  
     Vous pouvez configurer l’application pour qu’elle affiche un écran de démarrage pendant l’exécution du code de démarrage de l’application. Par défaut, le modèle d’application supprime l’écran de démarrage lorsque l' `/nosplash` argument `-nosplash` de ligne de commande ou est utilisé.  
  
- **Applications à instance unique**. L' <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> événement est déclenché lorsqu’une instance suivante d’une application à instance unique démarre. L’événement passe les arguments de ligne de commande de l’instance suivante.  
  
- **Exceptions non gérées**. Si l’application rencontre une exception non gérée, elle déclenche l' <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> événement. Votre gestionnaire pour cet événement peut examiner l’exception et déterminer s’il faut continuer l’exécution.  
  
     L' `UnhandledException` événement n’est pas déclenché dans certaines circonstances. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
- **Modifications de la connectivité réseau**. Si la disponibilité du réseau de l’ordinateur change, l’application <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> déclenche l’événement.  
  
     L' `NetworkAvailabilityChanged` événement n’est pas déclenché dans certaines circonstances. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
- **Arrêt**de l’application. L’application fournit l' <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> événement pour signaler le moment où elle est sur le paragraphe d’être arrêtée. Dans ce gestionnaire d’événements, vous pouvez vous assurer que les opérations que votre application doit effectuer (fermeture et enregistrement, par exemple) sont terminées. Vous pouvez configurer votre application pour qu’elle s’arrête lorsque le formulaire principal se ferme ou s’arrête uniquement lorsque toutes les formes se ferment.  
  
## <a name="availability"></a>Disponibilité  

 Par défaut, le modèle d’application Visual Basic est disponible pour les projets Windows Forms. Si vous configurez l’application pour utiliser un autre objet de démarrage ou si vous démarrez le code `Sub Main`d’application avec un personnalisé, cet objet ou cette classe devra peut- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> être fournir une implémentation de la classe pour utiliser le modèle d’application. Pour plus d’informations sur la modification de l’objet de démarrage, consultez [page application, concepteur de projets (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Extension du modèle d’application Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
