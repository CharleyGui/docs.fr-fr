---
ms.openlocfilehash: 8964cd2f69e95e4078001997ad5a5d126ce42d7b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496880"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="e26f2-101">Amélioration de la liaison de données pour KeyedCollection</span><span class="sxs-lookup"><span data-stu-id="e26f2-101">Data Binding improvement for KeyedCollection</span></span>

#### <a name="details"></a><span data-ttu-id="e26f2-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e26f2-102">Details</span></span>

<span data-ttu-id="e26f2-103">Correction <xref:System.Windows.Data.Binding> de l’utilisation incorrecte de l’indexeur IList lorsque l’objet source déclare un indexeur personnalisé avec la même signature (par exemple, KeyedCollection &lt; int, TItem &gt; ).</span><span class="sxs-lookup"><span data-stu-id="e26f2-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e26f2-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e26f2-104">Suggestion</span></span>

<span data-ttu-id="e26f2-105">Pour qu’une application qui cible une version antérieure puisse bénéficier de cette modification, elle doit s’exécuter sur le .NET Framework 4,8 ou version ultérieure, et elle doit accepter la modification en ajoutant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant à la <code>&lt;runtime&gt;</code> section du fichier de configuration d’application et en lui affectant la valeur <code>false</code> :</span><span class="sxs-lookup"><span data-stu-id="e26f2-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="e26f2-106">Name</span><span class="sxs-lookup"><span data-stu-id="e26f2-106">Name</span></span>    | <span data-ttu-id="e26f2-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="e26f2-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e26f2-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="e26f2-108">Scope</span></span>   |<span data-ttu-id="e26f2-109">Majeure</span><span class="sxs-lookup"><span data-stu-id="e26f2-109">Major</span></span>|
|<span data-ttu-id="e26f2-110">Version</span><span class="sxs-lookup"><span data-stu-id="e26f2-110">Version</span></span>|<span data-ttu-id="e26f2-111">4.8</span><span class="sxs-lookup"><span data-stu-id="e26f2-111">4.8</span></span>|
|<span data-ttu-id="e26f2-112">Type</span><span class="sxs-lookup"><span data-stu-id="e26f2-112">Type</span></span>|<span data-ttu-id="e26f2-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="e26f2-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e26f2-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="e26f2-114">Affected APIs</span></span>

<span data-ttu-id="e26f2-115">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="e26f2-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
