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
# <a name="flowchart-workflows"></a><span data-ttu-id="0d11f-102">Workflows d'organigramme</span><span class="sxs-lookup"><span data-stu-id="0d11f-102">Flowchart Workflows</span></span>

<span data-ttu-id="0d11f-103">Un organigramme est un paradigme connu pour la conception de programmes.</span><span class="sxs-lookup"><span data-stu-id="0d11f-103">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="0d11f-104">L'activité Organigramme est généralement utilisée pour implémenter des workflows non séquentiels, mais elle peut être utilisée pour les workflows séquentiels en l'absence de nœud `FlowDecision`.</span><span class="sxs-lookup"><span data-stu-id="0d11f-104">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="0d11f-105">Structure de flux de travail Flowchart</span><span class="sxs-lookup"><span data-stu-id="0d11f-105">Flowchart workflow structure</span></span>

 <span data-ttu-id="0d11f-106">Une activité Flowchart est une activité qui contient une collection d'activités à exécuter.</span><span class="sxs-lookup"><span data-stu-id="0d11f-106">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="0d11f-107">Les organigrammes contiennent également des éléments de contrôle de flux tels que <xref:System.Activities.Statements.FlowDecision> et <xref:System.Activities.Statements.FlowSwitch%601> qui dirigent l'exécution entre les activités contenues en fonction des valeurs des variables.</span><span class="sxs-lookup"><span data-stu-id="0d11f-107">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="0d11f-108">Types de nœuds de débit</span><span class="sxs-lookup"><span data-stu-id="0d11f-108">Types of flow nodes</span></span>

 <span data-ttu-id="0d11f-109">Les types d'éléments utilisés varient en fonction du type de contrôle de flux requis lors de l'exécution d'un élément.</span><span class="sxs-lookup"><span data-stu-id="0d11f-109">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="0d11f-110">Les types d'éléments d'organigramme sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="0d11f-110">Types of flowchart elements include:</span></span>

- <span data-ttu-id="0d11f-111">`FlowStep`- Modélise une seule étape d'exécution dans l'organigramme.</span><span class="sxs-lookup"><span data-stu-id="0d11f-111">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="0d11f-112">`FlowDecision`- Lie l'exécution à une condition booléenne, semblable à <xref:System.Activities.Statements.If>.</span><span class="sxs-lookup"><span data-stu-id="0d11f-112">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="0d11f-113">`FlowSwitch` – Lie l'exécution à un commutateur exclusif, semblable à <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="0d11f-113">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="0d11f-114">Chaque lien a une propriété `Action` qui définit un <xref:System.Activities.ActivityAction> à utiliser pour exécuter des activités enfants, et une ou plusieurs propriétés `Next` qui définissent l'élément ou les éléments à exécuter à la fin de l'exécution de l'élément actuel.</span><span class="sxs-lookup"><span data-stu-id="0d11f-114">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="0d11f-115">Création d’une séquence d’activité de base avec un nœud FlowStep</span><span class="sxs-lookup"><span data-stu-id="0d11f-115">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="0d11f-116">Pour modéliser une séquence de base dans laquelle deux activités s'exécutent l'une après l'autre, l'élément `FlowStep` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0d11f-116">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="0d11f-117">Dans l'exemple suivant, deux éléments `FlowStep` sont utilisés pour exécuter deux activités dans l'ordre indiqué.</span><span class="sxs-lookup"><span data-stu-id="0d11f-117">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="0d11f-118">Création d’un flowchart conditionnel avec un nœud FlowDecision</span><span class="sxs-lookup"><span data-stu-id="0d11f-118">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="0d11f-119">Pour modéliser un nœud de flux conditionnel dans un workflow d'organigramme (autrement dit, créer un lien qui fonctionne comme le symbole de décision d'un organigramme classique), un nœud <xref:System.Activities.Statements.FlowDecision> est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0d11f-119">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="0d11f-120">La propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> du nœud est définie sur une expression qui détermine la condition, et les propriétés <xref:System.Activities.Statements.FlowDecision.True%2A> et <xref:System.Activities.Statements.FlowDecision.False%2A> sont définies sur les instances <xref:System.Activities.Statements.FlowNode> à exécuter si l'expression a la valeur `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="0d11f-120">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="0d11f-121">L'exemple suivant indique comment définir un workflow qui utilise un nœud <xref:System.Activities.Statements.FlowDecision>.</span><span class="sxs-lookup"><span data-stu-id="0d11f-121">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="0d11f-122">Création d’un commutateur exclusif avec un nœud FlowSwitch</span><span class="sxs-lookup"><span data-stu-id="0d11f-122">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="0d11f-123">Pour modéliser un organigramme dans lequel un chemin d’accès exclusif est sélectionné selon une valeur correspondante, le nœud <xref:System.Activities.Statements.FlowSwitch%601> est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0d11f-123">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="0d11f-124">La propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> est définie sur un élément <xref:System.Activities.Activity%601> avec un paramètre de type <xref:System.Object> qui détermine la valeur de correspondance.</span><span class="sxs-lookup"><span data-stu-id="0d11f-124">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="0d11f-125">La propriété <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> définit un dictionnaire de clés et d'objets <xref:System.Activities.Statements.FlowNode> à mettre en correspondance avec l'expression conditionnelle, ainsi qu'un jeu d'objets <xref:System.Activities.Statements.FlowNode> qui détermine le flux de l'exécution si une correspondance est établie avec l'expression conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="0d11f-125">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="0d11f-126"><xref:System.Activities.Statements.FlowSwitch%601> définit également une propriété <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> qui détermine le flux de l'exécution si aucune correspondance n'est établie avec l'expression conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="0d11f-126">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="0d11f-127">L'exemple suivant montre comment définir un workflow qui utilise un élément <xref:System.Activities.Statements.FlowSwitch%601>.</span><span class="sxs-lookup"><span data-stu-id="0d11f-127">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

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
