---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937007"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="37b4b-101">API dupliquée supprimée des formulaires Windows</span><span class="sxs-lookup"><span data-stu-id="37b4b-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="37b4b-102">Un certain nombre d’API <xref:System.Windows.Forms?displayProperty=fullName> accidentellement dupliqué dans l’espace de nom à partir de .NET Core 3.0 Aperçu 4 ont été supprimés dans .NET Core 3.0 RC1.</span><span class="sxs-lookup"><span data-stu-id="37b4b-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="37b4b-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="37b4b-103">Change description</span></span>

<span data-ttu-id="37b4b-104">.NET Core 3.0 Aperçu 4 par inadvertance <xref:System.Windows.Forms?displayProperty=fullName> dupliqué un certain <xref:System.ComponentModel.Design?displayProperty=fullName> nombre de types dans l’espace nom qui existait déjà dans l’espace nom.</span><span class="sxs-lookup"><span data-stu-id="37b4b-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="37b4b-105">À partir de .NET Core 3.0 RC1, ces types dupliqués ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="37b4b-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="37b4b-106">Le tableau suivant affiche les listes du type d’origine et de son type dupliqué :</span><span class="sxs-lookup"><span data-stu-id="37b4b-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="37b4b-107">Type original</span><span class="sxs-lookup"><span data-stu-id="37b4b-107">Original type</span></span>|<span data-ttu-id="37b4b-108">Type dupliqué</span><span class="sxs-lookup"><span data-stu-id="37b4b-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="37b4b-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="37b4b-109">Version introduced</span></span>

<span data-ttu-id="37b4b-110">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="37b4b-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="37b4b-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="37b4b-111">Recommended action</span></span>

<span data-ttu-id="37b4b-112">Mettre à jour le code pour référencer le type d’origine, tel qu’indiqué dans la colonne de **type Original** de la table.</span><span class="sxs-lookup"><span data-stu-id="37b4b-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="37b4b-113">Category</span><span class="sxs-lookup"><span data-stu-id="37b4b-113">Category</span></span>

<span data-ttu-id="37b4b-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37b4b-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="37b4b-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="37b4b-115">Affected APIs</span></span>

- <span data-ttu-id="37b4b-116">Non détectable par l’analyse de l’API.</span><span class="sxs-lookup"><span data-stu-id="37b4b-116">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->
