---
ms.openlocfilehash: daf09748e69e70ad982bcee14461b66579f3bb87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614560"
---
### <a name="avoiding-endless-recursion-for-iworkflowinstancemanagementtransactedcancel-and-iworkflowinstancemanagementtransactedterminate"></a>Éviter la récursivité infinie pour IWorkflowInstanceManagement.TransactedCancel et IWorkflowInstanceManagement.TransactedTerminate

#### <a name="details"></a>Détails

Dans certaines circonstances, quand vous utilisez des API <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedCancel%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedTerminate%2A?displayProperty=nameWithType> pour annuler ou terminer une instance de service de workflow, l’instance de workflow peut rencontrer un dépassement de la capacité de la pile en raison d’une récursivité infinie quand le runtime `Workflow` tente de conserver l’instance de service dans le cadre du traitement de la demande. Le problème se produit si l’instance de workflow est dans un État où elle attend la fin d’une autre demande WCF en suspens vers un autre service. Les `TransactedCancel` `TransactedTerminate` opérations et créent des éléments de travail mis en file d’attente pour l’instance de service de Workflow. Ces éléments de travail ne sont pas exécutés dans le cadre du traitement de la demande `TransactedCancel/TransactedTerminate`. Étant donné que l’instance de service de workflow attend que soit effectuée l’autre demande WCF en suspens, l’élément de travail créé reste dans la file d’attente. L’opération `TransactedCancel/TransactedTerminate` est effectuée, puis le contrôle est retourné au client. Au moment de la validation de la transaction associée à l’opération `TransactedCancel/TransactedTerminate`, la transaction doit conserver l’état de l’instance de service de workflow. Toutefois, comme il existe une demande `WCF` en suspens pour l’instance, le runtime du workflow ne peut pas conserver l’instance de service de workflow, et une boucle de récursivité infinie entraîne le dépassement de la capacité de la pile. Étant donné que `TransactedCancel` et `TransactedTerminate` créent uniquement un élément de travail en mémoire, le fait qu’une transaction existe n’a aucun effet. Une restauration de la transaction n’abandonne pas l’élément de travail. Pour résoudre ce problème, à compter de .NET Framework 4.7.2, nous avons introduit un `AppSetting` qui peut être ajouté au fichier `web.config/app.config` du service de workflow qui lui indique d’ignorer les transactions pour `TransactedCancel` et `TransactedTerminate`. Cela permet à la transaction d’être validée sans attendre la conservation de l’instance de flux de travail. Le AppSetting pour cette fonctionnalité est nommé `microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate` . La valeur `true` indique que la transaction doit être ignorée, évitant ainsi le dépassement de la capacité de la pile. La valeur par défaut de cet AppSetting étant `false`, les instances de service de workflow existantes ne sont pas affectées.

#### <a name="suggestion"></a>Suggestion

Si vous utilisez AppFabric ou un autre client <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> et qu’un dépassement de la capacité de la pile se produit dans l’instance de service de workflow quand vous essayez d’annuler ou de terminer une instance de workflow, vous pouvez ajouter le code suivant à la section `<appSettings>` du fichier web.config/app.config pour le service de workflow :

<pre><code class="lang-xml">&lt;add key=&quot;microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate&quot; value=&quot;true&quot;/&gt;&#13;&#10;</code></pre>

Si vous ne rencontrez pas ce problème, il est inutile d’effectuer cette opération.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.2       |
| Type    | Reciblage |
