---
ms.openlocfilehash: beb869208e8d48d762d94b5989a558fa2f1aaf29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622009"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="340dd-101">Amélioration de la liaison de données pour KeyedCollection</span><span class="sxs-lookup"><span data-stu-id="340dd-101">Data Binding improvement for KeyedCollection</span></span>

#### <a name="details"></a><span data-ttu-id="340dd-102">Détails</span><span class="sxs-lookup"><span data-stu-id="340dd-102">Details</span></span>

<span data-ttu-id="340dd-103">Correction <xref:System.Windows.Data.Binding> de l’utilisation incorrecte de l’indexeur IList lorsque l’objet source déclare un indexeur personnalisé avec la même signature (par exemple, KeyedCollection &lt; int, TItem &gt; ).</span><span class="sxs-lookup"><span data-stu-id="340dd-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="340dd-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="340dd-104">Suggestion</span></span>

<span data-ttu-id="340dd-105">Pour qu’une application qui cible une version antérieure puisse bénéficier de cette modification, elle doit s’exécuter sur le .NET Framework 4,8 ou version ultérieure, et elle doit accepter la modification en ajoutant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant à la <code>&lt;runtime&gt;</code> section du fichier de configuration d’application et en lui affectant la valeur <code>false</code> :</span><span class="sxs-lookup"><span data-stu-id="340dd-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="340dd-106">Nom</span><span class="sxs-lookup"><span data-stu-id="340dd-106">Name</span></span>    | <span data-ttu-id="340dd-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="340dd-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="340dd-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="340dd-108">Scope</span></span>   |<span data-ttu-id="340dd-109">Majeure</span><span class="sxs-lookup"><span data-stu-id="340dd-109">Major</span></span>|
|<span data-ttu-id="340dd-110">Version</span><span class="sxs-lookup"><span data-stu-id="340dd-110">Version</span></span>|<span data-ttu-id="340dd-111">4.8</span><span class="sxs-lookup"><span data-stu-id="340dd-111">4.8</span></span>|
|<span data-ttu-id="340dd-112">Type</span><span class="sxs-lookup"><span data-stu-id="340dd-112">Type</span></span>|<span data-ttu-id="340dd-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="340dd-113">Runtime</span></span>|
