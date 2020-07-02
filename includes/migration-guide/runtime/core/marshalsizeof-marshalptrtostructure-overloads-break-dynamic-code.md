---
ms.openlocfilehash: c462c7b4ec8423ce8fd331d3cd31154283cf1f1d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619986"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="c07ae-101">Les surcharges Marshal.SizeOf et Marshal.PtrToStructure provoquent l’arrêt du code dynamique</span><span class="sxs-lookup"><span data-stu-id="c07ae-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

#### <a name="details"></a><span data-ttu-id="c07ae-102">Détails</span><span class="sxs-lookup"><span data-stu-id="c07ae-102">Details</span></span>

<span data-ttu-id="c07ae-103">À compter de .NET Framework 4.5.1, la liaison dynamique aux méthodes <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> ou <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (via Windows PowerShell, IronPython ou le mot clé dynamic du langage C#, par exemple) peut entraîner des exceptions <code>MethodInvocationExceptions</code>, car de nouvelles surcharges de ces méthodes ont été ajoutées et peuvent être ambiguës pour les moteurs de script.</span><span class="sxs-lookup"><span data-stu-id="c07ae-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c07ae-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="c07ae-104">Suggestion</span></span>

<span data-ttu-id="c07ae-105">Mettez à jour les scripts pour indiquer clairement quelle surcharge doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="c07ae-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="c07ae-106">Pour cela, castez explicitement les paramètres de type de la méthode en tant que <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="c07ae-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="c07ae-107">Cliquez sur [ce lien](https://support.microsoft.com/kb/2909958/) pour plus de détails et d’exemples sur la manière de contourner ce problème.</span><span class="sxs-lookup"><span data-stu-id="c07ae-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>

| <span data-ttu-id="c07ae-108">Nom</span><span class="sxs-lookup"><span data-stu-id="c07ae-108">Name</span></span>    | <span data-ttu-id="c07ae-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="c07ae-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c07ae-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="c07ae-110">Scope</span></span>   |<span data-ttu-id="c07ae-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="c07ae-111">Minor</span></span>|
|<span data-ttu-id="c07ae-112">Version</span><span class="sxs-lookup"><span data-stu-id="c07ae-112">Version</span></span>|<span data-ttu-id="c07ae-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="c07ae-113">4.5.1</span></span>|
|<span data-ttu-id="c07ae-114">Type</span><span class="sxs-lookup"><span data-stu-id="c07ae-114">Type</span></span>|<span data-ttu-id="c07ae-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="c07ae-115">Runtime</span></span>|
