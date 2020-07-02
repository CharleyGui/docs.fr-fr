---
ms.openlocfilehash: 7c2e80669d9ef27f87cde9442d8eeab0ee31a524
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614622"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a><span data-ttu-id="f8e91-101">La sélection de texte WPF TextBox/PasswordBox ne suit pas les couleurs système</span><span class="sxs-lookup"><span data-stu-id="f8e91-101">WPF TextBox/PasswordBox Text Selection Does Not Follow System Colors</span></span>

#### <a name="details"></a><span data-ttu-id="f8e91-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f8e91-102">Details</span></span>

<span data-ttu-id="f8e91-103">Dans .NET Framework 4.7.1 et versions antérieures, WPF `System.Windows.Controls.TextBox` et `System.Windows.Controls.PasswordBox` pouvaient afficher une sélection de texte uniquement dans la couche Ornement.</span><span class="sxs-lookup"><span data-stu-id="f8e91-103">In .NET Framework 4.7.1 and earlier versions, WPF `System.Windows.Controls.TextBox` and `System.Windows.Controls.PasswordBox` could only render a text selection in the Adorner layer.</span></span> <span data-ttu-id="f8e91-104">Dans certains thèmes système, cela occultait le texte, au point de le rendre difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="f8e91-104">In some system themes this would occlude text, making it hard to read.</span></span>  <span data-ttu-id="f8e91-105">Dans .NET Framework 4.7.2 et ultérieur, les développeurs ont la possibilité d’activer un schéma de rendu de sélection non basée sur la couche Ornement qui atténue ce problème.</span><span class="sxs-lookup"><span data-stu-id="f8e91-105">In .NET Framework 4.7.2 and later, developers have an option of enabling a non-Adorner-based selection rendering scheme that alleviates this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f8e91-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f8e91-106">Suggestion</span></span>

<span data-ttu-id="f8e91-107">Un développeur qui souhaite utiliser cette modification doit définir l’indicateur AppContext suivant de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="f8e91-107">A developer who wants to utilize this change must set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="f8e91-108">Vous ne pouvez utiliser cette fonctionnalité que si vous avez installé .NET Framework version 4.7.2 ou ultérieure. Pour activer la sélection non basée sur un ornement, utilisez l’indicateur AppContext suivant.</span><span class="sxs-lookup"><span data-stu-id="f8e91-108">To utilize this feature, the installed .NET Framework version must be 4.7.2 or greater.To enabled the non-adorner-based selection, use the following AppContext flag.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="f8e91-109">Nom</span><span class="sxs-lookup"><span data-stu-id="f8e91-109">Name</span></span>    | <span data-ttu-id="f8e91-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="f8e91-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f8e91-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="f8e91-111">Scope</span></span>   | <span data-ttu-id="f8e91-112">Edge</span><span class="sxs-lookup"><span data-stu-id="f8e91-112">Edge</span></span>        |
| <span data-ttu-id="f8e91-113">Version</span><span class="sxs-lookup"><span data-stu-id="f8e91-113">Version</span></span> | <span data-ttu-id="f8e91-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="f8e91-114">4.7.2</span></span>       |
| <span data-ttu-id="f8e91-115">Type</span><span class="sxs-lookup"><span data-stu-id="f8e91-115">Type</span></span>    | <span data-ttu-id="f8e91-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="f8e91-116">Retargeting</span></span> |
