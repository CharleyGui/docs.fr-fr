---
title: Compensation
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 60e2789c4bbd29185af50eaf6555307b894d3902
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289189"
---
# <a name="compensation"></a>Compensation

La compensation en Windows Workflow Foundation (WF) est le mécanisme par lequel le travail effectué précédemment peut être annulé ou compensé (selon la logique définie par l’application) lorsqu’une défaillance suivante se produit. Cette section décrit comment utiliser une compensation dans les flux de travail.  
  
## <a name="compensation-vs-transactions"></a>Compensation contre Transactions  

 Une transaction vous permet de combiner plusieurs opérations en une seule unité de travail. L’utilisation d’une transaction permet à votre application d’annuler (restaurer) toute modification exécutée depuis une transaction en cas d’erreur au cours du processus de transaction. Toutefois, l’utilisation de transactions peut ne pas convenir dans le cas d’un travail de longue durée. Par exemple, une application de planification de voyage est implémentée en tant que flux de travail. Les étapes du flux de travail peuvent porter sur la réservation d'un vol, l'attente de l'approbation du gestionnaire et le paiement du vol. Ce processus pourrait prendre de nombreux jours et ne s’avère pas pratique pour que les étapes de réservation et de paiement du vol puissent participer à la même transaction. Dans un tel scénario, la compensation pourrait être utilisée pour annuler l'étape de réservation du flux de travail en cas d'erreur ultérieure lors du traitement.  
  
> [!NOTE]
> Cette rubrique couvre la compensation dans les workflows. Pour plus d’informations sur les transactions dans les workflows, consultez [transactions](workflow-transactions.md) et <xref:System.Activities.Statements.TransactionScope> . Pour plus d’informations sur les transactions, consultez <xref:System.Transactions?displayProperty=nameWithType> et <xref:System.Transactions.Transaction?displayProperty=nameWithType> .  
  
## <a name="using-compensableactivity"></a>Utilisation de CompensableActivity  

 <xref:System.Activities.Statements.CompensableActivity> est l'activité de compensation principale dans [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Toutes les activités qui effectuent un travail pouvant nécessiter d'être compensé sont placées dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A> d'un <xref:System.Activities.Statements.CompensableActivity>. Dans cet exemple, l'étape de réservation de l'achat d'un vol est placée dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A> d'un <xref:System.Activities.Statements.CompensableActivity> et l'annulation de la réservation est placée dans le <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>. Juste après le <xref:System.Activities.Statements.CompensableActivity> dans le workflow, deux activités doivent être exécutées, d'une part l'approbation du gestionnaire, d'autre part l'achat du vol. Si une condition d'erreur entraîne l'annulation du workflow une fois <xref:System.Activities.Statements.CompensableActivity> correctement terminé, les activités du gestionnaire <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> sont planifiées et le vol est annulé.  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 L'exemple suivant est le workflow en XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 Lorsque le workflow est appelé, la sortie suivante s'affiche sur la console.  
  
 **ReserveFlight : le ticket est réservé.**  
**ManagerApproval : approbation du gestionnaire reçue.** 
 **PurchaseFlight : le ticket est acheté.** 
 Le **Workflow s’est terminé avec succès avec l’État : fermé.**
> [!NOTE]
> Les exemples d'activités de cette rubrique, telles que `ReserveFlight`, affichent leur nom et leur but dans la console pour faciliter l'illustration de l'ordre dans lequel les activités sont exécutées lorsque la compensation se produit.  
  
### <a name="default-workflow-compensation"></a>Compensation de workflow par défaut  

 Par défaut, si le workflow est annulé, la logique de compensation est exécutée pour toute activité compensable ayant abouti et n'ayant pas encore été confirmée ou compensée.  
  
> [!NOTE]
> Lorsqu’un <xref:System.Activities.Statements.CompensableActivity> est *confirmé*, la compensation pour l’activité ne peut plus être appelée. Le processus de confirmation est décrit plus loin dans cette section.  
  
 Dans cet exemple, une exception est levée après que le vol a été réservé mais avant l'étape d'approbation par le gestionnaire.  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 Cet exemple est le workflow en XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 Lorsque le workflow est appelé, l'exception de condition d'erreur simulée est gérée par l'application hôte dans <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, le workflow est annulé, et la logique de compensation est appelée.  
  
 **ReserveFlight : le ticket est réservé.**  
**SimulatedErrorCondition : levée d’un ApplicationException.** 
 **Exception non gérée du flux de travail :** 
 **System. ApplicationException : condition d’erreur simulée dans le Workflow.** 
 **CancelFlight : le ticket est annulé.** 
 Le **Workflow s’est terminé avec succès avec l’État : annulé.**

### <a name="cancellation-and-compensableactivity"></a>Annulation et CompensableActivity  

 Si les activités dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A> d'un <xref:System.Activities.Statements.CompensableActivity> ne se sont pas terminées et que l'activité est annulée, les activités dans le <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> sont exécutées.  
  
> [!NOTE]
> <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> est appelé uniquement si les activités dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> ne se sont pas terminées et que l'activité est annulée. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> est exécuté uniquement si les activités dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> se sont terminées avec succès et que la compensation est, par la suite, appelée sur l'activité.  
  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> donne aux auteurs de workflow la possibilité de fournir n’importe quelle logique d’annulation appropriée. Dans l'exemple suivant, une exception est levée pendant l'exécution de <xref:System.Activities.Statements.CompensableActivity.Body%2A>, puis <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> est appelé.  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 Cet exemple est le workflow en XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 Lorsque le workflow est appelé, l'exception de condition d'erreur simulée est gérée par l'application hôte dans <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, le workflow est annulé, et la logique d'annulation de <xref:System.Activities.Statements.CompensableActivity> est appelée. Dans cet exemple, la logique de compensation et la logique d'annulation ont des objectifs différents. Si <xref:System.Activities.Statements.CompensableActivity.Body%2A> se termine avec succès, cela signifie que la carte de crédit a été facturée et le vol réservé, donc la compensation doit annuler les deux étapes. (Dans cet exemple, l’annulation du vol annule automatiquement les frais de carte de crédit.) Toutefois, si le <xref:System.Activities.Statements.CompensableActivity> est annulé, cela signifie que le <xref:System.Activities.Statements.CompensableActivity.Body%2A> n’est pas terminé et que la logique de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> doit être en mesure de déterminer comment gérer au mieux l’annulation. Dans cet exemple, le <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> annule la facturation de la carte de crédit, mais comme `ReserveFlight` était la dernière activité dans <xref:System.Activities.Statements.CompensableActivity.Body%2A>, il n'essaie pas d'annuler le vol. Comme `ReserveFlight` était la dernière activité dans le <xref:System.Activities.Statements.CompensableActivity.Body%2A>, si elle s'est terminée avec succès, <xref:System.Activities.Statements.CompensableActivity.Body%2A> s'est terminé et aucune annulation n'est possible.  
  
 **ChargeCreditCard : frais de la carte de crédit pour le vol.**  
**SimulatedErrorCondition : levée d’un ApplicationException.** 
 **Exception non gérée du flux de travail :** 
 **System. ApplicationException : condition d’erreur simulée dans le Workflow.** 
 **CancelCreditCard : annuler les frais de carte de crédit.** 
 Le **Workflow s’est terminé avec succès avec l’État : annulé.**  Pour plus d’informations sur l’annulation, consultez [annulation](modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Compensation explicite à l'aide de l'activité Compensate  

 Dans la section précédente, la compensation implicite a été couverte. La compensation implicite peut convenir à des scénarios simples, mais si un contrôle explicite supplémentaire est requis sur la planification de compensation, la gestion de l'activité <xref:System.Activities.Statements.Compensate> peut être utilisée. Pour initialiser le processus de compensation avec l'activité <xref:System.Activities.Statements.Compensate>, le <xref:System.Activities.Statements.CompensationToken> du <xref:System.Activities.Statements.CompensableActivity> pour lequel la compensation est désirée est utilisé. L'activité <xref:System.Activities.Statements.Compensate> peut être utilisée pour initialiser la compensation sur tout <xref:System.Activities.Statements.CompensableActivity> ayant abouti et qui n'a pas été confirmé ou compensé. Par exemple, une activité <xref:System.Activities.Statements.Compensate> pourrait être utilisée dans la section <xref:System.Activities.Statements.TryCatch.Catches%2A> d'une activité <xref:System.Activities.Statements.TryCatch>, ou à n'importe quel moment après que le <xref:System.Activities.Statements.CompensableActivity> a abouti. Dans cet exemple, l'activité <xref:System.Activities.Statements.Compensate> est utilisée dans la propriété <xref:System.Activities.Statements.TryCatch.Catches%2A> d'une activité <xref:System.Activities.Statements.TryCatch> pour inverser l'action du <xref:System.Activities.Statements.CompensableActivity>.  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 Cet exemple est le workflow en XAML.  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 Lorsque le workflow est appelé, la sortie suivante s'affiche sur la console.  
  
 **ReserveFlight : le ticket est réservé.**  
**SimulatedErrorCondition : levée d’un ApplicationException.** 
 **CancelFlight : le ticket est annulé.** 
 Le **Workflow s’est terminé avec succès avec l’État : fermé.**

### <a name="confirming-compensation"></a>Confirmer la compensation  

 Par défaut, les activités compensables peuvent être compensées à n'importe quel moment, à condition qu'elles soient achevées. Toutefois, dans certains cas cela peut ne pas être suffisant. Dans l'exemple précédent la compensation destinée à réserver le ticket devait permettre d'annuler la réservation. Toutefois, une fois le vol effectué cette étape de compensation n'est plus valide. La confirmation de l'activité compensable appelle l'activité spécifiée dans la section <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>. Une utilisation possible de cela est de permettre la libération de toutes les ressources qui sont nécessaires pour effectuer la compensation. Lorsqu'une activité compensable est confirmée, il n'est pas possible de la dédommager, et si vous tentez cette opération, une exception <xref:System.InvalidOperationException> est levée. Lorsqu'un flux de travail aboutit, toutes les activités non confirmées et non dédommagées ayant abouti sont confirmées dans l'ordre inverse d'achèvement. Dans cet exemple le vol est réservé, acheté et finalisé, puis, l'activité compensable est confirmée. Pour confirmer un <xref:System.Activities.Statements.CompensableActivity>, utilisez l'activité <xref:System.Activities.Statements.Confirm> et spécifiez le <xref:System.Activities.Statements.CompensationToken> du <xref:System.Activities.Statements.CompensableActivity> à confirmer.  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 Cet exemple est le workflow en XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
Lorsque le workflow est appelé, la sortie suivante s'affiche sur la console.  
  
**ReserveFlight : le ticket est réservé.**  
**ManagerApproval : approbation du gestionnaire reçue.** 
 **PurchaseFlight : le ticket est acheté.** 
 **TakeFlight : le vol est terminé.** 
 **ConfirmFlight : le vol a été pris, aucune compensation possible.** 
 Le **Workflow s’est terminé avec succès avec l’État : fermé.**

## <a name="nesting-compensation-activities"></a>Imbrication d'activités de compensation  

Un <xref:System.Activities.Statements.CompensableActivity> peut être placé dans la section <xref:System.Activities.Statements.CompensableActivity.Body%2A> d'un autre <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity> ne peut pas être placé dans un gestionnaire d'un autre <xref:System.Activities.Statements.CompensableActivity>. Il est de la responsabilité d'un <xref:System.Activities.Statements.CompensableActivity> parent de garantir que lorsqu'il est annulé, confirmé, ou compensé, toutes les activités enfants compensables terminées avec succès et qui n'ont pas encore été confirmées ou compensées doivent être confirmées ou compensées avant que le parent complète l'annulation, la confirmation ou la compensation. Si cela n'est pas modélisé explicitement, le <xref:System.Activities.Statements.CompensableActivity> parent compensera implicitement les activités compensables enfants si le parent a reçu le signal d'annulation ou de compensation. Si le parent a reçu le signal de confirmation, il confirme implicitement les activités compensables enfants. Si la logique pour gérer l'annulation, la confirmation ou la compensation est explicitement modélisée dans le gestionnaire du <xref:System.Activities.Statements.CompensableActivity>parent, les enfants qui ne sont pas gérés explicitement seront confirmés implicitement.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
