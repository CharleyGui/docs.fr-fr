---
ms.openlocfilehash: 8964cd2f69e95e4078001997ad5a5d126ce42d7b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496880"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>Amélioration de la liaison de données pour KeyedCollection

#### <a name="details"></a>Détails

Correction <xref:System.Windows.Data.Binding> de l’utilisation incorrecte de l’indexeur IList lorsque l’objet source déclare un indexeur personnalisé avec la même signature (par exemple, KeyedCollection &lt; int, TItem &gt; ).

#### <a name="suggestion"></a>Suggestion

Pour qu’une application qui cible une version antérieure puisse bénéficier de cette modification, elle doit s’exécuter sur le .NET Framework 4,8 ou version ultérieure, et elle doit accepter la modification en ajoutant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant à la <code>&lt;runtime&gt;</code> section du fichier de configuration d’application et en lui affectant la valeur <code>false</code> :<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4.8|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
