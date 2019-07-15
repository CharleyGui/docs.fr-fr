---
ms.openlocfilehash: 62ba525a28960d96c5458aa1481e1f319d5bc875
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859239"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current peut retourner null en cas d’appel dans une clause using

|   |   |
|---|---|
|Détails|<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> peut retourner <code>null</code> et il peut en résulter un <xref:System.NullReferenceException> si toutes les conditions suivantes sont remplies :<ul><li>Vous récupérez la valeur de la propriété <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> dans une méthode qui retourne un <xref:System.Threading.Tasks.Task> ou un <xref:System.Threading.Tasks.Task%601>.</li><li>Vous instanciez l’objet <xref:System.ServiceModel.OperationContextScope> dans une clause <code>using</code>.</li><li>Vous récupérez la valeur de la propriété <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> dans l’<code>using statement</code>. Par exemple :</li></ul><pre><code class="lang-csharp">using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext context = OperationContext.Current;      // OperationContext.Current is null.&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre>|
|Suggestion|Pour résoudre ce problème, vous pouvez effectuer l’opération suivante :<ul><li>Modifiez votre code comme suit pour instancier un nouvel objet <xref:System.ServiceModel.OperationContext.Current%2A> non <code>null</code> :</li></ul><pre><code class="lang-csharp">OperationContext ocx = OperationContext.Current;&#13;&#10;using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext.Current = new OperationContext(ocx.Channel);&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre><ul><li>Installez la dernière mise à jour sur .NET Framework 4.6.2 ou effectuez une mise à niveau vers une version ultérieure du .NET Framework. Cela désactive le flux de <xref:System.Threading.ExecutionContext> dans <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> et restaure le comportement des applications WCF dans .NET Framework 4.6.1 et les versions antérieures. Ce comportement est configurable. Cela équivaut à ajouter le paramètre d’application suivant à votre fichier de configuration :</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Si ce changement n’est pas souhaitable et que votre application dépend du flux de contexte d’exécution entre les contextes d’opération, vous pouvez activer son flux comme suit :<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;false&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Portée|Microsoft Edge|
|Version|4.6.2|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType></li></ul>|

