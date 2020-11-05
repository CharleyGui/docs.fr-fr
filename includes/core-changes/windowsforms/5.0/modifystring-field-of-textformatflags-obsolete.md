---
ms.openlocfilehash: 56127309c5f5993ffc2e2faedd1f481e8131e094
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400632"
---
### <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="6e163-101">TextFormatFlags. ModifyString est obsolète</span><span class="sxs-lookup"><span data-stu-id="6e163-101">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="6e163-102">Le <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> champ est obsolète, comme un avertissement, et peut être supprimé dans une prochaine version .net.</span><span class="sxs-lookup"><span data-stu-id="6e163-102">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6e163-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="6e163-103">Change description</span></span>

<span data-ttu-id="6e163-104">Dans les versions précédentes de .NET, le <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> champ d’énumération n’est pas marqué comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="6e163-104">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="6e163-105">Dans .NET 5,0 et versions ultérieures, il est marqué comme étant obsolète en tant qu’avertissement.</span><span class="sxs-lookup"><span data-stu-id="6e163-105">In .NET 5.0 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="6e163-106">Ce champ peut être supprimé dans une future version .NET.</span><span class="sxs-lookup"><span data-stu-id="6e163-106">This field may be removed in a future .NET version.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6e163-107">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="6e163-107">Reason for change</span></span>

<span data-ttu-id="6e163-108">Le passage d’une chaîne à <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> avec <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> modifie la chaîne dans certaines situations.</span><span class="sxs-lookup"><span data-stu-id="6e163-108">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="6e163-109">Ce comportement interrompt la promesse de la chaîne d’immuabilité et peut entraîner une altération irrécupérable de l’état du Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="6e163-109">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6e163-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6e163-110">Version introduced</span></span>

<span data-ttu-id="6e163-111">.NET 5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="6e163-111">.NET 5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6e163-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6e163-112">Recommended action</span></span>

<span data-ttu-id="6e163-113">Mettez à jour le code qui s’appuie sur <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6e163-113">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="6e163-114">Category</span><span class="sxs-lookup"><span data-stu-id="6e163-114">Category</span></span>

<span data-ttu-id="6e163-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6e163-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6e163-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="6e163-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

-->
