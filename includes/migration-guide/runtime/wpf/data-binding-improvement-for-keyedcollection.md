---
ms.openlocfilehash: a0dc2401155a162eaa5aa6b4d9e6af1ca1c2ccc8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802597"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="13a84-101">Amélioration de la liaison de données pour KeyedCollection</span><span class="sxs-lookup"><span data-stu-id="13a84-101">Data Binding improvement for KeyedCollection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="13a84-102">Détails</span><span class="sxs-lookup"><span data-stu-id="13a84-102">Details</span></span>|<span data-ttu-id="13a84-103">Correction d’une mauvaise utilisation de <xref:System.Windows.Data.Binding> par l’indexeur IList quand l’objet source déclare un indexeur personnalisé avec la même signature (ex : KeyedCollection&lt;int,TItem&gt;).</span><span class="sxs-lookup"><span data-stu-id="13a84-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (e.g. KeyedCollection&lt;int,TItem&gt;).</span></span>|
|<span data-ttu-id="13a84-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="13a84-104">Suggestion</span></span>|<span data-ttu-id="13a84-105">Pour que l’application tire parti de ce changement, elle doit s’exécuter sur .NET Framework 4.7.2 ou ultérieur et accepter le changement en ajoutant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant à la section <code>&lt;runtime&gt;</code> du fichier de configuration d’application et en le définissant sur <code>false</code> :</span><span class="sxs-lookup"><span data-stu-id="13a84-105">In order for the application to benefit from this change, it must run on the .NET Framework 4.7.2 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="13a84-106">Portée</span><span class="sxs-lookup"><span data-stu-id="13a84-106">Scope</span></span>|<span data-ttu-id="13a84-107">Majeur</span><span class="sxs-lookup"><span data-stu-id="13a84-107">Major</span></span>|
|<span data-ttu-id="13a84-108">Version</span><span class="sxs-lookup"><span data-stu-id="13a84-108">Version</span></span>|<span data-ttu-id="13a84-109">4.8</span><span class="sxs-lookup"><span data-stu-id="13a84-109">4.8</span></span>|
|<span data-ttu-id="13a84-110">Type</span><span class="sxs-lookup"><span data-stu-id="13a84-110">Type</span></span>|<span data-ttu-id="13a84-111">Runtime</span><span class="sxs-lookup"><span data-stu-id="13a84-111">Runtime</span></span>|

