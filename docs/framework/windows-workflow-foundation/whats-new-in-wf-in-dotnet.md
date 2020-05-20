---
title: Nouveautés de Windows Workflow Foundation dans .NET 4.5
description: Windows Workflow Foundation dans .NET Framework 4,5 introduit de nombreuses nouvelles fonctionnalités, telles que les nouvelles activités, les fonctionnalités de concepteur et les modèles de développement de Workflow.
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: 85555e48929885b6eef7fde6ac0c9017fa403d4d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419458"
---
# <a name="whats-new-in-windows-workflow-foundation-in-net-45"></a>Nouveautés de Windows Workflow Foundation dans .NET 4.5

Windows Workflow Foundation (WF) dans .NET Framework 4,5 introduit de nombreuses nouvelles fonctionnalités, telles que les nouvelles activités, les fonctionnalités de concepteur et les modèles de développement de flux de travail. La plupart des nouvelles fonctionnalités de workflow introduites dans .NET Framework 4,5 sont prises en charge dans le concepteur de flux de travail réhébergé. Pour plus d’informations sur les nouvelles fonctionnalités prises en charge, consultez [prise en charge des nouvelles fonctionnalités de Workflow Foundation 4,5 dans le concepteur de flux de travail réhébergé](wf-features-in-the-rehosted-workflow-designer.md). Pour plus d’informations sur la migration des applications de flux de travail .NET 3,0 et .NET 3,5 afin d’utiliser la dernière version, consultez [Guide de migration](migration-guidance.md). Cette rubrique fournit une vue d’ensemble des nouvelles fonctionnalités de workflow introduites dans .NET Framework 4,5.

> [!WARNING]
> Les nouvelles fonctionnalités de Windows Workflow Foundation introduites dans .NET Framework 4,5 ne sont pas disponibles pour les projets qui ciblent des versions antérieures du Framework. Si un projet qui cible .NET Framework 4,5 est reciblé vers une version antérieure du Framework, plusieurs problèmes peuvent se produire.
>
> - Les expressions C# seront remplacées dans le concepteur avec la **valeur de message définie en XAML**.
> - De nombreuses erreurs de build se produisent, y compris l'erreur suivante.
>
> **Le format de fichier n’est pas compatible avec le Framework de ciblage actuel. Pour convertir le format de fichier, enregistrez le fichier explicitement. Ce message d’erreur s’affiche une fois que vous avez enregistré le fichier et rouvert le concepteur.**

## <a name="workflow-versioning"></a><a name="BKMK_Versioning"></a>Contrôle de version de workflow

.NET Framework 4,5 a introduit plusieurs nouvelles fonctionnalités de contrôle de version basées sur la nouvelle <xref:System.Activities.WorkflowIdentity> classe. <xref:System.Activities.WorkflowIdentity> fournit aux auteurs d'applications de workflow un mécanisme pour mapper une instance de workflow persistante avec sa définition.

- Les développeurs qui utilisent l'hébergement <xref:System.Activities.WorkflowApplication> peuvent utiliser <xref:System.Activities.WorkflowIdentity> pour permettre l'hébergement de plusieurs versions d'un workflow côte à côte. Les instances de workflow persistantes peuvent être chargées à l'aide de la nouvelle classe <xref:System.Activities.WorkflowApplicationInstance>, puis <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> peut être utilisé par l'hôte pour fournir la version appropriée de la définition de workflow en instanciant <xref:System.Activities.WorkflowApplication>. Pour plus d’informations, consultez [utilisation de WorkflowIdentity et de versioning](using-workflowidentity-and-versioning.md) et [Comment : héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

- <xref:System.ServiceModel.WorkflowServiceHost> est maintenant un hôte multi-version. Lorsqu'une nouvelle version d'un service de workflow est déployée, les nouvelles instances sont créées à l'aide du nouveau service, mais les instances existantes s'exécutent à l'aide de la version antérieure. Pour plus d’informations, consultez contrôle de [version côte à côte dans WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).

- Cette rubrique présente la mise à jour dynamique qui fournit un mécanisme pour mettre à jour la définition d'une instance persistante de workflow. Pour plus d’informations, consultez [mise à jour dynamique](dynamic-update.md) et [Comment : mettre à jour la définition d’une instance de workflow en cours d’exécution](how-to-update-the-definition-of-a-running-workflow-instance.md).

- Un script de base de données SqlWorkflowInstanceStoreSchemaUpgrade. SQL est fourni pour mettre à niveau les bases de données de persistance créées à l’aide des scripts de base de données .NET Framework 4. Ce script met à jour les bases de données de persistance .NET Framework 4 pour prendre en charge les nouvelles fonctionnalités de contrôle de version introduites dans .NET Framework 4,5. Des valeurs de versioning par défaut sont attribuées à toutes les instances persistantes de workflow dans la base de données et ces instances peuvent ensuite participer côte à côte à l'exécution et à la mise à jour dynamique. Pour plus d’informations, consultez [mise à niveau de bases de données de persistance .NET Framework 4 pour prendre en charge le contrôle de version de workflow](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

## <a name="activities"></a><a name="BKMK_NewActivities"></a>ACTIVITE

La bibliothèque d'activités intégrée contient de nouvelles activités et de nouvelles fonctionnalités pour les activités existantes.

### <a name="nopersist-scope"></a><a name="BKMK_NoPersistScope"></a>Étendue NoPersist

<xref:System.Activities.Statements.NoPersistScope> est une nouvelle activité de conteneur qui empêche la persistance d'un workflow lorsque des activités enfants de NoPersistScope sont en cours d'exécution. Cela s'avère utile dans les scénarios où il n'est pas nécessaire que le workflow soit rendu persistant, par exemple lorsque le workflow utilise des ressources propres à l'ordinateur telles que les handles de fichiers, ou pendant les transactions de bases de données. Auparavant, pour empêcher la persistance de se produire pendant l'exécution d'une activité, un <xref:System.Activities.NativeActivity> personnalisé utilisant un utilisait<xref:System.Activities.NoPersistHandle> était nécessaire.

### <a name="new-flowchart-capabilities"></a><a name="BKMK_NewFlowchartCapabilities"></a>Nouvelles fonctionnalités d’organigramme

Les organigrammes sont mis à jour pour .NET Framework 4,5 et présentent les nouvelles fonctionnalités suivantes :

- La propriété `DisplayName` d'une activité <xref:System.Activities.Statements.FlowSwitch%601> ou <xref:System.Activities.Statements.FlowDecision> est modifiable. Cela laisse le concepteur d'activités afficher davantage d'informations sur l'objectif de l'activité.

- Les organigrammes ont une nouvelle propriété appelée <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A> ; la valeur par défaut de cette propriété est `False`. Si cette propriété a la valeur `True`, les nœuds déconnectés d’organigramme génèreront des erreurs de validation.

## <a name="support-for-partial-trust"></a>Prise en charge de la confiance partielle

Les flux de travail dans .NET Framework 4 nécessitaient un domaine d’application entièrement fiable. Dans .NET Framework 4,5, les flux de travail peuvent fonctionner dans un environnement de confiance partielle. Dans un environnement de confiance partielle, des composants tiers peuvent être utilisés sans leur octroyer un accès total aux ressources de l'hôte. Les problèmes liés à l'exécution des workflows dans un environnement de confiance partielle sont les suivants :

1. L'utilisation de composants hérités (comprenant des règles) contenus dans l'activité <xref:System.Activities.Statements.Interop> n'est pas prise en charge dans un environnement de confiance partielle.

2. L'exécution de workflows dans un environnement de confiance partielle dans <xref:System.ServiceModel.WorkflowServiceHost> n'est pas prise en charge.

3. Les exceptions de persistance dans un scénario de confiance partielle sont une menace potentielle à la sécurité. Pour désactiver la persistance des exceptions, une extension de type <xref:System.Activities.ExceptionPersistenceExtension> doit être ajoutée au projet pour supprimer les exceptions persistantes. L'exemple de code suivant illustre l'implémentation de ce type.

    ```csharp
    public class ExceptionPersistenceExtension
    {
        public ExceptionPersistenceExtension()
        {
            this.PersistExceptions = false;
        }
        public bool PersistExceptions { get; set; }
    }
    ```

     Si les exceptions ne doivent pas être sérialisées, assurez-vous qu'elles sont utilisées dans un <xref:System.Activities.Statements.NoPersistScope>.

4. Les auteurs d'activités doivent substituer <xref:System.Activities.Activity.CacheMetadata%2A> pour éviter que le runtime du workflow exécute automatiquement la réflexion sur le type. Les arguments et les activités enfants doivent être non-null, et <xref:System.Activities.ActivityMetadata.Bind%2A> doit être appelé explicitement. Pour plus d’informations sur la substitution <xref:System.Activities.Activity.CacheMetadata%2A> , consultez [exposition de données avec CacheMetadata](exposing-data-with-cachemetadata.md). En outre, les instances d’arguments qui sont d’un type `internal` ou **privé** doivent être créées explicitement dans <xref:System.Activities.Activity.CacheMetadata%2A> pour éviter d’être créées par réflexion.

5. Les types n'utilisent pas <xref:System.Runtime.Serialization.ISerializable> ou <xref:System.SerializableAttribute> pour la sérialisation ; les types qui doivent être sérialisés doivent prendre en charge <xref:System.Runtime.Serialization.DataContractSerializer>.

6. Les expressions qui utilisent <xref:System.Activities.Expressions.LambdaValue%601> nécessitent <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A> et, par conséquent, ne fonctionnent pas dans un scénario de confiance partielle. Les workflows qui utilisent <xref:System.Activities.Expressions.LambdaValue%601> doivent remplacer les expressions qui ont des activités qui dérivent de <xref:System.Activities.CodeActivity%601>. .

7. Les expressions ne peuvent pas être compilées à l'aide de <xref:System.Activities.XamlIntegration.TextExpressionCompiler> ou du compilateur hébergé Visual Basic, mais les expressions précédemment compilées peuvent être exécutées.

8. Un assembly unique qui utilise la [transparence de niveau 2](https://aka.ms/Level2Transparency) ne peut pas être utilisé dans .NET Framework 4, [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] en mode de confiance totale et [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] en confiance partielle.

## <a name="new-designer-capabilities"></a><a name="BKMK_NewDesignerCapabilites"></a>Nouvelles fonctionnalités du concepteur

### <a name="designer-search"></a><a name="BKMK_DesignerSearch"></a>Recherche du concepteur

Pour rendre les plus grands workflows plus pratiques, les workflows peuvent maintenant être trouvés par mot clé. Cette fonctionnalité est disponible uniquement dans Visual Studio. Cette fonctionnalité n’est pas disponible dans un concepteur réhébergé. Il existe deux types de recherche disponibles :

- Recherche rapide, lancée avec **Ctrl + F** ou **modifier**, **Rechercher et remplacer**, **recherche rapide**.

- Recherchez dans les fichiers, initiés avec **Ctrl + Maj + F** ou **modifier**, **Rechercher et remplacer**, **Rechercher dans les fichiers**.

Notez que Remplacer n'est pas pris en charge.

#### <a name="quick-find"></a><a name="BKMK_QuickFind"></a>Recherche rapide

Les mots clés trouvés dans les workflows correspondent aux éléments de concepteur suivants :

- Propriétés des objets <xref:System.Activities.Activity>, des objets <xref:System.Activities.Statements.FlowNode>, des objets <xref:System.Activities.Statements.State>, des objets <xref:System.Activities.Statements.Transition>, et d'autres éléments de contrôle de flux personnalisés.

- Variables

- Arguments

- Expressions

La recherche rapide est exécutée sur l'arborescence <xref:System.Activities.Presentation.Model.ModelItem> du concepteur. La recherche rapide n'ajoutera pas d'espaces de noms importés dans la définition de workflow.

#### <a name="find-in-files"></a><a name="BKMK_FindInFiles"></a>Rechercher dans les fichiers

Les mots clés trouvés dans les workflows correspondent au contenu réel des fichiers de workflow. Les résultats de la recherche sont affichés dans le volet d'affichage des résultats de recherche de Visual Studio. Double-cliquez sur l'élément de résultat pour accéder à l'activité qui contient la correspondance dans le concepteur de workflow.

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a><a name="BKMK_VariableDeleteContextMenu"></a>Supprimer l’élément de menu contextuel dans le concepteur de variables et d’arguments

Dans .NET Framework 4, les variables et les arguments ne pouvaient être supprimés que dans le concepteur à l’aide du clavier. À compter de .NET Framework 4,5, les variables et les arguments peuvent être supprimés à l’aide du menu contextuel.

La capture d’écran suivante indique le menu contextuel du concepteur de variable et d’argument.

![Menu contextuel du concepteur de variable et d’argument](./media/whats-new-in-wf-in-dotnet/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a><a name="BKMK_AutoSurround"></a>Entourer automatiquement d’une séquence

Étant donné qu'un workflow ou certaines activités de conteneur (telles que <xref:System.Activities.Statements.NoPersistScope>) peuvent uniquement contenir une seule activité de corps, l'ajout d'une deuxième activité exigeait que le développeur supprime la première activité, ajoute une activité <xref:System.Activities.Statements.Sequence>, puis ajoute les deux activités à l'activité de séquence. À compter de .NET Framework 4,5, lors de l’ajout d’une deuxième activité à l’aire du concepteur, une `Sequence` activité est automatiquement créée pour encapsuler les deux activités.

La capture d'écran suivante affiche une activité `WriteLine` avec le `Body` d'un `NoPersistScope`.

![Activité WriteLine dans le corps d’une activité NoPersistScope.](./media/whats-new-in-wf-in-dotnet/auto-surround-write-line-activity.png)

La capture d’écran suivante montre l’activité `Sequence` créée automatiquement dans le `Body` lorsqu’un second `WriteLine` est déposé sous le premier.

![Séquence créée automatiquement dans le corps d’un NoPersistScope.](./media/whats-new-in-wf-in-dotnet/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a><a name="BKMK_PanMode"></a>Mode panoramique

Pour naviguer plus facilement dans un grand workflow dans le concepteur, le mode panoramiques peut être activé, ce qui permet au développeur de cliquer sur la partie visible du workflow et de la faire glisser, plutôt que d'utiliser les barres de défilement. Le bouton pour activer le mode panoramiques se trouve dans le coin inférieur droit du concepteur.

La capture d'écran suivante indique le bouton de panoramique qui se trouve dans le coin inférieur droit du concepteur de workflow.

![Bouton panoramique mis en surbrillance dans le concepteur de flux de travail.](./media/whats-new-in-wf-in-dotnet/pan-button-workflow-designer.png)

Le bouton central de la souris ou la barre d'espace peut également être utilisé pour appliquer un panoramique au concepteur de workflow.

### <a name="multi-select"></a><a name="BKMK_MultiSelect"></a>Sélection multiple

Plusieurs activités peuvent être sélectionnées en même temps, en faisant glisser un rectangle autour d'elles (lorsque le mode panoramique n'est pas activé), ou en maintenant la touche Ctrl enfoncée et en cliquant sur les activités souhaitées une à une.

Il est également possible de glisser-déplacer plusieurs activités sélectionnées et de les utiliser dans une interaction à l'aide du menu contextuel.

### <a name="outline-view-of-workflow-items"></a><a name="BKMK_DocumentOutline"></a>vue Structure d’éléments de flux de travail

Afin de simplifier la navigation dans les workflows hiérarchiques, les composants d’un workflow s’affichent dans un mode Plan de style arborescent. Le mode plan est affiché dans la vue **structure du document** . Pour ouvrir cette vue, dans le menu supérieur, sélectionnez **Afficher**, **autres fenêtres**, **structure du document**, ou appuyez sur CTRL W, U. Cliquer sur un nœud en mode Plan permet d'accéder à l'activité correspondante dans le Concepteur de workflow, et le mode Plan est mis à jour pour afficher les activités qui sont sélectionnées dans le concepteur.

La capture d’écran suivante du flux de travail terminé à partir du [didacticiel prise en main](getting-started-tutorial.md) présente le mode plan avec un flux de travail séquentiel.

![Capture d’écran du mode plan avec un flux de travail séquentiel dans Visual Studio.](./media/whats-new-in-wf-in-dotnet/outline-view-in-workflow-designer.jpg)

### <a name="c-expressions"></a><a name="BKMK_CSharpExpressions"></a>Expressions C#

Avant .NET Framework 4,5, toutes les expressions dans les workflows pouvaient uniquement être écrites en Visual Basic. Dans .NET Framework 4,5, les expressions Visual Basic sont utilisées uniquement pour les projets créés à l’aide de Visual Basic. Les projets Visual C# utilisent C# pour les expressions. Un éditeur d'expressions C# fonctionnel est fourni, qui a des fonctions telles que la mise en surbrillance de la grammaire et IntelliSense. Les projets de workflow C# créés dans les versions antérieures qui utilisent des expressions Visual Basic continueront à fonctionner.

Les expressions C# sont validées au moment du design. Les erreurs dans les expressions C# sont marquées avec un soulignement ondulé rouge.

Pour plus d’informations sur les expressions C#, consultez [expressions c#](csharp-expressions.md).

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a><a name="BKMK_Visibility"></a>Contrôle accru de la visibilité de la barre de Shell et des éléments d’en-tête

Dans un concepteur réhébergé, certains des contrôles d'interface utilisateur standard peuvent ne pas avoir de signification pour un workflow donné, et peuvent être désactivés. Dans .NET Framework 4, cette personnalisation est prise en charge uniquement par la barre de Shell en bas du concepteur. Dans .NET Framework 4,5, la visibilité des éléments d’en-tête de Shell en haut du concepteur peut être ajustée en définissant <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> avec la <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> valeur appropriée.

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a><a name="BKMK_AutoConnect"></a>Connexion automatique et insertion automatique dans un diagramme de flux de travail et des workflows d’ordinateur d’État

Dans .NET Framework 4, les connexions entre les nœuds d’un flux de travail d’organigramme devaient être ajoutées manuellement. Dans .NET Framework 4,5, les nœuds organigramme et machine à États ont des points de connexion automatique qui deviennent visibles quand une activité est glissée de la boîte à outils vers l’aire du concepteur. Le dépôt d’une activité sur un de ces points ajoute automatiquement l’activité avec la connexion nécessaire.

La capture d'écran suivante montre les points d'attachement qui sont visibles lorsqu'une activité est déplacée depuis la boîte à outils.

![Nœud de démarrage de l’organigramme présentant les points de connexion automatique](./media/whats-new-in-wf-in-dotnet/auto-connect-points-start-node.png)

Les activités peuvent également être déplacées sur les connexions entre des nœuds d'organigramme et des états de façon à insérer automatiquement le nœud entre deux autres nœuds. La capture d’écran suivante montre la ligne de connexion en surbrillance où les activités peuvent être glissées-déposées depuis la boîte à outils.

![Poignée d'insertion automatique pour déposer les activités](./media/whats-new-in-wf-in-dotnet/auto-insert-connecting-line.png)

### <a name="designer-annotations"></a><a name="BKMK_Annotations"></a>Annotations du concepteur

Pour faciliter le développement de plus grands workflows, le concepteur prend désormais en charge l'ajout d'annotations pour faciliter le suivi du processus de création. Une annotation peut être ajoutée aux activités, états, nœuds d’organigramme, variables et arguments. La capture d'écran suivante montre le menu contextuel utilisé pour ajouter des annotations au concepteur.

![Capture d’écran montrant un menu permettant d’ajouter des annotations.](./media/whats-new-in-wf-in-dotnet/designer-annotations-context-menu.png)

### <a name="debugging-states"></a>États de débogage

Dans .NET Framework 4, les éléments non-Activity ne peuvent pas prendre en charge les points d’arrêt de débogage, car ils n’étaient pas des unités d’exécution. Cette version fournit un mécanisme pour ajouter des points d'arrêt aux objets <xref:System.Activities.Statements.State>. Lorsqu'un point d'arrêt est défini sur un <xref:System.Activities.Statements.State>, l'exécution s'arrête lorsque l'état subit une transition, avant que ses activités d'entrée ou déclencheurs ne soient planifiés.

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a><a name="BKMK_ActivityDelegates"></a>Définir et consommer des objets ActivityDelegate dans le concepteur

Les activités dans .NET Framework 4 <xref:System.Activities.ActivityDelegate> ont utilisé des objets pour exposer des points d’exécution dans lesquels d’autres parties du flux de travail pouvaient interagir avec l’exécution d’un workflow, mais l’utilisation de ces points d’exécution nécessitait généralement une quantité de code équitable. Dans cette version finale, les développeurs peuvent définir et utiliser des délégués d'activité à l'aide du concepteur de workflow. Pour plus d’informations, consultez [Comment : définir et consommer des délégués d’activité dans le concepteur de flux de travail](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

### <a name="build-time-validation"></a><a name="BKMK_BuildTimeValidation"></a>Validation au moment de la génération

Dans .NET Framework 4, les erreurs de validation de workflow n’étaient pas comptabilisées comme des erreurs de build pendant la génération d’un projet de Workflow. Cela signifiait que la génération d’un projet de workflow pouvait réussir même lorsqu’il existait des erreurs de validation de workflow. Dans .NET Framework 4,5, les erreurs de validation de workflow provoquent l’échec de la génération.

### <a name="design-time-background-validation"></a><a name="BKMK_DesignTimeValidation"></a>Validation en arrière-plan au moment du design

Dans .NET Framework 4, les flux de travail étaient validés en tant que processus de premier plan, ce qui pourrait potentiellement bloquer l’interface utilisateur pendant les processus de validation complexes ou longs. La validation de workflow a lieu à présent sur un thread d'arrière-plan, afin que l'interface utilisateur ne soit pas bloquée.

### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a><a name="BKMK_ViewState"></a>État d’affichage situé dans un emplacement distinct dans les fichiers XAML

Dans .NET Framework 4, les informations d’état d’affichage d’un workflow sont stockées dans le fichier XAML à de nombreux emplacements différents. Cela n'est pas pratique pour les développeurs qui souhaitent lire le XAML directement, ou écrire du code pour supprimer les informations d'état d'affichage. Dans .NET Framework 4,5, les informations d’état d’affichage dans le fichier XAML sont sérialisées en tant qu’élément distinct dans le fichier XAML. Les développeurs peuvent facilement localiser et modifier les informations d’état d’affichage d’une activité, ou supprimer complètement l’état d’affichage.

### <a name="expression-extensibility"></a><a name="BKMK_ExpressionExtensibility"></a>Extensibilité des expressions

Dans .NET Framework 4,5, nous fournissons aux développeurs un moyen de créer leur propre expression et expérience de création d’expressions qui peut être connectée au concepteur de Workflow.

### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a><a name="BKMK_BackwardCompatRehostedDesigner"></a>Abonnement pour les fonctionnalités de workflow 4,5 dans le concepteur réhébergé

Pour préserver la compatibilité descendante, certaines nouvelles fonctionnalités incluses dans .NET Framework 4,5 ne sont pas activées par défaut dans le concepteur réhébergé. Il s'agit de garantir que les applications existantes qui utilisent le concepteur réhébergé ne sont pas interrompues par la mise à jour vers la version la plus récente. Pour activer les nouvelles fonctionnalités du concepteur réhébergé, affectez à <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> la valeur « .NET Framework 4.5 », ou définissez des membres de <xref:System.Activities.Presentation.DesignerConfigurationService> pour activer des fonctionnalités.

## <a name="new-workflow-development-models"></a><a name="BKMK_NewWFModels"></a>Nouveaux modèles de développement de workflow

Outre les modèles de développement d’organigramme et workflow séquentiel, cette mise en production inclut des workflows Machine à états, et les services de workflow Contrat en premier.

### <a name="state-machine-workflows"></a><a name="BKMK_StateMachine"></a>Workflows d’ordinateur d’État

Les workflows de machine à États ont été introduits dans le cadre de l' .NET Framework 4, version 4.0.1 dans la [mise à jour 1 de la plateforme Microsoft .NET Framework 4](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1). Cette mise à jour inclut plusieurs nouvelles classes et activités qui permettent aux développeurs de créer des workflow de machine à états. Ces classes et activités ont été mises à jour pour .NET Framework 4,5. Les mises à jour comprennent :

1. Possibilité de définir des points d'arrêt sur des états

2. Possibilité de copier et coller des transitions dans le concepteur de workflow

3. Prise en charge du concepteur pour la création de transition de déclencheur partagée

4. Les activités utilisées pour créer des workflows Machine à états, notamment : <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State> et <xref:System.Activities.Statements.Transition>

La capture d’écran suivante montre le flux de travail de l’ordinateur d’état terminé à partir de l’étape [prise en main didacticiel](getting-started-tutorial.md) [procédure : créer un workflow d’ordinateur d’État](how-to-create-a-state-machine-workflow.md).

![Illustration qui montre le flux de travail de l’ordinateur d’état terminé.](./media/whats-new-in-wf-in-dotnet/complete-state-machine-workflow.jpg)

Pour plus d’informations sur la création de workflows de machine à États, consultez [workflows de machine à États](state-machine-workflows.md).

### <a name="contract-first-workflow-development"></a><a name="BKMK_ContractFirst"></a>Développement de workflow contrat en premier

L’outil de développement de workflow contrat en premier permet au développeur de concevoir un contrat dans le code en premier, puis, en quelques clics dans Visual Studio, de générer automatiquement un modèle d’activité dans la boîte à outils représentant chaque opération. Ces activités sont ensuite utilisées pour créer un workflow qui implémente les opérations définies par le contrat. Le concepteur de workflow validera le service de workflow pour garantir que ces opérations sont implémentées et que la signature du workflow correspond à la signature du contrat. Le développeur peut également associer un service de workflow à une collection de contrats implémentés. Pour plus d’informations sur le développement d’un service de workflow contrat en premier, consultez Guide pratique [pour créer un service de workflow qui utilise un contrat de service existant](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).
