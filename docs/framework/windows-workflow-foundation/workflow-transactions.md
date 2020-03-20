---
title: Transactions de workflow
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 223c18195c8ffd0b51eb5dff77aa81953f6e47a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182674"
---
# <a name="workflow-transactions"></a>Transactions de workflow

[!INCLUDE[wf1](../../../includes/wf1-md.md)] offre une prise en charge pour participer aux transactions <xref:System.Transactions> en utilisant l'activité <xref:System.Activities.Statements.TransactionScope> pour étendre une unité traitée de travail. Alors que le <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> doit être terminé explicitement, l'activité <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> appelle implicitement la transaction une fois cette dernière terminée. Toute activité contenue dans l’élément <xref:System.Activities.Statements.TransactionScope.Body%2A> de l’activité <xref:System.Activities.Statements.TransactionScope> participe à la transaction. WF peut transférer des transactions dans un workflow en faisant appel à l’activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Comme l'activité <xref:System.Activities.Statements.TransactionScope>, toute activité contenue dans le <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participe à la transaction. WF vérifie que les activités dépendant de <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> utilisent à la fois <xref:System.Activities.Statements.TransactionScope> et <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Si les activités fournies par le système ne remplissent pas toutes les conditions, les activités personnalisées peuvent être construites à l’aide du <xref:System.Activities.RuntimeTransactionHandle> afin d’activer un flux avancé et des scénarios de contrôle de transaction.  
  
Dans l’exemple suivant, un flux de <xref:System.Activities.Statements.Sequence> travail est construit <xref:System.Activities.Statements.TransactionScope> consistant en une activité qui contient des activités pour enfants, y compris une activité. Les activités <xref:System.Activities.Statements.TransactionScope.Body%2A> du <xref:System.Activities.Statements.TransactionScope> s'exécutent sous la transaction initialisée par l'activité <xref:System.Activities.Statements.TransactionScope>.  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
```  
  
Pour plus d’informations, voir sur l’utilisation <xref:System.ServiceModel.Activities.TransactedReceiveScope>, voir [Flowing Transactions dans et hors de Workflow Services](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
