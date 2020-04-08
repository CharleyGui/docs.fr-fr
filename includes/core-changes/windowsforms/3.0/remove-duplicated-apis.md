---
ms.openlocfilehash: 0be59258df10aa13920551f011d68bc8efe20b93
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888114"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="cf3ca-101">API dupliquée supprimée des formulaires Windows</span><span class="sxs-lookup"><span data-stu-id="cf3ca-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="cf3ca-102">Un certain nombre d’API <xref:System.Windows.Forms?displayProperty=fullName> accidentellement dupliqué dans l’espace de nom à partir de .NET Core 3.0 Aperçu 4 ont été supprimés dans .NET Core 3.0 RC1.</span><span class="sxs-lookup"><span data-stu-id="cf3ca-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cf3ca-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="cf3ca-103">Change description</span></span>

<span data-ttu-id="cf3ca-104">.NET Core 3.0 Aperçu 4 par inadvertance <xref:System.Windows.Forms?displayProperty=fullName> dupliqué un certain <xref:System.ComponentModel.Design?displayProperty=fullName> nombre de types dans l’espace nom qui existait déjà dans l’espace nom.</span><span class="sxs-lookup"><span data-stu-id="cf3ca-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="cf3ca-105">À partir de .NET Core 3.0 RC1, ces types dupliqués ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="cf3ca-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="cf3ca-106">Le tableau suivant affiche les listes du type d’origine et de son type dupliqué :</span><span class="sxs-lookup"><span data-stu-id="cf3ca-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="cf3ca-107">Type original</span><span class="sxs-lookup"><span data-stu-id="cf3ca-107">Original type</span></span>|<span data-ttu-id="cf3ca-108">Type dupliqué</span><span class="sxs-lookup"><span data-stu-id="cf3ca-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="cf3ca-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="cf3ca-109">Version introduced</span></span>

<span data-ttu-id="cf3ca-110">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="cf3ca-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cf3ca-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="cf3ca-111">Recommended action</span></span>

<span data-ttu-id="cf3ca-112">Mettre à jour le code pour référencer le type d’origine, tel qu’indiqué dans la colonne de **type Original** de la table.</span><span class="sxs-lookup"><span data-stu-id="cf3ca-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="cf3ca-113">Category</span><span class="sxs-lookup"><span data-stu-id="cf3ca-113">Category</span></span>

<span data-ttu-id="cf3ca-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf3ca-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cf3ca-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="cf3ca-115">Affected APIs</span></span>

- <span data-ttu-id="cf3ca-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cf3ca-116">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->
