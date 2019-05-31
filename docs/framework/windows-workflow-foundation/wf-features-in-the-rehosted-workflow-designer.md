---
title: Prise en charge de nouvelles fonctionnalités Workflow Foundation 4.5 dans le concepteur de workflow réhébergé
ms.date: 03/30/2017
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
ms.openlocfilehash: 70e4a8580a8b383bdd4e5e5299bcc5210f3210dc
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423964"
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Prise en charge de nouvelles fonctionnalités Workflow Foundation 4.5 dans le concepteur de workflow réhébergé
Windows Workflow Foundation (WF) dans .NET Framework 4.5 a introduit de nombreuses nouvelles fonctionnalités, notamment plusieurs améliorations à l’expérience de Concepteur de flux de travail. Cette rubrique détaille lesquelles de ces fonctionnalités sont prises en charge dans le concepteur réhébergé, et celles qui ne sont pas actuellement prises en charge.

> [!NOTE]
>  Pour obtenir la liste de toutes les nouvelles fonctionnalités de Windows Workflow Foundation (WF) introduites dans .NET Framework 4.5, y compris ceux qui ne sont pas liées au réhébergement du concepteur, consultez [What ' s New in Windows Workflow Foundation dans .NET 4.5](whats-new-in-wf-in-dotnet.md).

## <a name="activities"></a>Activités
 La bibliothèque d'activités intégrée contient de nouvelles activités et de nouvelles fonctionnalités pour les activités existantes. Toutes ces nouvelles activités sont prises en charge dans le concepteur réhébergé. Pour plus d’informations sur ces nouvelles activités, consultez le [activités](whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) section de [What ' s New in Windows Workflow Foundation dans .NET 4.5](whats-new-in-wf-in-dotnet.md).

## <a name="c-expressions"></a>Expressions C#
 Avant le .NET Framework 4.5, toutes les expressions dans les workflows ne pouvaient être écrites en Visual Basic. Dans .NET Framework 4.5, les expressions Visual Basic sont uniquement utilisées pour les projets créés à l’aide de Visual Basic. Les projets Visual C# utilisent C# pour les expressions. Lors de la création de workflows dans Visual Studio 2012, un éditeur d’expressions c# fonctionnel est fourni qui a des fonctions telles que la mise en surbrillance de syntaxe et intellisense. Les projets de workflow C# créés dans les versions antérieures qui utilisent des expressions Visual Basic continueront à fonctionner.

> [!WARNING]
>  Les expressions C# ne sont pas prises en charge dans le concepteur réhébergé.

## <a name="new-designer-capabilities"></a>Nouvelles fonctions du concepteur

### <a name="designer-search"></a>Recherche du concepteur
 Le [recherche rapide](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) et [rechercher dans les fichiers](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) fonctionnalités introduites dans .NET Framework 4.5 ne sont pas pris en charge dans le concepteur réhébergé. La recherche `Toolbox` est prise en charge dans le concepteur réhébergé. Pour plus d’informations sur ces fonctionnalités, consultez [recherche du concepteur](whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).

> [!WARNING]
>  [Recherche rapide](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) et [rechercher dans les fichiers](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) ne sont pas pris en charge dans le concepteur réhébergé.

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Supprimer l’élément de menu contextuel dans le concepteur de variable et d’argument
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les variables et les arguments ne pouvaient être supprimés dans le concepteur qu'en utilisant le clavier. À compter de .NET Framework 4.5, variables et arguments peuvent être supprimés à l’aide du menu contextuel. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.

 La capture d’écran suivante indique le menu contextuel du concepteur de variable et d’argument.

 ![Menu contextuel du concepteur de variable et d’argument](./media/wf-features-in-the-rehosted-workflow-designer/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a>Encadrement automatique avec séquence
 Étant donné qu'un workflow ou certaines activités de conteneur (telles que <xref:System.Activities.Statements.NoPersistScope>) peuvent uniquement contenir une seule activité de corps, l'ajout d'une deuxième activité exigeait que le développeur supprime la première activité, ajoute une activité <xref:System.Activities.Statements.Sequence>, puis ajoute les deux activités à l'activité de séquence. Depuis .NET Framework 4.5, lorsque vous ajoutez une deuxième activité à l’aire du concepteur, un `Sequence` activité sera automatiquement créée pour encapsuler les deux activités. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.

 La capture d'écran suivante affiche une activité `WriteLine` avec le `Body` d'un `NoPersistScope`.

 ![Une activité WriteLine dans le corps d’une activité NoPersistScope.](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-write-line-activity.png)

 La capture d’écran suivante montre l’activité `Sequence` créée automatiquement dans le `Body` lorsqu’un second `WriteLine` est déposé sous le premier.

 ![Une séquence créée automatiquement dans le corps d’un NoPersistScope.](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a>Mode Panoramique
 Pour naviguer plus facilement dans un grand workflow dans le concepteur, le mode panoramiques peut être activé, ce qui permet au développeur de cliquer sur la partie visible du workflow et de la faire glisser, plutôt que d'utiliser les barres de défilement. Le bouton pour activer le mode panoramiques se trouve dans le coin inférieur droit du concepteur. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.

 La capture d'écran suivante indique le bouton de panoramique qui se trouve dans le coin inférieur droit du concepteur de workflow.

 ![Le bouton de panoramique mis en surbrillance dans le Concepteur de flux de travail.](./media/wf-features-in-the-rehosted-workflow-designer/pan-button-workflow-designer.png)

 Le bouton central de la souris ou la barre d'espace peut également être utilisé pour appliquer un panoramique au concepteur de workflow.

### <a name="multi-select"></a>Multisélection
 Plusieurs activités peuvent être sélectionnées en même temps, en faisant glisser un rectangle autour d'elles (lorsque le mode panoramique n'est pas activé), ou en maintenant la touche Ctrl enfoncée et en cliquant sur les activités souhaitées une à une. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.

 Il est également possible de glisser-déplacer plusieurs activités sélectionnées et de les utiliser dans une interaction à l'aide du menu contextuel.

### <a name="outline-view-of-workflow-items"></a>Mode Plan des éléments de workflow
 Afin de simplifier la navigation dans les workflows hiérarchiques, les composants d’un workflow s’affichent dans un mode Plan de style arborescent. Le mode plan est affiché dans le **structure du Document** vue. Pour ouvrir cette vue dans Visual Studio, dans le menu supérieur, sélectionnez **vue**, **Windows autres**, **structure du Document**, ou appuyez sur Ctrl W, U. Cliquer sur un nœud en mode Plan permet d'accéder à l'activité correspondante dans le Concepteur de workflow, et le mode Plan est mis à jour pour afficher les activités qui sont sélectionnées dans le concepteur. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.

 La capture d’écran suivante du workflow terminé à partir de la [Getting Started Tutorial](getting-started-tutorial.md) montre le mode plan avec un workflow séquentiel.

 ![Capture d’écran du mode plan avec un workflow séquentiel dans Visual Studio](./media/wf-features-in-the-rehosted-workflow-designer/outline-view-in-workflow-designer.jpg)

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Meilleur contrôle de la visibilité des éléments d'en-tête et de la barre de shell
 Dans un concepteur réhébergé, certains des contrôles d'interface utilisateur standard peuvent ne pas avoir de signification pour un workflow donné, et peuvent être désactivés. Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], cette personnalisation est prise en charge uniquement par la barre de shell en bas du concepteur. Dans .NET Framework 4.5, la visibilité des éléments d’en-tête de shell en haut du concepteur peut être ajustée en définissant <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> avec le bon <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> valeur.

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Connexion automatique et insertion automatique dans les workflows Organigramme et Machine à états
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les connexions entre les nœuds d'un workflow Organigramme devaient être ajoutées manuellement. Dans .NET Framework 4.5, les nœuds organigramme et Machine à états ont points qui sont visibles lorsqu’une activité est déplacée à partir de la boîte à outils vers l’aire du Concepteur de connexion automatique. Le dépôt d'une activité sur un de ces points ajoute automatiquement l'activité avec la connexion nécessaire.

 La capture d'écran suivante montre les points d'attachement qui sont visibles lorsqu'une activité est déplacée depuis la boîte à outils.

 ![Organigramme illustrant de nœud de démarrage points de connexion automatique](./media/wf-features-in-the-rehosted-workflow-designer/auto-connect-points-start-node.png)

 Les activités peuvent également être déplacées sur les connexions entre des nœuds d'organigramme et des états de façon à insérer automatiquement le nœud entre deux autres nœuds. La capture d’écran suivante montre la ligne de connexion en surbrillance où les activités peuvent être glissées-déposées depuis la boîte à outils.

 ![Poignée d’insertion automatique pour déposer les activités](./media/wf-features-in-the-rehosted-workflow-designer/auto-insert-connecting-line.png)

 Connexion automatique et insertion automatique sont prises en charge dans le concepteur réhébergé.

### <a name="designer-annotations"></a>Annotations du concepteur
 Pour faciliter le développement de plus grands workflows, le concepteur prend désormais en charge l'ajout d'annotations pour faciliter le suivi du processus de création. Une annotation peut être ajoutée aux activités, états, nœuds d'organigramme, variables et arguments. La capture d'écran suivante montre le menu contextuel utilisé pour ajouter des annotations au concepteur.

 ![Capture d’écran qui affiche le menu pour ajouter des notations.](./media/wf-features-in-the-rehosted-workflow-designer/designer-annotations-context-menu.png)

 Les annotations du concepteur sont prises en charge dans le concepteur réhébergé.

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Définir et consommer des objets ActivityDelegate dans le concepteur
 Les activités dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] utilisaient des objets <xref:System.Activities.ActivityDelegate> pour exposer des points d'exécution où d'autres parties du workflow peuvent interagir avec l'exécution d'un workflow, mais l'utilisation de ces points d'exécution nécessite généralement du code. Dans cette version finale, les développeurs peuvent définir et utiliser des délégués d'activité à l'aide du concepteur de workflow. Pour plus d'informations, voir [Procédure : Définir et utiliser des délégués d’activité dans le Concepteur de flux de travail](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

 Les délégués d'activité sont pris en charge dans le concepteur réhébergé.

### <a name="build-time-validation"></a>Validation au moment de la génération
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les erreurs de validation de workflow n'étaient pas été comptées comme des erreurs de build pendant la génération d'un projet de workflow. Cela signifiait que la génération d'un projet de workflow pouvait réussir même lorsqu'il existait des erreurs de validation de workflow. Dans .NET Framework 4.5, les erreurs de validation de flux de travail provoquent l’échec de la build.

> [!WARNING]
>  La validation au moment de la génération n'est pas prise en charge dans le concepteur réhébergé.  
  
### <a name="design-time-background-validation"></a>Validation d'arrière-plan au moment du design  
 Dans [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], flux de travail ont été validés en tant qu’un processus de premier plan, ce qui peut potentiellement se bloquer l’interface utilisateur pendant le processus de validation complexes ou longs. La validation de workflow a lieu à présent sur un thread d'arrière-plan, afin que l'interface utilisateur ne soit pas bloquée.  
  
 La validation de l'arrière-plan au moment de la génération est prise en charge dans le concepteur réhébergé.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>État d'affichage dans un emplacement distinct des fichiers XAML  
 Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], les informations d'état d'affichage pour un workflow sont stockées dans le fichier XAML en différents emplacements. Cela n'est pas pratique pour les développeurs qui souhaitent lire le XAML directement, ou écrire du code pour supprimer les informations d'état d'affichage. Dans .NET Framework 4.5, les informations d’état de vue dans le fichier XAML sont sérialisées comme un élément distinct dans le fichier XAML.  Les développeurs peuvent facilement localiser et modifier les informations d’état de vue d’une activité ou supprimer complètement de l’état d’affichage.  
  
 Cette fonctionnalité est prise en charge dans le concepteur de workflow réhébergé.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>Opter pour les fonctionnalités de workflow 4.5 dans le concepteur réhébergé  
 Pour préserver la compatibilité descendante, certaines nouvelles fonctionnalités incluses dans .NET Framework 4.5 ne sont pas activées par défaut dans le concepteur réhébergé. Il s'agit de garantir que les applications existantes qui utilisent le concepteur réhébergé ne sont pas interrompues par la mise à jour vers la version la plus récente. Pour activer les nouvelles fonctionnalités du concepteur réhébergé, affectez à <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> la valeur « .Net Framework 4.5 », ou définissez des membres de <xref:System.Activities.Presentation.DesignerConfigurationService> pour activer des fonctionnalités.  
  
## <a name="new-workflow-development-models"></a>Nouveaux modèles de développement de workflow  
 Outre les modèles de développement d'organigramme et workflow séquentiel, cette version inclut des workflows Machine à états, et les services de workflow Contrat en premier.  
  
### <a name="state-machine-workflows"></a>Workflows de machine à états  
 Workflows de machine à états ont été introduits dans le cadre du .NET Framework 4.0.1 dans le [Microsoft .NET Framework 4 Platform Update 1](https://go.microsoft.com/fwlink/?LinkID=215092). Cette mise à jour inclut plusieurs nouvelles classes et activités qui permettent aux développeurs de créer des workflow de machine à états. Ces classes et activités ont été mis à jour pour .NET Framework 4.5. Les mises à jour comprennent :  
  
1. Possibilité de définir des points d'arrêt sur des états  
  
2. Possibilité de copier et coller des transitions dans le concepteur de workflow  
  
3. Prise en charge du concepteur pour la création de transition de déclencheur partagée  
  
4. Les activités utilisées pour créer des workflows Machine à états, notamment : <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State> et <xref:System.Activities.Statements.Transition>  
  
 La capture d’écran suivante montre le workflow de machine d’état terminé du [Getting Started Tutorial](getting-started-tutorial.md) étape [Comment : Créer un Workflow de Machine à états](how-to-create-a-state-machine-workflow.md).  
  
 ![Illustration qui montre le workflow d’ordinateur d’état terminé.](./media/wf-features-in-the-rehosted-workflow-designer/complete-state-machine-workflow.jpg)  
  
 Pour plus d’informations sur la création de workflows machine à états, consultez [Workflows Machine à états](state-machine-workflows.md). Les workflow de machine à états sont pris en charge dans le concepteur réhébergé.  
  
### <a name="contract-first-workflow-development"></a>Développement de workflow « contrat en premier »  
 L’outil de développement de workflow contrat en premier permet au développeur de concevoir un contrat dans le code tout d’abord, puis, en quelques clics dans Visual Studio, générez automatiquement un modèle d’activité dans la boîte à outils représentant chaque opération. Ces activités sont ensuite utilisées pour créer un workflow qui implémente les opérations définies par le contrat. Le concepteur de workflow validera le service de workflow pour garantir que ces opérations sont implémentées et que la signature du workflow correspond à la signature du contrat. Le développeur peut également associer un service de workflow à une collection de contrats implémentés. Pour plus d’informations sur le développement de service de workflow contrat en premier, consultez [Comment : Créer un service de flux de travail qui utilise un contrat de service existant](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
> [!WARNING]
>  Le développement de workflow « contrat en premier » n'est pas pris en charge dans Workflow Designer.
