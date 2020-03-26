---
title: Workflows d'organigramme
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: b84b0de34f8869d9775fe0694e74c340cc16a6b3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249062"
---
# <a name="flowchart-workflows"></a>Workflows d'organigramme

Un organigramme est un paradigme connu pour la conception de programmes. L'activité Organigramme est généralement utilisée pour implémenter des workflows non séquentiels, mais elle peut être utilisée pour les workflows séquentiels en l'absence de nœud `FlowDecision`.

## <a name="flowchart-workflow-structure"></a>Structure de flux de travail Flowchart

 Une activité Flowchart est une activité qui contient une collection d'activités à exécuter.  Les organigrammes contiennent également des éléments de contrôle de flux tels que <xref:System.Activities.Statements.FlowDecision> et <xref:System.Activities.Statements.FlowSwitch%601> qui dirigent l'exécution entre les activités contenues en fonction des valeurs des variables.

## <a name="types-of-flow-nodes"></a>Types de nœuds de débit

 Les types d'éléments utilisés varient en fonction du type de contrôle de flux requis lors de l'exécution d'un élément. Les types d'éléments d'organigramme sont les suivants :

- `FlowStep`- Modélise une seule étape d'exécution dans l'organigramme.

- `FlowDecision`- Lie l'exécution à une condition booléenne, semblable à <xref:System.Activities.Statements.If>.

- `FlowSwitch` – Lie l'exécution à un commutateur exclusif, semblable à <xref:System.Activities.Statements.Switch%601>.

Chaque lien a une propriété `Action` qui définit un <xref:System.Activities.ActivityAction> à utiliser pour exécuter des activités enfants, et une ou plusieurs propriétés `Next` qui définissent l'élément ou les éléments à exécuter à la fin de l'exécution de l'élément actuel.

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Création d’une séquence d’activité de base avec un nœud FlowStep

Pour modéliser une séquence de base dans laquelle deux activités s'exécutent l'une après l'autre, l'élément `FlowStep` est utilisé. Dans l'exemple suivant, deux éléments `FlowStep` sont utilisés pour exécuter deux activités dans l'ordre indiqué.

```xml
<Flowchart>
  <FlowStep>
    <Assign DisplayName="Get Name">
      <Assign.To>
        <OutArgument x:TypeArguments="x:String">[result]</OutArgument>
      </Assign.To>
      <Assign.Value>
        <InArgument x:TypeArguments="x:String">["User"]</InArgument>
      </Assign.Value>
    </Assign>
    <FlowStep.Next>
      <FlowStep>
        <WriteLine Text="Hello, " & [result]/>
      </FlowStep>
    </FlowStep.Next>
  </FlowStep>
</Flowchart>
```

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Création d’un flowchart conditionnel avec un nœud FlowDecision

Pour modéliser un nœud de flux conditionnel dans un workflow d'organigramme (autrement dit, créer un lien qui fonctionne comme le symbole de décision d'un organigramme classique), un nœud <xref:System.Activities.Statements.FlowDecision> est utilisé. La propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> du nœud est définie sur une expression qui détermine la condition, et les propriétés <xref:System.Activities.Statements.FlowDecision.True%2A> et <xref:System.Activities.Statements.FlowDecision.False%2A> sont définies sur les instances <xref:System.Activities.Statements.FlowNode> à exécuter si l'expression a la valeur `true` ou `false`. L'exemple suivant indique comment définir un workflow qui utilise un nœud <xref:System.Activities.Statements.FlowDecision>.

```xml
<Flowchart>
  <FlowStep>
    <Read Result="[s]"/>
    <FlowStep.Next>
      <FlowDecision>
        <IsEmpty Input="[s]" />
        <FlowDecision.True>
          <FlowStep>
            <Write Text="Empty"/>
          </FlowStep>
        </FlowDecision.True>
        <FlowDecision.False>
          <FlowStep>
            <Write Text="Non-Empty"/>
          </FlowStep>
        </FlowDecision.False>
      </FlowDecision>
    </FlowStep.Next>
  </FlowStep>
</Flowchart>
```

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>Création d’un commutateur exclusif avec un nœud FlowSwitch

Pour modéliser un organigramme dans lequel un chemin d’accès exclusif est sélectionné selon une valeur correspondante, le nœud <xref:System.Activities.Statements.FlowSwitch%601> est utilisé. La propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> est définie sur un élément <xref:System.Activities.Activity%601> avec un paramètre de type <xref:System.Object> qui détermine la valeur de correspondance. La propriété <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> définit un dictionnaire de clés et d'objets <xref:System.Activities.Statements.FlowNode> à mettre en correspondance avec l'expression conditionnelle, ainsi qu'un jeu d'objets <xref:System.Activities.Statements.FlowNode> qui détermine le flux de l'exécution si une correspondance est établie avec l'expression conditionnelle. <xref:System.Activities.Statements.FlowSwitch%601> définit également une propriété <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> qui détermine le flux de l'exécution si aucune correspondance n'est établie avec l'expression conditionnelle. L'exemple suivant montre comment définir un workflow qui utilise un élément <xref:System.Activities.Statements.FlowSwitch%601>.

```xml
<Flowchart>
  <FlowSwitch>
    <FlowStep x:Key="Red">
      <WriteRed/>
    </FlowStep>
    <FlowStep x:Key="Blue">
      <WriteBlue/>
    </FlowStep>
    <FlowStep x:Key="Green">
      <WriteGreen/>
    </FlowStep>
  </FlowSwitch>
</Flowchart>
```
