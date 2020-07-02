---
ms.openlocfilehash: 9c9c4ec55143ef991e9b69a389e0f3368263bb4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614554"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a><span data-ttu-id="25212-101">NullReferenceException dans le code de gestion des exceptions à partir de ImageSourceConverter.ConvertFrom</span><span class="sxs-lookup"><span data-stu-id="25212-101">NullReferenceException in exception handling code from ImageSourceConverter.ConvertFrom</span></span>

#### <a name="details"></a><span data-ttu-id="25212-102">Détails</span><span class="sxs-lookup"><span data-stu-id="25212-102">Details</span></span>

<span data-ttu-id="25212-103">Une erreur dans le code de gestion des exceptions <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> a provoqué la levée d’une exception <xref:System.NullReferenceException?displayProperty=fullName> incorrecte au lieu de l’exception prévue (<xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> ou <xref:System.IO.FileNotFoundException?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="25212-103">An error in the exception handling code for <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> caused an incorrect <xref:System.NullReferenceException?displayProperty=fullName> to be thrown instead of the intended exception ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> or <xref:System.IO.FileNotFoundException?displayProperty=fullName>).</span></span> <span data-ttu-id="25212-104">Ce changement corrige cette erreur pour que la méthode lève la bonne exception.</span><span class="sxs-lookup"><span data-stu-id="25212-104">This change corrects that error so that the method now throws the right exception.</span></span> <p/><span data-ttu-id="25212-105">Par défaut, toutes les applications ciblant .NET Framework 4.6.2 et antérieur continuent à lever <xref:System.NullReferenceException?displayProperty=fullName> pour assurer la compatibilité.</span><span class="sxs-lookup"><span data-stu-id="25212-105">By default all applications targeting .NET Framework 4.6.2 and earlier continue to throw <xref:System.NullReferenceException?displayProperty=fullName> for compatibility.</span></span> <span data-ttu-id="25212-106">Les développeurs ciblant .NET Framework 4.7 et ultérieur devraient voir les bonnes exceptions.</span><span class="sxs-lookup"><span data-stu-id="25212-106">Developers targeting .NET Framework 4.7 and above should see the right exceptions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25212-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="25212-107">Suggestion</span></span>

<span data-ttu-id="25212-108">Les développeurs qui ciblent le .NET Framework 4.7 ou ultérieur et qui préfèrent obtenir l’exception <xref:System.NullReferenceException?displayProperty=fullName> peuvent ajouter/fusionner les éléments suivants dans le fichier App.config de leur application :</span><span class="sxs-lookup"><span data-stu-id="25212-108">Developers who wish to revert to getting <xref:System.NullReferenceException?displayProperty=fullName> when targeting .NET Framework 4.7 or later can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="25212-109">Nom</span><span class="sxs-lookup"><span data-stu-id="25212-109">Name</span></span>    | <span data-ttu-id="25212-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="25212-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="25212-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="25212-111">Scope</span></span>   | <span data-ttu-id="25212-112">Edge</span><span class="sxs-lookup"><span data-stu-id="25212-112">Edge</span></span>        |
| <span data-ttu-id="25212-113">Version</span><span class="sxs-lookup"><span data-stu-id="25212-113">Version</span></span> | <span data-ttu-id="25212-114">4,7</span><span class="sxs-lookup"><span data-stu-id="25212-114">4.7</span></span>         |
| <span data-ttu-id="25212-115">Type</span><span class="sxs-lookup"><span data-stu-id="25212-115">Type</span></span>    | <span data-ttu-id="25212-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="25212-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="25212-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="25212-117">Affected APIs</span></span>

- <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType>
