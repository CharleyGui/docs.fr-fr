---
ms.openlocfilehash: e08b78b49cab88d4435d75b04bd446b413a61340
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859239"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current peut retourner null en cas d’appel dans une clause using

|   |   |
|---|---|
|Détails|<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> peut retourner <code>null</code> et il peut en résulter un <xref:System.NullReferenceException> si toutes les conditions suivantes sont remplies :<ul><li>Vous récupérez la valeur de la propriété <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> dans une méthode qui retourne un <xref:System.Threading.Tasks.Task> ou un <xref:System.Threading.Tasks.Task%601>.</li><li>Vous instanciez l’objet <xref:System.ServiceModel.OperationContextScope> dans une clause <code>using</code>.</li><li>Vous récupérez la valeur de la propriété <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> dans l’<code>using statement</code>. Par exemple :</li></ul><pre><code class="lang-csharp">using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext context = OperationContext.Current;      // OperationContext.Current is null.&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre>|
|Suggestion|Pour résoudre ce problème, vous pouvez effectuer l’opération suivante :<ul><li>Modifiez votre code comme suit pour<code>null</code> <xref:System.ServiceModel.OperationContext.Current%2A> instantané d’un nouvel objet non :</li></ul><pre><code class="lang-csharp">OperationContext ocx = OperationContext.Current;&#13;&#10;using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext.Current = new OperationContext(ocx.Channel);&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre><ul><li>Installez la dernière mise à jour sur .NET Framework 4.6.2 ou effectuez une mise à niveau vers une version ultérieure du .NET Framework. Cela désactive le flux de <xref:System.Threading.ExecutionContext> dans <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> et restaure le comportement des applications WCF dans .NET Framework 4.6.1 et les versions antérieures. Ce comportement est configurable. Cela équivaut à ajouter le paramètre d’application suivant à votre fichier de configuration :</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Si ce changement n’est pas souhaitable et que votre application dépend du flux de contexte d’exécution entre les contextes d’opération, vous pouvez activer son flux comme suit :<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;false&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Étendue|Edge|
|Version|4.6.2|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType></li></ul>|
