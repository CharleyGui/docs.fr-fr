---
title: Prise en charge de nouvelles fonctionnalités Workflow Foundation 4.5 dans le concepteur de workflow réhébergé
ms.date: 03/30/2017
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
ms.openlocfilehash: 139215131afa38bc33539fa242a3584eb67d7941
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293947"
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Prise en charge de nouvelles fonctionnalités Workflow Foundation 4.5 dans le concepteur de workflow réhébergé

Windows Workflow Foundation (WF) dans .NET Framework 4,5 a introduit de nombreuses nouvelles fonctionnalités, y compris plusieurs améliorations apportées à l’expérience du concepteur de flux de travail. Cette rubrique détaille lesquelles de ces fonctionnalités sont prises en charge dans le concepteur réhébergé, et celles qui ne sont pas actuellement prises en charge.

> [!NOTE]
> Pour obtenir la liste de toutes les nouvelles fonctionnalités de Windows Workflow Foundation (WF) introduites dans .NET Framework 4,5, y compris celles qui ne sont pas liées au Réhébergement du concepteur, consultez [Nouveautés de Windows Workflow Foundation dans .NET Framework 4,5](whats-new-in-wf-in-dotnet.md).

## <a name="activities"></a>Activités

 La bibliothèque d'activités intégrée contient de nouvelles activités et de nouvelles fonctionnalités pour les activités existantes. Toutes ces nouvelles activités sont prises en charge dans le concepteur réhébergé. Pour plus d’informations sur ces nouvelles activités, consultez la section [activités](whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) des [Nouveautés de Windows Workflow Foundation dans .NET Framework 4,5](whats-new-in-wf-in-dotnet.md).

## <a name="c-expressions"></a>Expressions C#

 Avant .NET Framework 4,5, toutes les expressions dans les workflows pouvaient uniquement être écrites en Visual Basic. Dans .NET Framework 4,5, les expressions Visual Basic sont utilisées uniquement pour les projets créés à l’aide de Visual Basic. Les projets Visual C# utilisent C# pour les expressions. Lors de la création de flux de travail dans Visual Studio 2012, un éditeur d’expressions C# entièrement fonctionnel est fourni avec les fonctionnalités telles que la mise en surbrillance de la grammaire et IntelliSense. Les projets de workflow C# créés dans les versions antérieures qui utilisent des expressions Visual Basic continueront à fonctionner.

> [!WARNING]
> Les expressions C# ne sont pas prises en charge dans le concepteur réhébergé.

## <a name="new-designer-capabilities"></a>Nouvelles fonctions du concepteur

### <a name="designer-search"></a>Recherche du concepteur

 Les fonctionnalités [recherche rapide](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) et [Rechercher dans les fichiers](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) introduites avec .NET Framework 4,5 ne sont pas prises en charge dans le concepteur réhébergé. La recherche `Toolbox` est prise en charge dans le concepteur réhébergé. Pour plus d’informations sur ces fonctionnalités, consultez recherche dans le [Concepteur](whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).

> [!WARNING]
> La [recherche](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) et la recherche rapides [dans les fichiers](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) ne sont pas prises en charge dans le concepteur réhébergé.

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Supprimer l’élément de menu contextuel dans le concepteur de variable et d’argument

 Dans .NET Framework 4, les variables et les arguments ne pouvaient être supprimés que dans le concepteur à l’aide du clavier. À compter de .NET Framework 4,5, les variables et les arguments peuvent être supprimés à l’aide du menu contextuel. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.

 La capture d’écran suivante indique le menu contextuel du concepteur de variable et d’argument.

 ![Menu contextuel du concepteur de variable et d’argument](./media/wf-features-in-the-rehosted-workflow-designer/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a>Encadrement automatique avec séquence

 Étant donné qu'un workflow ou certaines activités de conteneur (telles que <xref:System.Activities.Statements.NoPersistScope>) peuvent uniquement contenir une seule activité de corps, l'ajout d'une deuxième activité exigeait que le développeur supprime la première activité, ajoute une activité <xref:System.Activities.Statements.Sequence>, puis ajoute les deux activités à l'activité de séquence. À compter de .NET Framework 4,5, lors de l’ajout d’une deuxième activité à l’aire du concepteur, une `Sequence` activité est automatiquement créée pour encapsuler les deux activités. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.

 La capture d'écran suivante affiche une activité `WriteLine` avec le `Body` d'un `NoPersistScope`.

 ![Activité WriteLine dans le corps d’une activité NoPersistScope.](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-write-line-activity.png)

 La capture d’écran suivante montre l’activité `Sequence` créée automatiquement dans le `Body` lorsqu’un second `WriteLine` est déposé sous le premier.

 ![Séquence créée automatiquement dans le corps d’un NoPersistScope.](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a>Mode Panoramique

 Pour naviguer plus facilement dans un grand workflow dans le concepteur, le mode panoramiques peut être activé, ce qui permet au développeur de cliquer sur la partie visible du workflow et de la faire glisser, plutôt que d'utiliser les barres de défilement. Le bouton pour activer le mode panoramiques se trouve dans le coin inférieur droit du concepteur. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.

 La capture d'écran suivante indique le bouton de panoramique qui se trouve dans le coin inférieur droit du concepteur de workflow.

 ![Bouton panoramique mis en surbrillance dans le concepteur de flux de travail.](./media/wf-features-in-the-rehosted-workflow-designer/pan-button-workflow-designer.png)

 Le bouton central de la souris ou la barre d'espace peut également être utilisé pour appliquer un panoramique au concepteur de workflow.

### <a name="multi-select"></a>Multisélection

 Plusieurs activités peuvent être sélectionnées en même temps, en faisant glisser un rectangle autour d'elles (lorsque le mode panoramique n'est pas activé), ou en maintenant la touche Ctrl enfoncée et en cliquant sur les activités souhaitées une à une. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.

 Il est également possible de glisser-déplacer plusieurs activités sélectionnées et de les utiliser dans une interaction à l'aide du menu contextuel.

### <a name="outline-view-of-workflow-items"></a>Mode Plan des éléments de workflow

 Afin de simplifier la navigation dans les workflows hiérarchiques, les composants d’un workflow s’affichent dans un mode Plan de style arborescent. Le mode plan est affiché dans la vue **structure du document** . Pour ouvrir cette vue dans Visual Studio, dans le menu supérieur, sélectionnez **Afficher**, **autres fenêtres**, **structure du document**, ou appuyez sur CTRL W, U. Cliquer sur un nœud en mode Plan permet d'accéder à l'activité correspondante dans le Concepteur de workflow, et le mode Plan est mis à jour pour afficher les activités qui sont sélectionnées dans le concepteur. Cette fonctionnalité est prise en charge dans le concepteur réhébergé.

 La capture d’écran suivante du flux de travail terminé à partir du [didacticiel prise en main](getting-started-tutorial.md) présente le mode plan avec un flux de travail séquentiel.

 ![Capture d’écran du mode plan avec un flux de travail séquentiel dans Visual Studio](./media/wf-features-in-the-rehosted-workflow-designer/outline-view-in-workflow-designer.jpg)

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Meilleur contrôle de la visibilité des éléments d'en-tête et de la barre de shell

 Dans un concepteur réhébergé, certains des contrôles d'interface utilisateur standard peuvent ne pas avoir de signification pour un workflow donné, et peuvent être désactivés. Dans .NET Framework 4, cette personnalisation est prise en charge uniquement par la barre de Shell en bas du concepteur. Dans .NET Framework 4,5, la visibilité des éléments d’en-tête de Shell en haut du concepteur peut être ajustée en définissant <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> avec la <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> valeur appropriée.

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Connexion automatique et insertion automatique dans les workflows Organigramme et Machine à états

 Dans .NET Framework 4, les connexions entre les nœuds d’un flux de travail d’organigramme devaient être ajoutées manuellement. Dans .NET Framework 4,5, les nœuds organigramme et machine à États ont des points de connexion automatique qui deviennent visibles quand une activité est glissée de la boîte à outils vers l’aire du concepteur. Le dépôt d’une activité sur un de ces points ajoute automatiquement l’activité avec la connexion nécessaire.

 La capture d'écran suivante montre les points d'attachement qui sont visibles lorsqu'une activité est déplacée depuis la boîte à outils.

 ![Nœud de démarrage de l’organigramme présentant les points de connexion automatique](./media/wf-features-in-the-rehosted-workflow-designer/auto-connect-points-start-node.png)

 Les activités peuvent également être déplacées sur les connexions entre des nœuds d'organigramme et des états de façon à insérer automatiquement le nœud entre deux autres nœuds. La capture d’écran suivante montre la ligne de connexion en surbrillance où les activités peuvent être glissées-déposées depuis la boîte à outils.

 ![Poignée d'insertion automatique pour déposer les activités](./media/wf-features-in-the-rehosted-workflow-designer/auto-insert-connecting-line.png)

 Connexion automatique et insertion automatique sont prises en charge dans le concepteur réhébergé.

### <a name="designer-annotations"></a>Annotations du concepteur

 Pour faciliter le développement de plus grands workflows, le concepteur prend désormais en charge l'ajout d'annotations pour faciliter le suivi du processus de création. Une annotation peut être ajoutée aux activités, états, nœuds d’organigramme, variables et arguments. La capture d'écran suivante montre le menu contextuel utilisé pour ajouter des annotations au concepteur.

 ![Capture d’écran montrant le menu permettant d’ajouter des notations.](./media/wf-features-in-the-rehosted-workflow-designer/designer-annotations-context-menu.png)

 Les annotations du concepteur sont prises en charge dans le concepteur réhébergé.

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Définir et consommer des objets ActivityDelegate dans le concepteur

 Les activités dans .NET Framework 4 <xref:System.Activities.ActivityDelegate> ont utilisé des objets pour exposer des points d’exécution dans lesquels d’autres parties du flux de travail pouvaient interagir avec l’exécution d’un workflow, mais l’utilisation de ces points d’exécution nécessitait généralement une quantité de code équitable. Dans cette version finale, les développeurs peuvent définir et utiliser des délégués d'activité à l'aide du concepteur de workflow. Pour plus d’informations, consultez [Comment : définir et consommer des délégués d’activité dans le concepteur de flux de travail](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

 Les délégués d'activité sont pris en charge dans le concepteur réhébergé.

### <a name="build-time-validation"></a>Validation au moment de la génération

 Dans .NET Framework 4, les erreurs de validation de workflow n’étaient pas comptabilisées comme des erreurs de build pendant la génération d’un projet de Workflow. Cela signifiait que la génération d’un projet de workflow pouvait réussir même lorsqu’il existait des erreurs de validation de workflow. Dans .NET Framework 4,5, les erreurs de validation de workflow provoquent l’échec de la génération.

> [!WARNING]
> La validation au moment de la génération n’est pas prise en charge dans le concepteur réhébergé.

### <a name="design-time-background-validation"></a>Validation d'arrière-plan au moment du design

 Dans .NET Framework 4, les flux de travail étaient validés en tant que processus de premier plan, ce qui pourrait potentiellement bloquer l’interface utilisateur pendant les processus de validation complexes ou longs. La validation de workflow a lieu à présent sur un thread d'arrière-plan, afin que l'interface utilisateur ne soit pas bloquée.

 La validation de l'arrière-plan au moment de la génération est prise en charge dans le concepteur réhébergé.

### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>État d'affichage dans un emplacement distinct des fichiers XAML

 Dans .NET Framework 4, les informations d’état d’affichage d’un workflow sont stockées dans le fichier XAML à de nombreux emplacements différents. Cela n'est pas pratique pour les développeurs qui souhaitent lire le XAML directement, ou écrire du code pour supprimer les informations d'état d'affichage. Dans .NET Framework 4,5, les informations d’état d’affichage dans le fichier XAML sont sérialisées en tant qu’élément distinct dans le fichier XAML.  Les développeurs peuvent facilement localiser et modifier les informations d’état d’affichage d’une activité, ou supprimer complètement l’état d’affichage.

 Cette fonctionnalité est prise en charge dans le concepteur de workflow réhébergé.

### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>Opter pour les fonctionnalités de workflow 4.5 dans le concepteur réhébergé

 Pour préserver la compatibilité descendante, certaines nouvelles fonctionnalités incluses dans .NET Framework 4,5 ne sont pas activées par défaut dans le concepteur réhébergé. Il s'agit de garantir que les applications existantes qui utilisent le concepteur réhébergé ne sont pas interrompues par la mise à jour vers la version la plus récente. Pour activer les nouvelles fonctionnalités du concepteur réhébergé, affectez à <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> la valeur « .Net Framework 4.5 », ou définissez des membres de <xref:System.Activities.Presentation.DesignerConfigurationService> pour activer des fonctionnalités.

## <a name="new-workflow-development-models"></a>Nouveaux modèles de développement de workflow

 Outre les modèles de développement d’organigramme et workflow séquentiel, cette mise en production inclut des workflows Machine à états, et les services de workflow Contrat en premier.

### <a name="state-machine-workflows"></a>Workflows de machine à états

 Les workflows de machine à États ont été introduits dans le cadre de la .NET Framework 4.0.1 dans la [mise à jour 1 de la plateforme Microsoft .NET Framework 4](/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1). Cette mise à jour inclut plusieurs nouvelles classes et activités qui permettent aux développeurs de créer des workflow de machine à états. Ces classes et activités ont été mises à jour pour .NET Framework 4,5. Les mises à jour comprennent :

1. Possibilité de définir des points d'arrêt sur des états

2. Possibilité de copier et coller des transitions dans le concepteur de workflow

3. Prise en charge du concepteur pour la création de transition de déclencheur partagée

4. Les activités utilisées pour créer des workflows Machine à états, notamment : <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State> et <xref:System.Activities.Statements.Transition>

 La capture d’écran suivante montre le flux de travail de l’ordinateur d’état terminé à partir de l’étape [prise en main didacticiel](getting-started-tutorial.md) [procédure : créer un workflow d’ordinateur d’État](how-to-create-a-state-machine-workflow.md).

 ![Illustration qui montre le flux de travail de l’ordinateur d’état terminé.](./media/wf-features-in-the-rehosted-workflow-designer/complete-state-machine-workflow.jpg)

 Pour plus d’informations sur la création de workflows de machine à États, consultez [workflows de machine à États](state-machine-workflows.md). Les workflow de machine à états sont pris en charge dans le concepteur réhébergé.

### <a name="contract-first-workflow-development"></a>Développement de workflow « contrat en premier »

 L’outil de développement de workflow contrat en premier permet au développeur de concevoir un contrat dans le code en premier, puis, en quelques clics dans Visual Studio, de générer automatiquement un modèle d’activité dans la boîte à outils représentant chaque opération. Ces activités sont ensuite utilisées pour créer un workflow qui implémente les opérations définies par le contrat. Le concepteur de workflow validera le service de workflow pour garantir que ces opérations sont implémentées et que la signature du workflow correspond à la signature du contrat. Le développeur peut également associer un service de workflow à une collection de contrats implémentés. Pour plus d’informations sur le développement d’un service de workflow contrat en premier, consultez Guide pratique [pour créer un service de workflow qui utilise un contrat de service existant](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).

> [!WARNING]
> Le développement de workflow « contrat en premier » n'est pas pris en charge dans Workflow Designer.
