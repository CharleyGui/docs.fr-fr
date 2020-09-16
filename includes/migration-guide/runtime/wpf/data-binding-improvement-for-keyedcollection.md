---
ms.openlocfilehash: 9cd1d0955b8b77cb77d5c6938b37d9042d8144f6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606609"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="8ed15-101">Amélioration de la liaison de données pour KeyedCollection</span><span class="sxs-lookup"><span data-stu-id="8ed15-101">Data Binding improvement for KeyedCollection</span></span>

#### <a name="details"></a><span data-ttu-id="8ed15-102">Détails</span><span class="sxs-lookup"><span data-stu-id="8ed15-102">Details</span></span>

<span data-ttu-id="8ed15-103">Correction <xref:System.Windows.Data.Binding> de l’utilisation incorrecte de l’indexeur IList lorsque l’objet source déclare un indexeur personnalisé avec la même signature (par exemple, KeyedCollection &lt; int, TItem &gt; ).</span><span class="sxs-lookup"><span data-stu-id="8ed15-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8ed15-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="8ed15-104">Suggestion</span></span>

<span data-ttu-id="8ed15-105">Pour qu’une application qui cible une version antérieure puisse bénéficier de cette modification, elle doit s’exécuter sur le .NET Framework 4,8 ou version ultérieure, et elle doit accepter la modification en ajoutant le [commutateur AppContext](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la <code>&lt;runtime&gt;</code> section du fichier de configuration d’application et en lui affectant la valeur <code>false</code> :</span><span class="sxs-lookup"><span data-stu-id="8ed15-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="8ed15-106">Name</span><span class="sxs-lookup"><span data-stu-id="8ed15-106">Name</span></span>    | <span data-ttu-id="8ed15-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="8ed15-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8ed15-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="8ed15-108">Scope</span></span>   |<span data-ttu-id="8ed15-109">Majeure</span><span class="sxs-lookup"><span data-stu-id="8ed15-109">Major</span></span>|
|<span data-ttu-id="8ed15-110">Version</span><span class="sxs-lookup"><span data-stu-id="8ed15-110">Version</span></span>|<span data-ttu-id="8ed15-111">4.8</span><span class="sxs-lookup"><span data-stu-id="8ed15-111">4.8</span></span>|
|<span data-ttu-id="8ed15-112">Type</span><span class="sxs-lookup"><span data-stu-id="8ed15-112">Type</span></span>|<span data-ttu-id="8ed15-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="8ed15-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8ed15-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="8ed15-114">Affected APIs</span></span>

<span data-ttu-id="8ed15-115">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="8ed15-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
