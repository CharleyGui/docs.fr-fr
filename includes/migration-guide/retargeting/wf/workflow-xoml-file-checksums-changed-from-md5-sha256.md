---
ms.openlocfilehash: 2aa424ff5e3308b730c22cb865993d4100f193cc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616248"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a><span data-ttu-id="ad957-101">Sommes de contrôle du fichier XOML de workflow passées de MD5 à SHA256</span><span class="sxs-lookup"><span data-stu-id="ad957-101">Workflow XOML file checksums changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="ad957-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ad957-102">Details</span></span>

<span data-ttu-id="ad957-103">Pour prendre en charge le débogage des workflows XOML avec Visual Studio, lorsque des projets de workflow contenant des fichiers XOML sont générés, une somme de contrôle du contenu du fichier XOML est incluse dans le code généré comme une valeur <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ad957-103">To support debugging XOML-based workflows with Visual Studio, when workflow projects containing XOML files build, a checksum of the contents of the XOML file is included in the code generated as a <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="ad957-104">Dans .NET Framework 4.7.2 et versions antérieures, le hachage de somme de contrôle utilisait l’algorithme MD5, ce qui entraînait des problèmes sur les systèmes compatibles FIPS.</span><span class="sxs-lookup"><span data-stu-id="ad957-104">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="ad957-105">À compter de .NET Framework 4.8, l’algorithme utilisé est SHA256.</span><span class="sxs-lookup"><span data-stu-id="ad957-105">Starting with the .NET Framework 4.8, the algorithm used is SHA256.</span></span> <span data-ttu-id="ad957-106">Pour des raisons de compatibilité avec le WorkflowMarkupSourceAttribute.MD5Digest, seuls les 16 premiers octets de la somme de contrôle générée sont utilisés. Cela peut entraîner des problèmes pendant le débogage.</span><span class="sxs-lookup"><span data-stu-id="ad957-106">To be compatibile with the WorkflowMarkupSourceAttribute.MD5Digest, only the first 16 bytes of the generated checksum are used.This may cause problems during debugging.</span></span> <span data-ttu-id="ad957-107">Vous aurez peut-être à regénérer votre projet.</span><span class="sxs-lookup"><span data-stu-id="ad957-107">You may need to re-build your project.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ad957-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ad957-108">Suggestion</span></span>

<span data-ttu-id="ad957-109">Si la regénération de votre projet ne résout pas le problème, essayez de définir le commutateur `AppContext`&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; sur true. Dans le code, cela donne :</span><span class="sxs-lookup"><span data-stu-id="ad957-109">If re-building your project does not solve the problem, try setting the `AppContext` switch &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; to true.In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="ad957-110">Dans un fichier de configuration (qui doit être MSBuild.exe.config pour le MSBuild.exe que vous utilisez), cela donne :</span><span class="sxs-lookup"><span data-stu-id="ad957-110">Or in a configuration file (this needs to be in MSBuild.exe.config for the MSBuild.exe that you are using):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="ad957-111">Nom</span><span class="sxs-lookup"><span data-stu-id="ad957-111">Name</span></span>    | <span data-ttu-id="ad957-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="ad957-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ad957-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="ad957-113">Scope</span></span>   | <span data-ttu-id="ad957-114">Secondaire</span><span class="sxs-lookup"><span data-stu-id="ad957-114">Minor</span></span>       |
| <span data-ttu-id="ad957-115">Version</span><span class="sxs-lookup"><span data-stu-id="ad957-115">Version</span></span> | <span data-ttu-id="ad957-116">4.8</span><span class="sxs-lookup"><span data-stu-id="ad957-116">4.8</span></span>         |
| <span data-ttu-id="ad957-117">Type</span><span class="sxs-lookup"><span data-stu-id="ad957-117">Type</span></span>    | <span data-ttu-id="ad957-118">Reciblage</span><span class="sxs-lookup"><span data-stu-id="ad957-118">Retargeting</span></span> |
