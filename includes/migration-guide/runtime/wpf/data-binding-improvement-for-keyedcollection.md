---
ms.openlocfilehash: beb869208e8d48d762d94b5989a558fa2f1aaf29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622009"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>Amélioration de la liaison de données pour KeyedCollection

#### <a name="details"></a>Détails

Correction <xref:System.Windows.Data.Binding> de l’utilisation incorrecte de l’indexeur IList lorsque l’objet source déclare un indexeur personnalisé avec la même signature (par exemple, KeyedCollection &lt; int, TItem &gt; ).

#### <a name="suggestion"></a>Suggestion

Pour qu’une application qui cible une version antérieure puisse bénéficier de cette modification, elle doit s’exécuter sur le .NET Framework 4,8 ou version ultérieure, et elle doit accepter la modification en ajoutant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant à la <code>&lt;runtime&gt;</code> section du fichier de configuration d’application et en lui affectant la valeur <code>false</code> :<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4.8|
|Type|Runtime|
