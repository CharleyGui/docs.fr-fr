---
ms.openlocfilehash: 8aae403e3f23d3bfc755140b2ac29d757f10f753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74451414"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>Amélioration de la liaison de données pour KeyedCollection

|   |   |
|---|---|
|Détails|Utilisation <xref:System.Windows.Data.Binding> incorrecte fixe de l’indexeur IList lorsque l’objet source déclare un indexeur personnalisé avec la même signature (par exemple, KeyedCollection&lt;int,TItem&gt;).|
|Suggestion|Pour qu’une application qui cible une version plus ancienne bénéficie de cette modification, elle doit s’exécuter sur le cadre .NET 4.8 ou plus tard, et <code>false</code>elle doit opter pour la modification en ajoutant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant à la <code>&lt;runtime&gt;</code> section du fichier config app et en la définissant à :<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Étendue|Majeure|
|Version|4.8|
|Type|Runtime|
