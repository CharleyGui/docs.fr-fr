---
title: Workflows d'ordinateur d'état
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: 349d7e00616a1c12dac45f24b1c39c1899d8f824
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728209"
---
# <a name="state-machine-workflows"></a>Workflows d'ordinateur d'état
Une machine à états représente un paradigme connu pour développer des programmes. L'activité <xref:System.Activities.Statements.StateMachine>, avec <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>, et d'autres activités peut être utilisée pour générer des programmes de workflow de machine à états. Cette rubrique fournit une vue d'ensemble de la création des workflows de machine à états.  
  
## <a name="state-machine-workflow-overview"></a>Présentation du workflow de machine à états  
 Les workflows de machine à états fournissent un style de modélisation avec lequel vous pouvez modéliser votre workflow de façon pilotée par événements. Une activité <xref:System.Activities.Statements.StateMachine> contient les états et les transitions qui composent la logique de la machine à états, et peut être utilisée partout où une activité peut être utilisée. Il existe plusieurs classes dans le runtime de machine à états :  
  
- <xref:System.Activities.Statements.StateMachine>  
  
- <xref:System.Activities.Statements.State>  
  
- <xref:System.Activities.Statements.Transition>  
  
 Pour créer un workflow d’ordinateur d’État, les États sont <xref:System.Activities.Statements.StateMachine> ajoutés à une activité, et les transitions sont utilisées pour contrôler le flux entre les États. La capture d’écran suivante, extraite de l’étape [prise en main didacticiel](getting-started-tutorial.md) [procédure : créer un workflow d’ordinateur d’État](how-to-create-a-state-machine-workflow.md), montre un workflow d’ordinateur d’État avec trois États et trois transitions. **Initialiser la cible** est l’état initial et représente le premier État du flux de travail. Cela est désigné par la ligne qui le mène à partir du nœud de **départ** . L’état final du flux de travail est nommé **FinalState**et représente le point auquel le flux de travail est terminé.  
  
 ![Illustration qui montre le flux de travail de l’ordinateur d’état terminé.](./media/state-machine-workflows/complete-state-machine-workflow.jpg)  
  
 Un workflow de machine à états ne doit avoir qu'un seul état initial, et au moins un état final. Chaque état qui n'est pas un état final doit avoir au moins une transition. Les sections suivantes décrivent la création et la configuration des états et des transitions.  
  
## <a name="creating-and-configuring-states"></a>Création et configuration d'états  
 Un <xref:System.Activities.Statements.State> représente un état dans lequel une machine à états peut être. Pour ajouter un <xref:System.Activities.Statements.State> à un workflow, faites glisser le concepteur d’activités **State** de la section **machine à États** de la **boîte à outils** et déposez-le sur une <xref:System.Activities.Statements.StateMachine> activité sur l’aire de concepteur de flux de travail Windows.  
  
 ![Capture d’écran de la section de la machine à États de la boîte à outils.](./media/state-machine-workflows/state-machine-section-toolbox.jpg)  
  
 Pour configurer un État comme **état initial**, cliquez avec le bouton droit sur l’État et sélectionnez **définir en tant qu’état initial**. En outre, s’il n’y a pas d’état initial actuel, l’état initial peut être désigné en faisant glisser une ligne du nœud de **départ** situé en haut du flux de travail vers l’état souhaité. Lorsqu’une <xref:System.Activities.Statements.StateMachine> activité est déposée dans le concepteur de workflow, elle est préconfigurée avec un état initial nommé **State1**. Un workflow de machine à états ne doit avoir qu'un seul état initial.  
  
 Un état qui représente un état d'arrêt dans une machine à états est appelé un état final. Un état final est un état dont la propriété <xref:System.Activities.Statements.State.IsFinal%2A> a la valeur `true`, n'a aucune activité <xref:System.Activities.Statements.State.Exit%2A>, et aucune transition provenant de cette dernière. Pour ajouter un état final à un workflow, faites glisser un concepteur d’activités **FinalState** de la section **machine à États** de la **boîte à outils** et déposez-le sur une <xref:System.Activities.Statements.StateMachine> activité sur l’aire de concepteur de flux de travail Windows. Un workflow de machine à états doit avoir au moins un état final.  
  
### <a name="configuring-entry-and-exit-actions"></a>Configurer les actions d'entrée et de sortie  
 Un état peut avoir une propriété <xref:System.Activities.Statements.State.Entry%2A> et une action <xref:System.Activities.Statements.State.Exit%2A>. (Un état configuré comme état final ne peut avoir qu'une action d'entrée.) Lorsqu'une instance du workflow entre dans un état, toutes les activités de l'action d'entrée s'exécutent. Une fois l’action d’entrée terminée, les déclencheurs pour les transitions de l’État sont planifiés. Lorsqu'une transition vers un autre état est validée, les activités de l'action de sortie sont exécutées, même si l'état revient au même état. Une fois l’action de sortie terminée, les activités de l’action de transition s’exécutent, puis le nouvel état passe à et ses actions d’entrée sont planifiées.  
  
> [!NOTE]
> Lors du débogage d'un workflow de machine à états, les points d'arrêt peuvent être placés sur l'activité de machine à états racine et les états dans le workflow de machine à états. Les points d'arrêt ne peuvent pas être placés directement sur les transitions, mais ils peuvent être placés sur toutes les activités contenues dans les états et les transitions.  
  
## <a name="creating-and-configuring-transitions"></a>Création et configuration de transitions  
 Tous les États doivent avoir au moins une transition, à l’exception d’un état final, qui peut ne pas avoir de transitions. Des transitions peuvent être ajoutées après ajout d’un état à un workflow de machine à états, ou elles peuvent être créées à mesure que l’état est déposé.  
  
 Pour ajouter un <xref:System.Activities.Statements.State> et créer une transition en une seule étape, faites glisser une activité **State** de la section **machine à États** de la **boîte à outils** et placez-la sur un autre État dans le concepteur de Workflow. Lorsque le <xref:System.Activities.Statements.State> est déplacé vers un autre <xref:System.Activities.Statements.State>, quatre triangles apparaissent autour de l'autre <xref:System.Activities.Statements.State>. Si <xref:System.Activities.Statements.State> est déposé sur un des quatre triangles, il est ajouté à la machine à états et une transition est créée à partir du <xref:System.Activities.Statements.State> source vers le <xref:System.Activities.Statements.State> de destination de dépôt. Pour plus d’informations, consultez [Concepteur d’activités de transition](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Pour créer une transition après ajout d'un état, il existe deux options. La première option consiste à faire glisser l’état depuis l’aire du concepteur de workflow et à le placer sur un état existant, puis à le déposer sur l’un des points de dépôt. Cela est similaire à la méthode décrite dans la section précédente. Vous pouvez également pointer la souris sur l'état source souhaité, et faire glisser une ligne vers l'état de destination souhaité.  
  
> [!NOTE]
> Un seul état dans une machine à états peut contenir jusqu'à 76 transitions créées à l'aide du concepteur de workflow. Le nombre maximal de transitions d'un état pour les workflows créés en dehors du concepteur est limité uniquement par les ressources système.  
  
 Une transition peut avoir un <xref:System.Activities.Statements.Transition.Trigger%2A>, un <xref:System.Activities.Statements.Transition.Condition%2A> et un <xref:System.Activities.Statements.Transition.Action%2A>. Une transition <xref:System.Activities.Statements.Transition.Trigger%2A> est planifiée lorsque l’action de <xref:System.Activities.Statements.State.Entry%2A> l’état source de la transition est terminée. En général, <xref:System.Activities.Statements.Transition.Trigger%2A> est une activité qui attend qu'un type d'événement se produise, mais il peut s'agir de n'importe quelle activité, ou d'aucune activité. Une fois que l'activité <xref:System.Activities.Statements.Transition.Trigger%2A> est terminée, <xref:System.Activities.Statements.Transition.Condition%2A>, le cas échéant, est évalué. S’il n’y <xref:System.Activities.Statements.Transition.Trigger%2A> a pas d’activité <xref:System.Activities.Statements.Transition.Condition%2A> , la est évaluée immédiatement. Si la condition a la valeur `false`, la transition est annulée et l' <xref:System.Activities.Statements.Transition.Trigger%2A> activité de toutes les transitions de l’État est replanifiée. Si d’autres transitions partagent le même état source que la transition actuelle, ces <xref:System.Activities.Statements.Transition.Trigger%2A> actions sont annulées et replanifiées également. Si <xref:System.Activities.Statements.Transition.Condition%2A> a la valeur `true`, ou s'il n'existe aucune condition, l'action <xref:System.Activities.Statements.State.Exit%2A> de l'état source est exécutée, puis le <xref:System.Activities.Statements.Transition.Action%2A> de la transition est exécuté. Lorsque se <xref:System.Activities.Statements.Transition.Action%2A> termine, le contrôle passe à l’état **cible**  
  
 Les transitions qui partagent un déclencheur commun sont appelées transitions de déclencheur partagées. Chaque transition d'un groupe de transitions de déclencheur partagé a le même déclencheur, mais un <xref:System.Activities.Statements.Transition.Condition%2A> et une action uniques. Pour ajouter des actions supplémentaires à une transition et créer une transition partagée, cliquez sur le cercle qui indique le début de la transition souhaitée et faites-le glisser vers l'état souhaité. La nouvelle transition partagera le même déclencheur que la transition d'origine, mais elle aura une condition et une action uniques. Des transitions partagées peuvent également être créées à partir du concepteur de transition en cliquant sur **Ajouter une transition de déclencheur partagée** en bas du concepteur de transition, puis en sélectionnant l’État cible souhaité dans la liste déroulante **États disponibles pour la connexion** .  
  
> [!NOTE]
> Notez que si la condition <xref:System.Activities.Statements.Transition.Condition%2A> d'une transition a pour valeur `False` (ou si toutes les conditions d'une transition de déclencheur partagée ont la valeur `False`), la transition n'a pas lieu et tous les déclencheurs de toutes les transitions de l'état sont replanifiés.  
  
 Pour plus d’informations sur la création de workflows de machine à États, consultez Guide pratique [pour créer un workflow d’ordinateur d’État, le concepteur d'](how-to-create-a-state-machine-workflow.md) [activités StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer), le [Concepteur](/visualstudio/workflow-designer/state-activity-designer)d’activités d’État, le [Concepteur d’activités FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)et le concepteur d’activités de [transition](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Terminologie de machine à états  
 Cette section explique la terminologie de machine à états utilisée dans cette rubrique.  
  
 State  
 Unité de base qui constitue une machine à états. Une machine à états peut être dans un état à un moment donné.  
  
 Action d'entrée  
 Activité exécutée lors de la transition à l'état  
  
 Action de sortie  
 Activité exécutée lors de la sortie de l'état  
  
 Transition  
 Relation dirigée entre deux États qui représente la réponse complète d’un ordinateur d’État à une occurrence d’un événement d’un type particulier.  
  
 Transition partagée  
 Transition qui partage un état source et un déclencheur avec une ou plusieurs transitions, mais qui possède une condition et une action uniques.  
  
 Déclencheur  
 Activité de déclenchement qui provoque une transition.  
  
 Condition  
 Contrainte qui doit s’évaluer à `true` après le déclencheur pour que la transition se termine.  
  
 Action de transition  
 Activité qui est exécutée lors de l’exécution d’une certaine transition.  
  
 Transition conditionnelle  
 Transition avec une condition explicite.  
  
 Transition  
 Transition qui transite d’un État à lui-même.  
  
 État initial  
 État qui représente le point de départ de l’ordinateur d’État.  
  
 État final  
 État qui représente l’achèvement de la machine à États.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer un workflow de machine à états](how-to-create-a-state-machine-workflow.md)
- [Concepteur d'activités StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer)
- [Concepteur d'activités d'état](/visualstudio/workflow-designer/state-activity-designer)
- [Concepteur d'activités FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)
- [Concepteur d'activités de transition](/visualstudio/workflow-designer/transition-activity-designer)
