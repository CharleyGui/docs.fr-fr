---
ms.openlocfilehash: 811b1a91169eeebfa056d9ecdb07d342d3b32d85
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615718"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a><span data-ttu-id="6658b-101">Icon.ToBitmap convertit correctement les icônes dotées de cadres PNG en objets Bitmap</span><span class="sxs-lookup"><span data-stu-id="6658b-101">Icon.ToBitmap successfully converts icons with PNG frames into Bitmap objects</span></span>

#### <a name="details"></a><span data-ttu-id="6658b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="6658b-102">Details</span></span>

<span data-ttu-id="6658b-103">À compter des applications qui ciblent .NET Framework 4.6, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> convertit correctement en objets Bitmap les icônes comportant des cadres PNG.</span><span class="sxs-lookup"><span data-stu-id="6658b-103">Starting with the apps that target the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into Bitmap objects.</span></span><p/><span data-ttu-id="6658b-104">Dans les applications qui ciblent .NET Framework 4.5.2 et versions antérieures, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> lève une exception <xref:System.ArgumentOutOfRangeException> si l’objet Icon comporte des cadres PNG.</span><span class="sxs-lookup"><span data-stu-id="6658b-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the  <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the Icon object has PNG frames.</span></span><p/><span data-ttu-id="6658b-105">Ce changement affecte les applications qui sont recompilées pour cibler .NET Framework 4.6 et qui implémentent un traitement spécial pour l’exception <xref:System.ArgumentOutOfRangeException> qui est levée quand un objet Icon comporte des cadres PNG.</span><span class="sxs-lookup"><span data-stu-id="6658b-105">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an Icon object has PNG frames.</span></span> <span data-ttu-id="6658b-106">Dans le cadre d’une exécution sous le .NET Framework 4.6, la conversion aboutit, il n’est plus levé d’exception <xref:System.ArgumentOutOfRangeException> et, de ce fait, le gestionnaire d’exceptions n’est plus appelé.</span><span class="sxs-lookup"><span data-stu-id="6658b-106">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6658b-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="6658b-107">Suggestion</span></span>

<span data-ttu-id="6658b-108">Si ce comportement est indésirable, vous pouvez conserver le comportement précédent en ajoutant l’élément suivant à la section `<runtime>` de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="6658b-108">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the `<runtime>` section of your app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>

<span data-ttu-id="6658b-109">Si le fichier app.config contient déjà l’élément `AppContextSwitchOverrides`, la nouvelle valeur doit être fusionnée avec l’attribut value comme ceci :</span><span class="sxs-lookup"><span data-stu-id="6658b-109">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the value attribute like this:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="6658b-110">Nom</span><span class="sxs-lookup"><span data-stu-id="6658b-110">Name</span></span>    | <span data-ttu-id="6658b-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="6658b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6658b-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="6658b-112">Scope</span></span>   | <span data-ttu-id="6658b-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="6658b-113">Minor</span></span>       |
| <span data-ttu-id="6658b-114">Version</span><span class="sxs-lookup"><span data-stu-id="6658b-114">Version</span></span> | <span data-ttu-id="6658b-115">4.6</span><span class="sxs-lookup"><span data-stu-id="6658b-115">4.6</span></span>         |
| <span data-ttu-id="6658b-116">Type</span><span class="sxs-lookup"><span data-stu-id="6658b-116">Type</span></span>    | <span data-ttu-id="6658b-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="6658b-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6658b-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="6658b-118">Affected APIs</span></span>

- <xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType>
