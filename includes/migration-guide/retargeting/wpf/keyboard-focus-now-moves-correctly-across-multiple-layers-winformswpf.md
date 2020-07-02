---
ms.openlocfilehash: a82b720fd4e771481ea1142a88a095443afa0d5b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614603"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a><span data-ttu-id="75e83-101">Le focus clavier se déplace désormais correctement entre plusieurs couches d’hébergement WinForms/WPF</span><span class="sxs-lookup"><span data-stu-id="75e83-101">Keyboard focus now moves correctly across multiple layers of WinForms/WPF hosting</span></span>

#### <a name="details"></a><span data-ttu-id="75e83-102">Détails</span><span class="sxs-lookup"><span data-stu-id="75e83-102">Details</span></span>

<span data-ttu-id="75e83-103">Imaginez une application WPF qui héberge un contrôle WinForms hébergeant à son tour des contrôles WPF.</span><span class="sxs-lookup"><span data-stu-id="75e83-103">Consider a WPF application hosting a WinForms control which in turn hosts WPF controls.</span></span> <span data-ttu-id="75e83-104">Les utilisateurs peuvent être dans l’impossibilité de quitter la couche WinForms au moyen de la touche Tab si le premier ou dernier contrôle dans cette couche est le contrôle WPF `System.Windows.Forms.Integration.ElementHost`.</span><span class="sxs-lookup"><span data-stu-id="75e83-104">Users may not be able to tab out of the WinForms layer if the first or last control in that layer is the WPF `System.Windows.Forms.Integration.ElementHost`.</span></span> <span data-ttu-id="75e83-105">Ce changement résout ce problème, et les utilisateurs peuvent désormais quitter la couche WinForms au moyen de la touche Tab. Les applications automatisées pour lesquelles il est indispensable que le focus ne quitte jamais la couche WinForms pourraient ne plus fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="75e83-105">This change fixes this issue, and users are now able to tab out of the WinForms layer.Automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="75e83-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="75e83-106">Suggestion</span></span>

<span data-ttu-id="75e83-107">Un développeur qui souhaite utiliser ce changement tout en ciblant une version du .NET Framework antérieure à la version 4.7.2 peut définir l’ensemble suivant d’indicateurs AppContext sur false pour activer la modification.</span><span class="sxs-lookup"><span data-stu-id="75e83-107">A developer who wants to utilize this change while targeting a framework version below .NET 4.7.2 can set the following set of AppContext flags to false for the change to be enabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="75e83-108">Les applications WPF doivent accepter toutes les améliorations d’accessibilité antérieures pour obtenir les dernières améliorations.</span><span class="sxs-lookup"><span data-stu-id="75e83-108">WPF applications must opt in to all early accessibility improvements to get the later improvements.</span></span> <span data-ttu-id="75e83-109">En d’autres termes, les deux commutateurs `Switch.UseLegacyAccessibilityFeatures` et `Switch.UseLegacyAccessibilityFeatures.2` doivent être définis. Un développeur qui a besoin des fonctionnalités antérieures tout en ciblant .NET 4.7.2 ou version ultérieure peut définir l’indicateur AppContext suivant sur la valeur true pour activer la modification.</span><span class="sxs-lookup"><span data-stu-id="75e83-109">In other words, both the `Switch.UseLegacyAccessibilityFeatures` and the `Switch.UseLegacyAccessibilityFeatures.2` switches must be setA developer who requires the previous functionality while targeting .NET 4.7.2 or greater can set the following AppContext flag to true for the change to be disabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="75e83-110">Nom</span><span class="sxs-lookup"><span data-stu-id="75e83-110">Name</span></span>    | <span data-ttu-id="75e83-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="75e83-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="75e83-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="75e83-112">Scope</span></span>   | <span data-ttu-id="75e83-113">Edge</span><span class="sxs-lookup"><span data-stu-id="75e83-113">Edge</span></span>        |
| <span data-ttu-id="75e83-114">Version</span><span class="sxs-lookup"><span data-stu-id="75e83-114">Version</span></span> | <span data-ttu-id="75e83-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="75e83-115">4.7.2</span></span>       |
| <span data-ttu-id="75e83-116">Type</span><span class="sxs-lookup"><span data-stu-id="75e83-116">Type</span></span>    | <span data-ttu-id="75e83-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="75e83-117">Retargeting</span></span> |
