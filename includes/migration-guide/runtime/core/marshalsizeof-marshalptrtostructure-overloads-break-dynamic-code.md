---
ms.openlocfilehash: 086dac69d085d070511fcfd5820bd2644ee4598e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497349"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="ab83d-101">Les surcharges Marshal.SizeOf et Marshal.PtrToStructure provoquent l’arrêt du code dynamique</span><span class="sxs-lookup"><span data-stu-id="ab83d-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

#### <a name="details"></a><span data-ttu-id="ab83d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ab83d-102">Details</span></span>

<span data-ttu-id="ab83d-103">À compter de .NET Framework 4.5.1, la liaison dynamique aux méthodes <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> ou <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (via Windows PowerShell, IronPython ou le mot clé dynamic du langage C#, par exemple) peut entraîner des exceptions <code>MethodInvocationExceptions</code>, car de nouvelles surcharges de ces méthodes ont été ajoutées et peuvent être ambiguës pour les moteurs de script.</span><span class="sxs-lookup"><span data-stu-id="ab83d-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ab83d-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ab83d-104">Suggestion</span></span>

<span data-ttu-id="ab83d-105">Mettez à jour les scripts pour indiquer clairement quelle surcharge doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="ab83d-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="ab83d-106">Pour cela, castez explicitement les paramètres de type de la méthode en tant que <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="ab83d-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="ab83d-107">Cliquez sur [ce lien](https://support.microsoft.com/kb/2909958/) pour plus de détails et d’exemples sur la manière de contourner ce problème.</span><span class="sxs-lookup"><span data-stu-id="ab83d-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>

| <span data-ttu-id="ab83d-108">Name</span><span class="sxs-lookup"><span data-stu-id="ab83d-108">Name</span></span>    | <span data-ttu-id="ab83d-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="ab83d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ab83d-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="ab83d-110">Scope</span></span>   |<span data-ttu-id="ab83d-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="ab83d-111">Minor</span></span>|
|<span data-ttu-id="ab83d-112">Version</span><span class="sxs-lookup"><span data-stu-id="ab83d-112">Version</span></span>|<span data-ttu-id="ab83d-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="ab83d-113">4.5.1</span></span>|
|<span data-ttu-id="ab83d-114">Type</span><span class="sxs-lookup"><span data-stu-id="ab83d-114">Type</span></span>|<span data-ttu-id="ab83d-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="ab83d-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ab83d-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="ab83d-116">Affected APIs</span></span>

<span data-ttu-id="ab83d-117">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="ab83d-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
