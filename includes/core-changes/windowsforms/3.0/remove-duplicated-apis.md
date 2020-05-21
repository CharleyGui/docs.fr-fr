---
ms.openlocfilehash: 3dfacadb5127319d4ce27f367803637cfb1ed00f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721427"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="c4eda-101">API dupliquées supprimées de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c4eda-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="c4eda-102">Un certain nombre d’API dupliquées accidentellement dans l' <xref:System.Windows.Forms?displayProperty=fullName> espace de noms à compter de .net core 3,0 Preview 4 ont été supprimées dans .net core 3,0 RC1.</span><span class="sxs-lookup"><span data-stu-id="c4eda-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c4eda-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="c4eda-103">Change description</span></span>

<span data-ttu-id="c4eda-104">.NET Core 3,0 Preview 4 a, par inadvertance, dupliqué un certain nombre de types dans l' <xref:System.Windows.Forms?displayProperty=fullName> espace de noms qui existaient déjà dans l' <xref:System.ComponentModel.Design?displayProperty=fullName> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c4eda-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="c4eda-105">À compter de .NET Core 3,0 RC1, ces types dupliqués ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="c4eda-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="c4eda-106">Le tableau suivant répertorie le type d’origine et son type dupliqué :</span><span class="sxs-lookup"><span data-stu-id="c4eda-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="c4eda-107">Type d’origine</span><span class="sxs-lookup"><span data-stu-id="c4eda-107">Original type</span></span>|<span data-ttu-id="c4eda-108">Type dupliqué</span><span class="sxs-lookup"><span data-stu-id="c4eda-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="c4eda-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c4eda-109">Version introduced</span></span>

<span data-ttu-id="c4eda-110">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="c4eda-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c4eda-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c4eda-111">Recommended action</span></span>

<span data-ttu-id="c4eda-112">Mettez à jour le code pour référencer le type d’origine, comme indiqué dans la colonne **type d’origine** de la table.</span><span class="sxs-lookup"><span data-stu-id="c4eda-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="c4eda-113">Category</span><span class="sxs-lookup"><span data-stu-id="c4eda-113">Category</span></span>

<span data-ttu-id="c4eda-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c4eda-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c4eda-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="c4eda-115">Affected APIs</span></span>

- <span data-ttu-id="c4eda-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c4eda-116">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis.

-->
