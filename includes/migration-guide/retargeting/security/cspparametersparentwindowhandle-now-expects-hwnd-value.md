---
ms.openlocfilehash: 12ba3bd3c9e9e00b88cab0e568a1ce0f4f8bbb05
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606411"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a><span data-ttu-id="94f77-101">CspParameters.ParentWindowHandle attend maintenant une valeur HWND</span><span class="sxs-lookup"><span data-stu-id="94f77-101">CspParameters.ParentWindowHandle now expects HWND value</span></span>

#### <a name="details"></a><span data-ttu-id="94f77-102">Détails</span><span class="sxs-lookup"><span data-stu-id="94f77-102">Details</span></span>

<span data-ttu-id="94f77-103">La valeur <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle>, introduite dans .NET Framework 2.0, permet à une application d’inscrire une valeur de handle de fenêtre parente, pour que toute interface utilisateur nécessaire pour accéder à la clé (par exemple, une invite de code confidentiel ou une boîte de dialogue de consentement) s’ouvre sous la forme d’un enfant modal de la fenêtre spécifiée. À partir des applications qui ciblent .NET Framework 4.7, une application Windows Forms peut définir la propriété <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> avec du code semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="94f77-103">The <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> value, introduced in .NET Framework 2.0, allows an application to register a parent window handle value such that any UI required to access the key (such as a PIN prompt or consent dialog) opens as a modal child to the specified window.Starting with apps that target the .NET Framework 4.7, a Windows Forms application can set the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> property with code like the following:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="94f77-104">Dans les versions précédentes du .NET Framework, la valeur devait être un <xref:System.IntPtr?displayProperty=fullName> représentant un emplacement en mémoire où se trouvait la valeur [HWND](/windows/desktop/WinProg/windows-data-types#HWND).</span><span class="sxs-lookup"><span data-stu-id="94f77-104">In previous versions of the .NET Framework, the value was expected to be an <xref:System.IntPtr?displayProperty=fullName> representing a location in memory where the [HWND](/windows/desktop/WinProg/windows-data-types#HWND) value resided.</span></span> <span data-ttu-id="94f77-105">La définition de la propriété sur form.Handle sur Windows 7 et les versions antérieures n’avait aucun effet, mais sur Windows 8 et les versions ultérieures, cela entraîne un &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> : Le paramètre est incorrect.&quot;</span><span class="sxs-lookup"><span data-stu-id="94f77-105">Setting the property to form.Handle on Windows 7 and earlier versions had no effect, but on Windows 8 and later versions, it results in a &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>: The parameter is incorrect.&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="94f77-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="94f77-106">Suggestion</span></span>

<span data-ttu-id="94f77-107">Les applications ciblant .NET Framework 4.7 ou ultérieur qui souhaitent inscrire une relation de fenêtre parente sont encouragées à utiliser la forme simplifiée :</span><span class="sxs-lookup"><span data-stu-id="94f77-107">Applications targeting .NET Framework 4.7 or higher wishing to register a parent window relationship are encouraged to use the simplified form:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="94f77-108">Les utilisateurs qui avaient identifié que la bonne valeur à passer était l’adresse d’un emplacement de la mémoire qui détenait la valeur `form.Handle` peuvent refuser ce changement de comportement en définissant le commutateur AppContext `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` sur `true` :</span><span class="sxs-lookup"><span data-stu-id="94f77-108">Users who had identified that the correct value to pass was the address of a memory location which held the value `form.Handle` can opt out of the behavior change by setting the AppContext switch `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` to `true`:</span></span>

- <span data-ttu-id="94f77-109">En définissant des commutateurs de compatibilité programmatiquement sur AppContext, comme expliqué [ici](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span><span class="sxs-lookup"><span data-stu-id="94f77-109">By programmatically setting compat switches on the AppContext, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="94f77-110">En ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="94f77-110">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<runtime>
 <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
</runtime>
```

<span data-ttu-id="94f77-111">À l’inverse, les utilisateurs qui souhaitent adopter ce nouveau comportement sur le runtime .NET Framework 4.7 quand l’application se charge sur des versions antérieures du .NET Framework peuvent définir le commutateur AppContext sur `false`.</span><span class="sxs-lookup"><span data-stu-id="94f77-111">Conversely, users who wish to opt in to the new behavior on the .NET Framework 4.7 runtime when the application loads under older .NET Framework versions can set the AppContext switch to `false`.</span></span>

| <span data-ttu-id="94f77-112">Name</span><span class="sxs-lookup"><span data-stu-id="94f77-112">Name</span></span>    | <span data-ttu-id="94f77-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="94f77-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="94f77-114">Étendue</span><span class="sxs-lookup"><span data-stu-id="94f77-114">Scope</span></span>   | <span data-ttu-id="94f77-115">Secondaire</span><span class="sxs-lookup"><span data-stu-id="94f77-115">Minor</span></span>       |
| <span data-ttu-id="94f77-116">Version</span><span class="sxs-lookup"><span data-stu-id="94f77-116">Version</span></span> | <span data-ttu-id="94f77-117">4,7</span><span class="sxs-lookup"><span data-stu-id="94f77-117">4.7</span></span>         |
| <span data-ttu-id="94f77-118">Type</span><span class="sxs-lookup"><span data-stu-id="94f77-118">Type</span></span>    | <span data-ttu-id="94f77-119">Reciblage</span><span class="sxs-lookup"><span data-stu-id="94f77-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="94f77-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="94f77-120">Affected APIs</span></span>

- <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType>
