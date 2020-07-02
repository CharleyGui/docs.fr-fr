---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616247"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a><span data-ttu-id="5a6fe-101">La définition XOML du workflow et les clés de cache SqlTrackingService sont passées de MD5 à SHA256</span><span class="sxs-lookup"><span data-stu-id="5a6fe-101">Workflow XOML definition and SqlTrackingService cache keys changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="5a6fe-102">Détails</span><span class="sxs-lookup"><span data-stu-id="5a6fe-102">Details</span></span>

<span data-ttu-id="5a6fe-103">L’exécution du workflow conserve un cache des définitions de workflow définies en XOML.</span><span class="sxs-lookup"><span data-stu-id="5a6fe-103">The Workflow Runtime in keeps a cache of workflow definitions defined in XOML.</span></span> <span data-ttu-id="5a6fe-104">SqlTrackingService conserve également un cache qui est indexé par des chaînes.</span><span class="sxs-lookup"><span data-stu-id="5a6fe-104">The SqlTrackingService also keeps a cache that is keyed by strings.</span></span> <span data-ttu-id="5a6fe-105">Ces caches sont indexés par les valeurs qui incluent la valeur de hachage de la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="5a6fe-105">These caches are keyed by values that include checksum hash value.</span></span> <span data-ttu-id="5a6fe-106">Dans .NET Framework 4.7.2 et versions antérieures, le hachage de somme de contrôle utilisait l’algorithme MD5, ce qui entraînait des problèmes sur les systèmes compatibles FIPS.</span><span class="sxs-lookup"><span data-stu-id="5a6fe-106">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="5a6fe-107">À partir de la .NET Framework 4,8, l’algorithme utilisé est SHA256. Il ne devrait pas y avoir de problème de compatibilité avec cette modification, car les valeurs sont recalculées chaque fois que l’exécution du workflow et SqlTrackingService démarrent.</span><span class="sxs-lookup"><span data-stu-id="5a6fe-107">Starting with the .NET Framework 4.8, the algorithm used is SHA256.There shouldn't be a compatibility issue with this change because the values are recalculated each time the Workflow Runtime and SqlTrackingService is started.</span></span> <span data-ttu-id="5a6fe-108">Toutefois, nous vous proposons des astuces pour permettre aux clients de revenir à l’algorithme de hachage existant, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5a6fe-108">However, we have provided quirks to allow customers to revert back to usage of the legacy hashing algorithm, if necessary.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5a6fe-109">Suggestion</span><span class="sxs-lookup"><span data-stu-id="5a6fe-109">Suggestion</span></span>

<span data-ttu-id="5a6fe-110">Si ce changement présente un problème lors de l’exécution de workflows, essayez de définir un commutateur `AppContext` ou les deux :</span><span class="sxs-lookup"><span data-stu-id="5a6fe-110">If this change presents a problem when executing workflows, try setting one or both of the `AppContext` switches:</span></span>

- <span data-ttu-id="5a6fe-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; sur true.</span><span class="sxs-lookup"><span data-stu-id="5a6fe-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; to true.</span></span>
- <span data-ttu-id="5a6fe-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; sur true.</span><span class="sxs-lookup"><span data-stu-id="5a6fe-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; to true.</span></span>
<span data-ttu-id="5a6fe-113">Dans le code :</span><span class="sxs-lookup"><span data-stu-id="5a6fe-113">In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="5a6fe-114">Ou dans le fichier de configuration (cette opération doit avoir lieu dans le fichier de configuration de l’application qui crée l’objet <xref:System.Workflow.Runtime.WorkflowRuntime>) :</span><span class="sxs-lookup"><span data-stu-id="5a6fe-114">Or in the configuration file (this needs to be in the config file for the application that is creating the <xref:System.Workflow.Runtime.WorkflowRuntime> object):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="5a6fe-115">Nom</span><span class="sxs-lookup"><span data-stu-id="5a6fe-115">Name</span></span>    | <span data-ttu-id="5a6fe-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="5a6fe-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5a6fe-117">Étendue</span><span class="sxs-lookup"><span data-stu-id="5a6fe-117">Scope</span></span>   | <span data-ttu-id="5a6fe-118">Secondaire</span><span class="sxs-lookup"><span data-stu-id="5a6fe-118">Minor</span></span>       |
| <span data-ttu-id="5a6fe-119">Version</span><span class="sxs-lookup"><span data-stu-id="5a6fe-119">Version</span></span> | <span data-ttu-id="5a6fe-120">4.8</span><span class="sxs-lookup"><span data-stu-id="5a6fe-120">4.8</span></span>         |
| <span data-ttu-id="5a6fe-121">Type</span><span class="sxs-lookup"><span data-stu-id="5a6fe-121">Type</span></span>    | <span data-ttu-id="5a6fe-122">Reciblage</span><span class="sxs-lookup"><span data-stu-id="5a6fe-122">Retargeting</span></span> |
